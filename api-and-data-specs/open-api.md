# Open API Gateway

For this stage of the project we have pretty minimal requirements for the API; however, we DO need to setup the foundation of the API layer, for us to have initial code and API service available to communicate between the isgood.ai webapp, and the isgood.ai platform \(DS data brain\).

Those involved in the server infrastructure, ci/cd and DevOps, will be integral in the overall API and communications layer - incl.  infra for WebApp, API and platform services and infrastructure.

Open does NOT mean insecure, it means that we intend it to be able to connect to a very open number of AUTHORISED apps and systems. 

## Base API Service

Default communication for WebApp and platform is JSON, so looking at options we can start looking at the following around easy to manage, deploy and contribute Open-API frameworks:

* [https://jsonapi.org/](https://jsonapi.org/)
* [https://swagger.io/specification/](https://swagger.io/specification/)
* ... other options to look at for base ... want open, not lock-in ???

{% hint style="danger" %}
NOTE: Complex access filters & permissions via API, will need to be handled and reflected via [WebApp](../base-functional-specs/roles-permissions-acl.md) interface for data/platform permissions, as well as hierarchy/group permissions.
{% endhint %}

## API Functionality for 2021 Q1 Release

1. WebApp sends first four fields of project profile info to the API.
2. Platform receives the JSON text and processes it.
3. Returns list of platform indicatorIDs to WebApp and is stored as recommended indicatorIDs against the project.

## Initial API between WebApp & DS Functions

Would have also multiple beneficiary groups, with multiples of demographics for each beneficiary group, with multiple indicators for the project \(default 5\).

### Sending Project info to DS Brain, via API Gateway

```text
{
    projectId: 1234567890,
    name: "test",
    description: "string",
    projectImpacts: ["string", "string", "string"],
    outcomesDesired: ["string", "string", "string"],
    beneficiaries: [
        {
           name: "string",
           change: "string",
           demographics: [
               {
                   type: "string",
                   operator: "string",
                   value: integer
               },
           ]
        },
    ],
    geolocation: [lat, lng],
    startDate: "timestamp",
    endDate: "timestamp"
}
```

.... and for now it is just:

```text
{
    projectId: 1234567890,
    name: "string",
    description: "string",
    projectImpacts: ["string", "string", "string"],
    outcomesDesired: ["string", "string", "string"],
}
```

### Response back from the DS Mapper function \(via Gateway\)

```text
{
    projectId: 1234567890,
    indicators: [
        {
            indicatorID: uidOfIndicatorxxx,
            alignedStrength: 0.937465873983,  //I am the vector of strength?
        },
        {
            indicatorID: uidOfIndicatorxxx,
            alignedStrength: 0.837465873983,  //I am the vector of strength?
        },
        {
            indicatorID: uidOfIndicatorxxx,
            alignedStrength: 0.737465873983,  //I am the vector of strength?
        }
    ]
}
```

#### Notes from DS Side

* Project ID \(object ID for DS side\) must also be sent to the back end with the text input as well as the number of recommendations
* API Call will give us Client ID, object Id, user input \(First 4 fields\), number of indicators to be returned
* Client ID will be the UID of Client sending us the input.
* Object ID will be the UID associated with the text input.
* User input will be the input .
* And the number of indicators to be returned.
* We will be returning the indicator UID and the strengthIng our table we will have Recommendation ID, ClientID, Object ID, text, Text\_Vector

**Clarifications:**

* Keep the option to be able to request more indicators to be returned - default is 5. 
* just return the asset-id \(ID\) fir the recommended indicators with strength. The detail is requested from the global-text as the record of the details, and is on cache in the app.
* Yes for the extra into to be saved in the DS DB

## API Infra as Code

Hsin and Tim have been working on [Terraform](https://www.hashicorp.com/products/terraform) for the management and deploy of the API Gateway on AWS.

## 20210303 - Meeting to Discuss

{% embed url="https://youtu.be/Zodq9h1vDjY" %}

### Support 202 Response for WebApp
{% hint style="info" %}
**DRAFT**
{% endhint %}

| route | behavior |
| -- | -- |
| `/echo` | HTTP integration w/ fake data |
| `/echo/foxtrot` | HTTP integration detail w/ fake data |
| `/lambda` | Lambda integration w/ fake data |
| `/lambda/mu` | Lambda integration detail w/ fake data |
| `/lambda/x` | **202 Response** w/ placeholders |

With the new `/lambda/x` route, we remove Cognito and switch to API keys for controlling access. One API key is generated with the Terraform deployment and is named *demo-api-key* when viewed in the AWS management console. It should be the same as manually generating keys and usage plans within the console. So the WebApp can be assigned any API key after deployment, by going to the console and using the UI (as described in [AWS doc](https://docs.aws.amazon.com/apigateway/latest/developerguide/api-gateway-api-usage-plans.html)).

We used a guide to configure the `202` response behavior which is more clear than I can write. See [Lambda destinations](https://aws.amazon.com/blogs/compute/introducing-aws-lambda-destinations/) to get the general idea of the request-response flow. To adapt this guide for our infra, the steps were converted into Terraform HCL.

| git | module |
| -- | -- |
| [tf/modules/rest](https://github.com/for-good/isgood-api/tree/main/tf/modules/rest) | REST configuration |
| [tf/modules/lambda](https://github.com/for-good/isgood-api/tree/main/tf/modules/lambda) | Lambda functions |

**tf/modules/rest/oas3.json**
The new route (`/lambda/x`) is added on line #10. It has a security scheme that we name DemoRegisteredKeys. The `uri` field is a parameter that is bound to the event-invoke Lambda's ARN.
```
  "paths": {
    "/lambda/x": {
      "post": {
        "security": [{"DemoRegisteredKeys": []}],
        "x-amazon-apigateway-integration": {
	  "uri": "${event_invoke_uri}",
          "httpMethod": "POST",
          "responses": {
            "default": {
              "statusCode": "202"
            }
          },
          "passthroughBehavior": "when_no_match",
          "type": "aws_proxy"
        }
      }
    },
```
The DemoRegisteredKeys security scheme replaces the ExampleRegisteredKeys and specifies X-API-KEY as the header for the API key value.
```
  "components": {
    "securitySchemes": {
        "DemoRegisteredKeys": {
          "type": "apiKey",
          "name": "x-api-key",
          "in": "header"
        }
    }
  }
```
**tf/modules/rest/rest-api-key.tf**
The *demo-api-key* is defined with the HCL inside the rest-api-key.tf file. These steps can be applied manually from the AWS management console. This HCL and the *demo-api-key* is for convenience, and to help in adhoc/automation when we want to test against a gateway after deployment. It will be removed when the automation can create its test key within the test framework.


**tf/modules/lambda/event-invoke-step.tf**
The backend-Lambda is encapsulated inside the *event-invoke-step* configuration. The Python file `event-invoke-step.py` is a placeholder. When the backend-Lambda is ready, this `aws_lambda_function.event_invoke_step_lambda` will be removed, and the ARN from the backend-Lambda will supercede. This means there will be some adjustment at the interface between the backend-Lambda and the invoke.

Also, notice the configuration for retries and destination. Until we make the Python logic idempotent, this disables the automatic retries. AND we will want to add the dead letter queue to track errors.  
```
resource "aws_lambda_function_event_invoke_config" "event_invoke_step_config" {
  function_name = aws_lambda_function.event_invoke_step_lambda.function_name
  # Do not retry when error occurs (until we have re-entrant handling)
  maximum_retry_attempts = 0
  # Final step after subprocess ends
  destination_config {
    # Move forward when function is successful
    # by sending invocation record to destination child Lambda
    on_success {
      destination = aws_lambda_function.event_invoke_final_lambda.arn
    }
  }
}
```
The destination config is how we chain a final step. When the `event-invoke-step` function is finished, the destination Lambda will then be called.

**tf/modules/lambda/functions/event-invoke.py**
The `FunctionName` (line #58) will need to be replaced by the backend-Lambda's ARN when it is ready.
```
def invoke_subprocess(data):
        # Make payload passed to subprocess
        subproc_payload = json.dumps({
            PROJECT_ID_STRING: data
        })

        # Invoking subprocess asynchronously by using InvocationType='Event'
        sdk = boto3.client('lambda')
        response = sdk.invoke(
                FunctionName='event-invoke-step',
                InvocationType='Event',
                Payload=subproc_payload
        )

        # returns 202 on success
        return response
```
The `Payload` data currently contains the *PROJECT_ID_STRING* field (line #52). After the backend-Lambda is ready, it may be necessary to adjust this payload. That way we can make sure we are passing the expected fields to the production backend-Lambda.

**tf/modules/lambda/functions/event-invoke-step.py**
This Python file is a placeholder for the backend-Lambda. It demonstrates how a Lambda function can be called asynchronously. Currently, it generates fake indicators data and returns response 200.

**tf/modules/lambda/functions/event-invoke-final.py**
This Python file is executed when the `event-invoke-step` function is done. Currently, it sends a request to Auth0 to obtain the JWT, and then makes a POST to the *echo* service that we host on Netlify. The *WEBAPP_HOST* and *WEBAPP_HOST* parameters will need to be changed when the webapp backend endpoint is ready. This interface which includes the request headers and payload will need to be adjusted too.
```
def send_post_to_known_webconsumer(req):
        # Get the webapp backend endpoint from environment variables
        web_host = os.environ['WEBAPP_HOST']
        web_path = os.environ['WEBAPP_PATH']

        logger.info("## starting to send post...")
        logger.info(req)

        # Make the POST request to the webapp backend
        conn = http.client.HTTPSConnection(web_host)
        conn.request("POST", web_path, req['payload'], req['headers'])
        res = conn.getresponse()
        data = res.read()

        return data.decode("utf-8")
```
For debugging, it's necessary to go to the Cloudwatch logs. Each Lambda function has its own set of logs. The logs can be delayed, but eventually appear. Looking for the log entries from the `event-invoke-final` function will confirm whether the asynchronous invocation triggered because the chain can fail at two steps prior to reaching the final funcion.


| infrastructure | role |
| -- | -- |
| Github | source control repo |
| Github actions | Continuous Integration |
| Terraform Cloud | Terraform remote state |
| Terraform Vault | temporary AWS credentials |
| AWS | API gateway |

How to deploy the API gateway for development:
1. `aws configure`
2. sign-up at app.terraform.io 
3. `git clone https://github.com/for-good/isgood-api.git`
4. `cd isgood-api && git checkout -b` *gh-issue-NNN*
5. `terraform init`
6. edit `tf/remote-backend.tf` with values from step #2
7. edit `env/dev.tfvars`
8. apply fix for *gh-issue-NNN*
9. `terraform validate`
10. `AWS_REGION=us-east-2 terraform apply -var-file=env/dev.tfvars`




**TODO and backlog items**
When you read the AWS documentation about `InvocationType=Event`, it mentions retries and potential lost events. To manage these edge cases, there is more to think about.
-[] Configure dead letter queue to track lost/retries and help determine when to redesign for scale (which may mean researching EventBridge, Step Functions)
-[] Somewhat related to retries, the Lambda functions would need to handle; reentrant, idempotent
-[] Limit the scope of the IAM roles in the Lambda functions and refactor out the wildcards (`resources = ["*"]`)
-[] Adjust interface after backend-Lambda is ready
-[] Adjust interface after webapp backend endpoint is ready
-[] Test the failure behavior in the invocation chain


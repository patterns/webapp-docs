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

{% api-method method="post" host="" path="/Initial/Things" %}
{% api-method-summary %}
Initial API between WebApp & DS Functions
{% endapi-method-summary %}

{% api-method-description %}
Would have also multiple beneficiary groups, with multiples of demographics for each beneficiary group, with multiple indicators for the project \(default 5\).
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=true %}
Sending Project info to DS Brain, via API Gateway
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Something like this as a response 
{% endapi-method-response-example-description %}

```
{
    name: "test",
    description: "dxftdkrxghijoih'ug;yflhkt",
    projectImpacts: ["ertvwerb eb", "evwevweveq", "efvweveqveqv"],
    outcomesDesired: ["fvwevrvwvt", "efvwevwqvq", "ervewvrvw"],
    beneficiaries: [
        {
           name: "ljhvkv",
           change: ",jh kgvj",
           demographics: [
               {
                   type: "age",
                   operator: ">",
                   value: "10"
               },
           ]
        },
    ],
    geolocation: ["ervweqv", "vevewveq"],
    startDate: "timestamp",
    endDate: "timestamp",
    indicators: [
        {
            indicatorId: "",
            indicator: "",
            strength: "",
        }
    ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## API Infra as Code

Hsin and Tim have been working on [Terraform](https://www.hashicorp.com/products/terraform) for the management and deploy of the API Gateway on AWS.

## 20210303 - Meeting to Discuss

{% embed url="https://youtu.be/Zodq9h1vDjY" %}




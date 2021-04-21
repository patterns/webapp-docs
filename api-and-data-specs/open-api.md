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
            indicatorID: primaryKeyOfIndicatorxxx,
            alignedStrength: 0.937465873983,  //I am the vector of strength?
        },
        {
            indicatorID: primaryKeyOfIndicatorxxx,
            alignedStrength: 0.837465873983,  //I am the vector of strength?
        },
        {
            indicatorID: primaryKeyOfIndicatorxxx,
            alignedStrength: 0.737465873983,  //I am the vector of strength?
        }
    ]
}
```

#### Notes from DS Side

* Project ID \(object ID for DS side\) must also be sent to the back end with the text input as well as the number of recommendations
* API Call will give us Client ID, object Id, user input \(First 4 fields\), number of indicators to be returned
* Client ID will be the ID of Client sending us the input.
* Object ID will be the ID associated with the text input.
* User input will be the input .
* And the number of indicators to be returned.
* We will be returning the indicator ID and the strengthIn our table we will have Recommendation ID, ClientID, Object ID, text, Text\_Vector

**Clarifications:**

* Keep the option to be able to request more indicators to be returned - default is 5. 
* just return the primary key \(ID\) fir the recommended indicators with strength. The detail is requested from the global-text as the record of the details, and is on cache in the app.
* Yes for the extra into to be saved in the DS DB

## API Infra as Code

Hsin and Tim have been working on [Terraform](https://www.hashicorp.com/products/terraform) for the management and deploy of the API Gateway on AWS.

## 20210303 - Meeting to Discuss

{% embed url="https://youtu.be/Zodq9h1vDjY" %}




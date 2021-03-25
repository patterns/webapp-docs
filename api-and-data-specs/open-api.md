# Open API Service

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

## API Functionality for Q1 Release

1. WebApp sends first four fields of project profile info to the API.
2. Platform receives the JSON text and processes it.
3. Returns list of platform indicatorIDs to WebApp and is stored as recommended indicatorIDs against the project.

## Kickoff Meeting Recording

{% embed url="https://youtu.be/Zodq9h1vDjY" %}




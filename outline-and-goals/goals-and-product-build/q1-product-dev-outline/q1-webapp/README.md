# Q1 WebApp



## A basic step through of the WebApp module to get working NOW:

1. enable user account rego
2. if no org, setup org \(workspace billing account "owner", like redcross australia\)
3. if no project, setup a project \(like a folder in google drive, that sits under the parent/org, can have secondary billing to be inherited\)
4. is has access to org and projects, user sees list of projects they have access to
5. when setting up/edit project, enter project profile info \(people, place, problem\)
6. once project info entered, AI returns recommendation of project indicators \(mapper/global\_text/w2vec\), top results displayed on project profile to user

## For recommendations to work:

* inputs are the project fields
* outputs are the recommended indicator IDs returned by mapper script vectors -&gt; full info from global\_text

## Relationship Fundamentals

* permissions and access is very similar to the way google drive works
* users - they can access what has been shared with them \(ACL user levels, and per user share\)
* organisation is the primary “account holder” \(workspace\)
* projects belong to an organisation
* projects have info about the people, problem, place
* ownership and access of assets, data, etc in the webapp by user \(or group TBA\)
* project partner/child relations, similar to folder structure in google drive \(and sharing similar too\)
* VERY hierarchical \(think of how intl aid orgs, military, etc type structures work\)

## Mock and User Flow

The mock and user flow has been collated via our [Miro Board](https://miro.com/app/board/o9J_kyYfLV0=/?moveToWidget=3074457354464890435&cot=10).

note: the mocks have not been done with the [recently chosen](https://www.loomio.org/s/as3HMDBN) Material-UI front-end UI framework, and styles, so while it may look a little different from our [starter](https://github.com/creativetimofficial/material-dashboard-react), the functionality and concepts remain.

## 


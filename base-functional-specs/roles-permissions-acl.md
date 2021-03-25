# Roles, Permissions, ACL

## Current Status

Technically, our approach appears to be a **hybrid of RBAC and ABAC policies**  \(thx @Ilias for defining this 🙏 \)

We are currently investigating the following libraries, which seem to solidly support our approach:

* [https://casbin.org/](https://casbin.org/)   \(Ilias leading investigation of this\)
* [https://www.osohq.com/](https://www.osohq.com/)    \(Matt leading investigation of this\)

## Relationship Fundamentals

* permissions and access is very similar to the way google drive works
* users - they can access what has been shared with them \(ACL user levels, and per user share\)
* _**User are the one global entity in the isgood.ai app, everything else in there are just assets, to which users do or do not have access, and have certain permissions or roles for.**_ 
* organisation is the top level hierarchical asset
* projects belong to an organisation
* projects have info about the project/initiative being run \(people, problem, place\). 
* ownership and access of assets, data, etc in the webapp by user
* user-groups and sharing groups \(eg. share with everyone in org\) will come later. 
* project partner/child relations, similar to folder structure in google drive \(and sharing similar too\)
* VERY hierarchical \(think of how intl aid orgs, military, etc type structures work\)
* permissions are inherited, but do not over-ride protections on individual assets if restricted, etc.

## How's it Work?

**User**: is a global entity, they have access to whatever is created/shared with them, at the access level permissions/role shared.    
All of the elements within the app are ASSETS, to which a user is shared access and assigned a certain role for that asset  \(like in google drive\).

**Organisation**: is the top-level asset in the webapp, like a G-Suite organisation.

* An **organisation owner** permission is given to the user that created the org.
* Access to the org can be shared, with edit permissions to an **organisation manager**, who can manage the org on behalf of the owner.
* They can share and invite other users to the organisation, with specific permissions \(see below table\). 
* An org will be the top-level billing entity \(after we integrate billing\).

**Project**: projects sit under organisations, and have hierarchy like folders in google drive.

* The **project owner** permission is given to the user that created the project.
* Access to the project can be shared, with edit permissions to a **project manager**, who can manage the project on behalf of the owner.
* They can share and invite other users to the projects, with specific permissions \(see below table\). 
* Projects will be hierarchical billing entities, paying for their owned/child projects \(after we integrate billing\).

There are other entities where permissions apply, and gets quite complex once data-sources and such come into play; but, for now we just want the above basics.

## Permissions Specification Table

**All permissions are just based off the following:**

-&gt; **assetID** \(org, project, dash, tile, data, group, etc\)

* if this doesn't exist, they have no access to the asset with that assetID
* check in hierarchical order for user, to filter at highest level

-&gt; **Permission** \(owner, manager, contributor, guest edit, guest view, etc\)

* for an asset where the assetID is given to a user, then what is the permissions level
* can always view as have access, but extra functionality may be restricted, per access level

_As permissions are inherited, an org owner would be able to have permissions on everything in an org, unless it was expressly set as not being able to access \(private\), would be visible as existing, but would need to request to view/edit._

![Permission only to PROJECT LEVEL during this release](https://t6902024.p.clickup-attachments.com/t6902024/023d3400-3cec-4f36-9289-0317baaf4ff6/image.png)

NOTE:

* Overall access is based on sharing with users, similar to how it works in Google. drive, Clickup, Slack, AirTable, Miro, etc
* Spreadsheet source -&gt; [https://docs.google.com/spreadsheets/d/15eKNQurjpG-gUrt\_bcD32ltuZaLsBZGciqIcQOUaXCQ/edit?usp=sharing](https://docs.google.com/spreadsheets/d/15eKNQurjpG-gUrt_bcD32ltuZaLsBZGciqIcQOUaXCQ/edit?usp=sharing)

## Historical

~~There has been work done by Matt and Hamid on this ... but, not sure it seems aligned ??!?!?!?!~~

~~Hamid is doing via the ground up via Prisma, while Matt is approaching DBschema first ... maybe a mix of both will end up being the result ???~~

~~Approach suggested from Max, is via Role and attribute based approach, via plugin like:~~

* ~~~~[~~https://www.npmjs.com/package/@superawesome/permissions~~](https://www.npmjs.com/package/@superawesome/permissions)~~~~
* ~~~~[~~https://github.com/ntgussoni/blitz-guard~~](https://github.com/ntgussoni/blitz-guard)  ~~\(official blitzjs permissions package/library\)~~


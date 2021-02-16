# Roles, Permissions, ACL

## Relationship Fundamentals

* permissions and access is very similar to the way google drive works
* users - they can access what has been shared with them \(ACL user levels, and per user share\)
* organisation is the primary “account holder”
* projects belong to an organisation
* projects have info about the people, problem, place
* ownership and access of assets, data, etc in the webapp by user
* user-groups and sharing groups \(eg. share with everyone in org\) will come later.
* project partner/child relations, similar to folder structure in google drive \(and sharing similar too\)
* VERY hierarchical \(think of how intl aid orgs, military, etc type structures work\)
* permissions are inherited, but do not over-ride protections on individual assets if restricted, etc.

## How's it Work?

**User**: is a global entity, they have access to whatever is created/shared with them, at the access level/role shared.

**Organisation**: is the top-level asset in the webapp, like a G-Suite organisation.

* An **organisation owner** is the user that created the org.
* Access to the org can be shared, with edit permissions to an **organisation manager**, who can manage the org on behalf of the owner.
* They can share and invite other users to the organisation, with specific permissions \(see below table\). 
* An org will be the top-level billing entity \(after we integrate billing\).

**Project**: projects sit under organisations, and have hierarchy like folders in google drive.

* A **project owner** is the user that created the project.
* Access to the project can be shared, with edit permissions to a **project manager**, who can manage the project on behalf of the owner.
* They can share and invite other users to the projects, with specific permissions \(see below table\). 
* Projects will be hierarchical billing entities, paying for their owned/child projects \(after we integrate billing\).

There are other entities where permissions apply, and gets quite complex once data-sources and such come into play; but, for now we just want the above basics.

## Permissions Specification Table

![Permission only to PROJECT LEVEL during this release](https://t6902024.p.clickup-attachments.com/t6902024/023d3400-3cec-4f36-9289-0317baaf4ff6/image.png)

NOTE:

* Overall access is based on sharing with users, similar to how it works in Google. drive, Clickup, Slack, AirTable, Miro, etc
* Spreadsheet source -&gt; [https://docs.google.com/spreadsheets/d/15eKNQurjpG-gUrt\_bcD32ltuZaLsBZGciqIcQOUaXCQ/edit?usp=sharing](https://docs.google.com/spreadsheets/d/15eKNQurjpG-gUrt_bcD32ltuZaLsBZGciqIcQOUaXCQ/edit?usp=sharing)

## Progress

There has been work done by Matt and Hamid on this ... but, not sure it seems aligned ??!?!?!?!

Hamid is doing via the ground up via Prisma, while Matt is approaching DBschema first ... maybe a mix of both will end up being the result ???

Approach suggested from Max, is via Role and attribute based approach, via plugin like:  
[https://www.npmjs.com/package/@superawesome/permissions](https://www.npmjs.com/package/@superawesome/permissions)


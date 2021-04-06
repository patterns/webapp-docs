# Project Profile Fields

## Initial Project Entry Fields

**3 Step Form in UI** - ref [from mock](https://www.figma.com/proto/N9yF8ph0Ie3lOtFjgxryaM/v5-WebApp?kind=&node-id=262%3A5388&scaling=min-zoom)  --&gt;&gt;  See [Miro Flow](https://miro.com/app/board/o9J_kyYfLV0=/?moveToWidget=3074457354464890435&cot=10)

| Label | Type | Req'd |
| :--- | :--- | :--- |
| Project Name | text | \* |
| Description | text area | \* |
| Project Impacts | entered as list items \(json list\), or multiple as per below | \* |
| Desired Outcomes | entered as list items \(json list\), or multiple as per below | \* |
| Beneficiary Group Name \([multiple](https://www.figma.com/proto/N9yF8ph0Ie3lOtFjgxryaM/v5-WebApp?kind=&node-id=262%3A5388&scaling=min-zoom)\) | \(project one to many\) |  |
|  - Beneficiary Group Change \([multiple](https://www.figma.com/proto/N9yF8ph0Ie3lOtFjgxryaM/v5-WebApp?kind=&node-id=262%3A6047&scaling=min-zoom)\) | \(beneficiary one to many\) |  |
|  - Demographic\|Operator\|Value | \(beneficiary one to many\) [choice from global demographic variables](https://www.figma.com/proto/N9yF8ph0Ie3lOtFjgxryaM/v5-WebApp?kind=&node-id=262%3A5926&scaling=min-zoom) |  |
| Geolocation | lat / long / geocode  \(ref: [https://app.clickup.com/t/2ay5dk](https://app.clickup.com/t/2ay5dk)\) |  |
| Start Date \(UI select\) | Unix TIMESTAMP |  |
| End Date \(UI select\) | Unix TIMESTAMP |  |

note: there are more fields coming for entry into the Project Profile in future releases, but these are the only ones being implemented now.

## Extra Fields for UI / Data Elements

| Label | Type |
| :--- | :--- |
| Project Logo | image/ |
| Project Banner | image/ |
| projectIndicatorIDs | json string |
| ? owner/users ? |  |
|  |  |


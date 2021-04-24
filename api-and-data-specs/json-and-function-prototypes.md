---
description: To ensure all parts of the app maintain consistent JSON objects
---

# JSON & Function Prototypes

Here are are formats we will use.

### **Returning JSON from ANY function**

**Failure**

```text
{
    "success": False,
    "reason": "Somethong that can be displayed to the user if need be",
    "error": "Meaningful error details useful to a dev to debug"
}
```

**Success**

```text
{
    "success": True,
    "data": {
               "key1": "data",
               "key2": "data" 
            } 


}
```

### Receiving JSON into a Function

All data passed into a function should be of a standardized format, we want certain identifying data to be in the same place all the time, allowing us to use shared functionality more efficientlyIf an elemnet specified here is not available it must be included with a null valueIf the function does not need a specific element, it should be included, it may be required in the future, we want to minimise code refactoring for future enhancements**We are highly likely to provide wrapper functions to handle the formatting of the Json so its consistent, when these are available, details will be posted here**

```text
{
    "userid": 1,
    "projectid": 2,
    "connectorid": 3,
    "dashboardid": 4,
    "userData": {
        "key1": "data",
        "key2": "data"
    },
    "projectData": {
        "key1": "data",
        "key2": "data"
    },
    "connectorData": {
        "key1": "data",
        "key2": "data"
    },
    "dashboardData": {
        "key1": "data",
        "key2": "data"
    },
    "data": {
        "key1": "data",
        "key2": "data"
    }
}
```

### Function Prototypes

As a rule, we want most functions to follow certain standards

```text
def myFunction ( request, dataJSON, db = None, logger = None )
```

where:

* `request` is the request object
* `dataJson` is Json as specified above
* `db` is an object pointing to an already open instance of a isgood\_database connection
* `logger` is an object pointing to an already open instance of an isgood\_logger


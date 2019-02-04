---
uid: eisk-webapi-exception-handling
---
# Exception Handling

## Web Api Exceptions over Http

In Eisk Web API, an exception can be triggered either from system level exceptions or from domain validation actions.   

Errors are the inside components of specific exceptions. A given type of such exception can contain different types of errors as defined by the class structure. 

Errors as exposed by API belong to one of the following types, which are required to be parsed accordingly by the consuming services (such as an ASP.NET MVC Application).  
 
### Aggregated Domain Error

The error is returned to caller services as aggregated list of errors when one or more validation fails on the submitted model. 

    {
    	"message": "The request is invalid.",
    	"modelState": {
    		"entity.FirstName": ["First name is required."],
    		"entity.LastName": ["Last name is required"]
    	}
    }

### Generic Error

The error is triggered to caller service when domain validation fails that is submitted or an internal system exception occurs.

Sample Response:

    {
    	"ErrorMessage": "There is a problem connecting dependent service. Please wait and check later.",
    	"ErrorCode": "ID-001",
    	"HttpCode": 500
    }

---
title: SmartCode API Reference

language_tabs:
  - shell: cURL
  - vb: vba

toc_footers:
  - <a href='https://mysmartcode.com/developers/signup'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the SmartCode API! If you do not have an API key yet, please sign up for one <a href="https://mysmartcode.com/developers/signup">here</a>. The SmartCode API provides developers with direct access to our backend for use within their medical applications.

Code samples are provided to the right of each section.

# General Equivalence Mappings (GEMs)

## ICD9 to ICD10


> Example Request

```shell
curl https://api.mysmartcode.com/dev/icd9/gems?q=250.00&callback=angular.callback_0d&token=abcdef1234567890
```

```vb
Dim result As String
Dim myURL As String
Dim winHttpReq As Object
Set winHttpReq = CreateObject("WinHttp.WinHttpRequest.5.1")
 
myURL = "https://api.mysmartcode.com/dev/icd9/gems?q=250.00&token=abcdef1234567890"
 
winHttpReq.Open "GET", myURL, False
winHttpReq.Send
 
result = winHttpReq.responseText
```

> Example Response

```shell
{
    "results": {
        "query": "250.00",
        "codes_searched": "250.00",
        "count": "1",
        "type": "icd9",
        "crosswalk": {
            "diag": {
                "name": "250.00",
                "desc": "Diabetes mellitus, Diabetes mellitus without mention of complication, type II or unspecified type, not stated as uncontrolled",
                "fifth_code_details": "Fifth-digit 0 is for use for type II patients, even if the patient requires insulin;Use additional code, if applicable, for associated long-term (current) insulin use V58.67"
            },
            "cross": [
                {
                    "diag": {
                        "name": "E11.9",
                        "desc": "Type 2 diabetes mellitus without complications"
                    },
                    "icd9gem": {
                        "icd9code": "250.00",
                        "icd10code": "E11.9",
                        "flag": "10000"
                    },
                    "icd10_cross": {
                        "icd10gem": {
                            "icd10code": "E11.9",
                            "icd9code": "250.00",
                            "flag": "10000"
                        }
                    }
                },
                {
                    "diag": {
                        "name": "E11.9",
                        "desc": "Type 2 diabetes mellitus without complications"
                    },
                    "icd10gem": {
                        "icd10code": "E11.9",
                        "icd9code": "250.00",
                        "flag": "10000"
                    },
                    "icd10_cross": {
                        "icd10gem": {
                            "icd10code": "E11.9",
                            "icd9code": "250.00",
                            "flag": "10000"
                        }
                    }
                },
                {
                    "diag": {
                        "name": "E13.9",
                        "desc": "Other specified diabetes mellitus without complications"
                    },
                    "icd10gem": {
                        "icd10code": "E13.9",
                        "icd9code": "250.00",
                        "flag": "10000"
                    },
                    "icd10_cross": [
                        {
                            "icd10gem": {
                                "icd10code": "E13.9",
                                "icd9code": "249.00",
                                "flag": "10000"
                            }
                        },
                        {
                            "icd10gem": {
                                "icd10code": "E13.9",
                                "icd9code": "250.00",
                                "flag": "10000"
                            }
                        }
                    ]
                }
            ]
        }
    }
}
```

```vba
{
    "results": {
        "query": "250.00",
        "codes_searched": "250.00",
        "count": "1",
        "type": "icd9",
        "crosswalk": {
            "diag": {
                "name": "250.00",
                "desc": "Diabetes mellitus, Diabetes mellitus without mention of complication, type II or unspecified type, not stated as uncontrolled",
                "fifth_code_details": "Fifth-digit 0 is for use for type II patients, even if the patient requires insulin;Use additional code, if applicable, for associated long-term (current) insulin use V58.67"
            },
            "cross": [
                {
                    "diag": {
                        "name": "E11.9",
                        "desc": "Type 2 diabetes mellitus without complications"
                    },
                    "icd9gem": {
                        "icd9code": "250.00",
                        "icd10code": "E11.9",
                        "flag": "10000"
                    },
                    "icd10_cross": {
                        "icd10gem": {
                            "icd10code": "E11.9",
                            "icd9code": "250.00",
                            "flag": "10000"
                        }
                    }
                },
                {
                    "diag": {
                        "name": "E11.9",
                        "desc": "Type 2 diabetes mellitus without complications"
                    },
                    "icd10gem": {
                        "icd10code": "E11.9",
                        "icd9code": "250.00",
                        "flag": "10000"
                    },
                    "icd10_cross": {
                        "icd10gem": {
                            "icd10code": "E11.9",
                            "icd9code": "250.00",
                            "flag": "10000"
                        }
                    }
                },
                {
                    "diag": {
                        "name": "E13.9",
                        "desc": "Other specified diabetes mellitus without complications"
                    },
                    "icd10gem": {
                        "icd10code": "E13.9",
                        "icd9code": "250.00",
                        "flag": "10000"
                    },
                    "icd10_cross": [
                        {
                            "icd10gem": {
                                "icd10code": "E13.9",
                                "icd9code": "249.00",
                                "flag": "10000"
                            }
                        },
                        {
                            "icd10gem": {
                                "icd10code": "E13.9",
                                "icd9code": "250.00",
                                "flag": "10000"
                            }
                        }
                    ]
                }
            ]
        }
    }
}
```


The GEMs provide a mapping between ICD9 codes and ICD10 codes. This endpoint provides the ICD10 equivalents to an ICD9 code. 
<aside class="notice">
This endpoint will perform a query for subcodes if the query does not return a value. For example, a search for `250.0` will not yield any results, so the system will search on the following codes to provide a result: 250.00, 250.01, 250.02, 250.03
</aside>

### HTTP Request

`GET /icd9/gems`

### Response
### Query Parameters

Parameter | Required | Description
--------- | ------- | -----------
q | true | The ICD9 code to be searched
token | true | Your API Token
callback | false | The callback parameter for JSONP requests

### The `results` object

Parameter | Description
--------- | -------
query | The incoming query from the `q` parameter
codes_searched | The codes and subcodes searched
count | The number of GEMs found
type | The codebase, `ICD9`
crosswalk | The object containing the GEMs information

### The `crosswalk` object
This object will be a hash if there is only one item, or it will be an array if there are multiple
items. These items are the GEMs for the query.

Parameter | Description
--------- | -------
diag  | The object containing information about the ICD9 code
cross | The object containing the GEMs data for the ICD9 in diag

### The `diag` object

Parameter | Description
--------- | -------
desc | The long description for the code in the codebase
fifth_code_details | Includes information about the required fifth code, if it exists

### The `cross` object
The cross object contains all the GEMs linked to this code

Parameter | Description
--------- | -------
diag | The ICD10 code information
icd9gem | The object containing GEM information about the ICD9-ICD10
icd10_cross | The GEM information for this ICD10 code

### The `icd9gem` object

Parameter | Description
--------- | -------
icd9code | The ICD9 code
icd10code |The ICD10 code
flag | The flag definition of the GEM

### The `icd10_cross` object
The icd10_cross object is included for completeness and includes the crosswalk data for the
ICD10 code. This is either a hash or array of icd10gem objects.

### The `icd10gem` object
Parameter | Description
--------- | -------
icd10code | The ICD10 code
icd9code | The ICD9 code
flag | The flag definition of the GEM

## ICD10 to ICD9

To be documented.

## GEMs Flags

Flags `3` and `4` are used to clarify the combination flag (Flag `2`)

Position | Name | Notes | Example
--------- | ------- | --------- | -------
0 | Approximate | 1 = translation is approximate; 0 = translation is identical | `1`0112
1 | No Map | 1 = no plausible translation; 0 = at least one plausible translation | 1`0`112
2 | Combination | 1 = the code maps to more than one code; 0 = the code maps to a single code | 10`1`12
3 | Scenario | More then one code is required in the target system. | 101`1`2
4 | Choice List | Used the translation alternatives in a combination code | 1011`2`
---
title: "Credit Limit Service"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "BRM"
weight: 302
toc: false
---

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /brm/v1/creditlimit/{accountNo}
{{% /method-block %}}

This service allows you to fetch the credit limit details of an account number from BRM.

It requires accountNo, token, correlationid, srdate, source, operation and destination as input parameters. If successful it will return credit limit details. If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **accountNo** (mandatory)    | ``string`` (path) | Provide the account number of which you want to view the balance details. |
| **token** (optional)    | ``string`` (header) | Provide the token of the ticket. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
accountNo:string
token:string
correlationId:SO-100
operation:emailExists
destination:CRM
source:Selfcare
srDate:11-09-2021
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "success": "true",
      "arguments": {
        "accountNo": "ACC10831",
        "range": 900
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Client Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "success": "false",
      "arguments": {
        "errorCode": "6000003",
        "errorMessage": "BRM Error -Invalid account number"
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Server Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "false",
    "result": {
      "arguments": {
        "errorCode": "6000003",
        "errorMessage": "BRM Error -ERR_NAP_CONNECT_FAILED"
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
/crm/v1/social/ticket
{{% /method-block %}}

This service is used to update the credit limit of the customer. It requires correlationId, srdate, source, operation and destination as input parameters. If successful it will update the credit limit of the customer. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (optional)    | ``string`` (header) | Provide the token of the ticket. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (optional)    | ``string`` (header) | Provide the token of the ticket. |
| **correlationId** (mandatory)    | ``string`` (body)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (body)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (body)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (body)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (body)      |    Provide the destination as the value. |

{{< tabs "uniqueid1" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:SO-101
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:verifyOTP
{{< / highlight >}}
{{< /tab >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
  "poid": "string",
  "accountNo": "string",
  "creditLimit": 0,
  "programName": "string",
  "flag": "string"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "success": "true",
      "arguments": {
        "accountNo": "ACC10831",
        "range": 900
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Client Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "success": "false",
      "arguments": {
        "errorCode": "6000003",
        "errorMessage": "BRM Error -Invalid account number"
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Server Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "false",
    "result": {
      "arguments": {
        "errorCode": "6000003",
        "errorMessage": "BRM Error -ERR_NAP_CONNECT_FAILED"
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

{{% method-block bgcolor="warning" type="bg-orange" callmethod="PUT" %}}
  /brm/v1/service/modification
{{% /method-block %}}

This service is used to modify the status of the customer in BRM.

<section>

{{< tabs "uniqueid1" >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
  "header": {
    "operation": "string",
    "serviceRequestId": "string",
    "requestorChannel": "string",
    "srDate": "string",
    "backendChannel": "string",
    "correlationId": "string",
    "subOperation": "string"
  },
  "message": {
    "accounts": [
      {
        "poid": "string",
        "accountNo": "string",
        "programName": "string",
        "nameInfo": [
          {
            "elem": "string",
            "address": "string",
            "city": "string",
            "company": "string",
            "contactType": "string",
            "country": "string",
            "emailAddr": "string",
            "firstName": "string",
            "lastName": "string",
            "middleName": "string",
            "salutation": "string",
            "state": "string",
            "zip": "string",
            "phones": [
              {
                "elem": "string",
                "phone": "string",
                "type": "string"
              }
            ]
          }
        ],
        "profiles": [
          {
            "elem": "string",
            "deviceId": "string",
            "autoRenewFlags": "string",
            "subscriberPreferences": [
              {
                "elem": "string",
                "value": "string",
                "name": "string",
                "subscriberPreferenceId": "string"
              }
            ]
          }
        ],
        "billInfo": [
          {
            "elem": "string",
            "actgFutureDom": "string"
          }
        ]
      }
    ]
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "arguments": {
        "RESULTS": [
          {
            "DESCR": "Account modified Successfully",
            "ERROR_NUM": 0,
            "POID": "0.0.0.1 /profile/csmart 19483041 25"
          }
        ]
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Client Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "success": "false",
      "arguments": {
        "errorCode": "6000003",
        "errorMessage": "BRM Error -Invalid account number"
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Server Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "false",
    "result": {
      "arguments": {
        "errorCode": "6000003",
        "errorMessage": "BRM Error -ERR_NAP_CONNECT_FAILED"
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

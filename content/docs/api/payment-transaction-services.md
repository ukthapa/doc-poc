---
title: "Payment Transaction Services"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "CRM"
weight: 208
toc: false
---

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
  /crm/v1/services/transactionInfo
{{% /method-block %}}

This service is used to save the payment transaction of the bills. It requires correlationId, operation, destination, source, token, srDate as input parameters . If successful the payment transaction details will be saved related to particular bills. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **amount** (mandatory)    | ``string`` (body)      |   Provide the amount as the value. For example - 201 |
| **orderId** (mandatory)    | ``string`` (body)      |   Provide the order Id as the value. For example - S017287 |
| **processingStatus** (mandatory)    | ``string`` (body)      |   Provide the processing status as the value. For example - Success |
| **softDescriptor** (mandatory)    | ``string`` (body)      |   Provide the soft descriptor as the value. For example - bolton |
| **currency** (mandatory)    | ``string`` (body)      |   Provide the currency as the value. For example - US |
| **amount** (mandatory)    | ``string`` (body)      |   Provide the amount as the value. For example - 201 |
| **transaction** (mandatory) | ``string`` (body)      |    Provide the transaction number as the value. For example - 8878 |
| **date** (mandatory)    | ``string`` (body)      |   Provide the transaction date as the value. For example - 2019-08-03T20:00:25Z |
| **source** (mandatory)    | ``string`` (body)      |   Provide the source date as the value. For example - app |

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
    "amount": "201",
    "orderId": "SO17287",
    "processingStatus": "Success",
    "softDescriptor": "bolton",
    "currency": "US",
    "transactionId": "8878",
    "date": "2019-08-03T20:00:25Z",
    "source": "app"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "message": "Payment submitted successfully"
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
      "arguments": {
        "statusCode": "400",
        "errorCode": "400 BAD_REQUEST",
        "errorMessage": "Header 'source' not present in the request."
      }
    },
    "success": "false"
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
        "statusCode": "500",
        "errorCode": "Downstream error",
        "errorMessage": "- Not Able to connect with CRM."
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

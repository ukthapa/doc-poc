---
title: "Email Notfication Controller"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "NS"
weight: 402
toc: false
---

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
/notification/v1/user/email
{{% /method-block %}}

This service is used to send simple email to the user.

It requires correlationId, serviceProvider, srdate, operation and requestorChannel as input header parameters and EmailNotificationRequest object as request body. If successful the system will send email to the customer. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **requestorChannel** (mandatory) | ``string`` (header)      |    Provide the requestorChannel. |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **serviceProvider** (mandatory) | ``string`` (header)      |    Provide the name of the service provider. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (body)      |   Provide the correlationId as the value. For example - SO-100 |
| **requestorChannel** (mandatory) | ``string`` (body)      |    Provide the requestorChannel. |
| **srdate** (mandatory) | ``string`` (body)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (body)      |    Provide the operation as the value. For example - emailExists |
| **serviceProvider** (mandatory) | ``string`` (body)      |    Provide the name of the service provider. |

{{< tabs "uniqueid2" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:SO-101
requestorChannel:string
serviceProvider:string
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:verifyOTP
{{< / highlight >}}
{{< /tab >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
  "header": {
    "correlationId": "string",
    "operation": "string",
    "requestorChannel": "string",
    "srDate": "string",
    "serviceProvider": "string",
    "backendChannel": "string"
  },
  "message": {
    "activityId": "string",
    "channel": "string",
    "notificationType": "string",
    "content": {
      "message": "string",
      "from": "string",
      "data": {
        "firstName": "string",
        "lastName": "string",
        "email": "string",
        "cc": "string",
        "bcc": "string",
        "salutation": "string",
        "middleName": "string",
        "accountNumber": "string",
        "mobNumber": "string",
        "imsi": "string",
        "imei": "string",
        "plan": "string",
        "userId": "string",
        "password": "string",
        "createDate": "string",
        "paymentMethod": "string",
        "paymentReceiver": "string",
        "total": "string",
        "balance": "string",
        "treceipt": "string",
        "userExpiryDate": "string",
        "autoRegAccountName": "string",
        "userPaymentBalance": "string",
        "billIndex": "string",
        "invoiceNumber": "string",
        "partnerId": "string",
        "environment": "string",
        "comment": "string",
        "supportEmail": "string",
        "partnerContactNumber": "string",
        "partnerEmail": "string",
        "partnerStatus": "string",
        "loginUrl": "string"
      },
      "attachments": [
        {
          "fileName": "string",
          "filePath": "string"
        }
      ]
    },
    "recipients": [
      {
        "to": "string",
        "name": "string",
        "cc": [
          "string"
        ],
        "bcc": [
          "string"
        ]
      }
    ],
    "templateType": "string"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "email": "karthikeyantest003@yopmail.com",
      "message": "Email has been sent"
    },
    "success": "SUCCESS"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Client Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "message": "Missing request header 'srDate' for method parameter of type String"
    },
    "success": "FAILED"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Server Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "message": "Illegal address"
    },
    "success": "FAILED"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
/notification/v1/vl/email
{{% /method-block %}}

This service is used to send simple email to the partner.

<section>

{{< tabs "uniqueid3" >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
  "header": {
    "correlationId": "string",
    "operation": "string",
    "requestorChannel": "string",
    "srDate": "string",
    "serviceProvider": "string",
    "backendChannel": "string"
  },
  "message": {
    "subject": "string",
    "templateType": "string",
    "data": {
      "firstName": "string",
      "lastName": "string",
      "email": "string",
      "cc": "string",
      "bcc": "string",
      "salutation": "string",
      "middleName": "string",
      "accountNumber": "string",
      "mobNumber": "string",
      "imsi": "string",
      "imei": "string",
      "plan": "string",
      "userId": "string",
      "password": "string",
      "createDate": "string",
      "paymentMethod": "string",
      "paymentReceiver": "string",
      "total": "string",
      "balance": "string",
      "treceipt": "string",
      "userExpiryDate": "string",
      "autoRegAccountName": "string",
      "userPaymentBalance": "string",
      "billIndex": "string",
      "invoiceNumber": "string",
      "partnerId": "string",
      "environment": "string",
      "comment": "string",
      "supportEmail": "string",
      "partnerContactNumber": "string",
      "partnerEmail": "string",
      "partnerStatus": "string",
      "loginUrl": "string"
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "email": "support@xyz.com",
      "message": "Email has been sent"
    },
    "success": "SUCCESS"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Client Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "message": "Missing request header 'srDate' for method parameter of type String"
    },
    "success": "FAILED"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Server Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "message": "Subject must not be null"
    },
    "success": "FAILED"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

---
title: "SMS Notification Controller"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "NS"
weight: 404
toc: false
---

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
​/notification​/smpp​/v1​/user​/sms
{{% /method-block %}}

This service is used to send custom SMS to specified number based on SMS template specified in the request using SMPP protocol.

It requires correlationId, serviceProvider, srdate, operation, destination as input header parameters and SmsNotificationRequest Object as request body. If successful the system will send email to the customer. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **source** (mandatory) | ``string`` (header)      |    Provide the source as the value. |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **source** (mandatory) | ``string`` (header)      |    Provide the source as the value. |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid2" >}}
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
  "activityId": "string",
  "channel": "string",
  "from": "string",
  "message": "string",
  "shortCode": "string",
  "messageKey": "string",
  "notificationType": "string",
  "content": {
    "message": "string",
    "from": "string",
    "data": {
      "userId": "string",
      "mobNumber": "string",
      "accountNumber": "string",
      "password": "string",
      "expiryDate": "string",
      "total": "string",
      "plan": "string",
      "email": "string",
      "msisdn": "string",
      "segment": "string",
      "amount": "string",
      "voucherCode": "string",
      "addOnName": "string",
      "ticketNo": "string",
      "tickekStatus": "string",
      "accountStatus": "string",
      "startDate": "string",
      "updateDate": "string"
    }
  },
  "msisdn": "string",
  "shortMessage": "string",
  "shortCodeNumber": "string",
  "recipients": [
    "string"
  ],
  "templateType": "string",
  "EventName": "string",
  "EventCode": "string"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "SUCCESS",
    "result": {
      "mobNumber": "447368011035",
      "message": "Message has been sent.",
      "messageId": "436b6454-d2bc-4dbb-9e10-ed01ac6facc5"
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
      "message": "Missing request header 'correlationId' for method parameter of type String"
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
    "success": "FAILED",
    "result": {
      "message": "Exception occurred while sending SMS to 99219703 and error is :- Negative response 00000061 (Invalid Scheduled Delivery Time) found"
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
​/notification/smpp/v1/bulk/sms
{{% /method-block %}}

This service is used to send custom bulk SMS to specified number based on SMS template specified in the request using SMPP protocol.

It requires correlationId, serviceProvider, srdate, operation, destination as input header parameters and SmsNotificationRequest Object as request body. If successful the system will send email to the customer. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **source** (mandatory) | ``string`` (header)      |    Provide the source as the value. |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **source** (mandatory) | ``string`` (header)      |    Provide the source as the value. |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid3" >}}
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
  "activityId": "string",
  "channel": "string",
  "from": "string",
  "message": "string",
  "shortCode": "string",
  "messageKey": "string",
  "notificationType": "string",
  "content": {
    "message": "string",
    "from": "string",
    "data": {
      "userId": "string",
      "mobNumber": "string",
      "accountNumber": "string",
      "password": "string",
      "expiryDate": "string",
      "total": "string",
      "plan": "string",
      "email": "string",
      "msisdn": "string",
      "segment": "string",
      "amount": "string",
      "voucherCode": "string",
      "addOnName": "string",
      "ticketNo": "string",
      "tickekStatus": "string",
      "accountStatus": "string",
      "startDate": "string",
      "updateDate": "string"
    }
  },
  "msisdn": "string",
  "shortMessage": "string",
  "shortCodeNumber": "string",
  "recipients": [
    "string"
  ],
  "templateType": "string",
  "EventName": "string",
  "EventCode": "string"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "SUCCESS",
    "result": {
      "mobNumber": "447368011035",
      "message": "Message has been sent.",
      "messageId": "436b6454-d2bc-4dbb-9e10-ed01ac6facc5"
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
      "message": "Missing request header 'correlationId' for method parameter of type String"
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
    "success": "FAILED",
    "result": {
      "message": "Exception occurred while sending sms to 99219703 and error is :- Negative response 00000061 (Invalid Scheduled Delivery Time) found"
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

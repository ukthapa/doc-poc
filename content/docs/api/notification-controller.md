---
title: "Notification Controller"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "NS"
weight: 403
toc: false
---

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
/fcm/notification
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
  "deviceId": "string",
  "firebaseTockenId": [
    "string"
  ],
  "notification": {
    "title": "string",
    "body": "string"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "token": "projects/csmart-72685/messages/0:1627468730646285%9fea26239fea2623"
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
    "result": {
      "message": "Exactly one of token, topic or condition must be specified"
    },
    "success": "FAILED"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

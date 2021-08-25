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
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **requestorChannel** (mandatory) | ``string`` (header)      |    Provide the requestorChannel. |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **serviceProvider** (mandatory) | ``string`` (header)      |    Provide the name of the service provider. |

#### *Request Body Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| **deviceId** (mandatory)    | ``string`` (header)      |   Provide the deviceId as the value. For example - 1234A |
| {{< expand id="testing1" atext="firebaseTockenId (array)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>firebaseTockenId</td>
<td>string</td>
<td>Provide the fire base token id as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing2" atext="notification (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>title</td>
<td>string</td>
<td>Provide the title of the notification as the value.</td>
</tr>
<tr>
<td>body</td>
<td>string</td>
<td>Provide the body of the notification as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
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
  "deviceId": "1234A",
  "firebaseTockenId": [
    "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJWVVMiLCJqdGkiOiJ0YXRhbW92ZSMxI1ZVUyNvasadfwredbd"
  ],
  "notification": {
    "title": "Update Password",
    "body": "Password is updated successfully"
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

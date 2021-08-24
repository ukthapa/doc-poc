---
title: "SMS Controller"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "NS"
weight: 401
toc: false
---

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
/notification/sms/v1
{{% /method-block %}}

This service is used to send custom SMS to specified number based on the SMS template specified in request using SMS gateway provider.

It requires correlationId, srdate, source, operation and destination as input parameters and SmsNotificationRequest object as request body. If successful the system will send SMS to the customer. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

#### *Request Body Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| **to** (mandatory)    | ``string`` (query) | Provide the phone number to whom the SMS will be sent as the value. |
| **cc** (mandatory)    | ``string`` (query) | Provide the email address to whom the email will be copied as the value. |
| **bcc** (mandatory)    | ``string`` (query) | Provide the email address to whom the email will be sent as bcc as the value. |
| **replyTo** (mandatory)    | ``string`` (query) | Provide the email address to whom the reply of the email will go as the value. |
| **subject** (mandatory)    | ``string`` (query) | Provide the subject of the notification as the value. |
| **content** (mandatory)    | ``string`` (query) | Provide the content of the notification as the value. |
| **attachment** (mandatory)    | ``string`` (query) | Provide the attachment of the notification as the value. |
| **type** (mandatory)    | ``string`` (query) | Provide the type of the notification as the value. For example - ACCOUNT_CREATE |
| {{< expand id="testing1" atext="UserInfo (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>FirstName</td>
<td>string</td>
<td>Provide the first name as the value.</td>
</tr>
<tr>
<td>MiddleName</td>
<td>string</td>
<td>Provide the middle name as the value.</td>
</tr>
<tr>
<td>LastName</td>
<td>string</td>
<td>Provide the last name as the value.</td>
</tr>
<tr>
<td>accountNumber</td>
<td>string</td>
<td>Provide the account number as the value.</td>
</tr>
<tr>
<td>mobNumber</td>
<td>string</td>
<td>Provide the mobile phone number as the value.</td>
</tr>
<tr>
<td>email</td>
<td>string</td>
<td>Provide the email address as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing2" atext="data (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>address</td>
<td>string</td>
<td>Provide the address as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| **requestType** (mandatory) | ``string``       |    Provide the type of request as the value. For example - simpleSMS |
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
  "to": "9620757121",
  "cc": "kiran@gmail.com",
  "bcc": "sai@gmail.com",
  "replyTo": "venky@gmail.com",
  "subject": "Custom Subject",
  "content": "This is custom msg",
  "attachment": "string",
  "type": "ACCOUNT_CREATE",
  "userInfo": {
    "firstName": "Shanthamma",
    "middleName": "S",
    "lastName": "Shivanna",
    "accountNumber": "10000190",
    "mobNumber": "8789890006",
    "email": "shnathi@gmail.com"
  },
  "data": {
    "Address": "v-37 chnnapatna"
  },
  "requestType": "simpleSMS"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "message": "SMS processed successfully."
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
      "message": "Missing request header 'destination' for method parameter of type String"
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
      "message": "Invalid Content Details,Note1: Don't use symbols  # + & in API Url, Note2: instead of variable symbol {#var#} , mention any values in API Url"
    },
    "success": "FAILED"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
/notification/sms/v1/campaign
{{% /method-block %}}

This service is used to send campaign SMS to specified numbers using SMS gateway provider.

It requires correlationId, srdate, source, operation and destination as input parameters and SmsNotificationRequest object as request body. If successful the system will send SMS to the customer. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

#### *Request Body Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| **to** (mandatory)    | ``string`` (query) | Provide the phone number to whom the SMS will be sent as the value. |
| **cc** (mandatory)    | ``string`` (query) | Provide the email address to whom the email will be copied as the value. |
| **bcc** (mandatory)    | ``string`` (query) | Provide the email address to whom the email will be sent as bcc as the value. |
| **replyTo** (mandatory)    | ``string`` (query) | Provide the email address to whom the reply of the email will go as the value. |
| **subject* (mandatory)    | ``string`` (query) | Provide the subject of the notification as the value. |
| **content** (mandatory)    | ``string`` (query) | Provide the content of the notification as the value. |
| **attachment** (mandatory)    | ``string`` (query) | Provide the attachment of the notification as the value. |
| **type** (mandatory)    | ``string`` (query) | Provide the type of the notification as the value. For example - ACCOUNT_CREATE |
| {{< expand id="testing3" atext="UserInfo (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>FirstName</td>
<td>string</td>
<td>Provide the first name as the value.</td>
</tr>
<tr>
<td>MiddleName</td>
<td>string</td>
<td>Provide the middle name as the value.</td>
</tr>
<tr>
<td>LastName</td>
<td>string</td>
<td>Provide the last name as the value.</td>
</tr>
<tr>
<td>accountNumber</td>
<td>string</td>
<td>Provide the account number as the value.</td>
</tr>
<tr>
<td>mobNumber</td>
<td>string</td>
<td>Provide the mobile phone number as the value.</td>
</tr>
<tr>
<td>email</td>
<td>string</td>
<td>Provide the email address as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing4" atext="data (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>address</td>
<td>string</td>
<td>Provide the address as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| **requestType** (mandatory) | ``string``       |    Provide the type of request as the value. For example - simpleSMS |

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
  "to": "9620757121",
  "cc": "kiran@gmail.com",
  "bcc": "sai@gmail.com",
  "replyTo": "venky@gmail.com",
  "subject": "Custom Subject",
  "content": "This is custom msg",
  "attachment": "string",
  "type": "ACCOUNT_CREATE",
  "userInfo": {
    "firstName": "Shanthamma",
    "middleName": "S",
    "lastName": "Shivanna",
    "accountNumber": "10000190",
    "mobNumber": "8789890006",
    "email": "shnathi@gmail.com"
  },
  "data": {
    "Address": "v-37 chnnapatna"
  },
  "requestType": "simpleSMS"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "message": "SMS processed successfully."
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
      "message": "Missing request header 'destination' for method parameter of type String"
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
      "message": "Invalid Content Details,Note1: Don't use symbols  # + & in API Url, Note2: instead of variable symbol {#var#} , mention any values in API Url"
    },
    "success": "FAILED"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
/notification/sms/v1/simple
{{% /method-block %}}

This service is used to send simple SMS to specified numbers.

It requires correlationId, srdate, source, operation and destination as input parameters and SmsNotificationRequest object as request body. If successful the system will send SMS to the customer. If failed the appropriate error code will be returned.

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
| **to** (mandatory)    | ``string`` (body)      |   Provide the phone number where to send the SMS as the value. For example - 9620757121 |
| **content** (mandatory)    | ``string`` (body)      |   Provide the content of the SMS as the value. For example - This is custom message |
| **subject** (mandatory)    | ``string`` (body)      |   Provide the subject of the SMS as the value. For example - Custom message |
| **requestType** (mandatory)    | ``string`` (body)      |   Provide the request type of the SMS as the value. For example - simpleSMS |

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
    "to": "9620757121",
    "content": "This is custom msg",
    "subject": "Custom Subject",
    "requestType": "simpleSMS"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "message": "SMS processed successfully."
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
      "message": "Missing request header 'destination' for method parameter of type String"
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
      "message": "Invalid Content Details,Note1: Don't use symbols  # + & in API Url, Note2: instead of variable symbol {#var#} , mention any values in API Url"
    },
    "success": "FAILED"
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

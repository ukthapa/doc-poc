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
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - smppUserSms |
| **source** (mandatory) | ``string`` (header)      |    Provide the source as the value. |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

#### *Request Body Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| **activityId** (mandatory)    | ``string`` (query) | Provide the activity id as the value. For example - accountCreation |
| **channel** (mandatory)    | ``string`` (query) | Provide the channel of notification as the value. For example - SMS |
| **from** (mandatory)    | ``string`` (query) | Provide from whom the notification will be sent as the value. |
| **message** (mandatory)    | ``string`` (query) | Provide the message as the value. |
| **shortCode** (mandatory)    | ``string`` (query) | Provide the short code of the notification as the value. For example - 12345 |
| **messageKey** (mandatory)    | ``string`` (query) | Provide the message key of the notification as the value. For example - sms123 |
| **notificationType** (mandatory)    | ``string`` (query) | Provide the type of notification as the value. |
| {{< expand id="testing1" atext="content (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>message</td>
<td>string</td>
<td>Provide the message of the notification as the value.</td>
</tr>
<tr>
<td>from</td>
<td>string</td>
<td>Provide the from whom the notification will be sent as the value.</td>
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
<td>userId</td>
<td>string</td>
<td>Provide the user id as the value.</td>
</tr>
<tr>
<td>mobNumber</td>
<td>string</td>
<td>Provide the mobile phone number as the value.</td>
</tr>
<tr>
<td>accountNumber</td>
<td>string</td>
<td>Provide the account number as the value.</td>
</tr>
<tr>
<td>password</td>
<td>string</td>
<td>Provide the password as the value.</td>
</tr>
<tr>
<td>expiryDate</td>
<td>string</td>
<td>Provide the expiry date as the value.</td>
</tr>
<tr>
<td>total</td>
<td>string</td>
<td>Provide the total notifications to be sent as the value.</td>
</tr>
<tr>
<td>plan</td>
<td>string</td>
<td>Provide the type of plan as the value. For example - F&F Offer 60GB17.5K ACE</td>
</tr>
<tr>
<td>email</td>
<td>string</td>
<td>Provide the email as the value.</td>
</tr>
<tr>
<td>msidn</td>
<td>string</td>
<td>Provide the msidn number as the value.</td>
</tr>
<tr>
<td>segment</td>
<td>string</td>
<td>Provide the segment as the value. For example - Prepaid</td>
</tr>
<tr>
<td>voucherCode</td>
<td>string</td>
<td>Provide the voucher code as the value.</td>
</tr>
<tr>
<td>addOnName</td>
<td>string</td>
<td>Provide the add on name as the value. For example - msidn</td>
</tr>
<tr>
<td>ticketNo</td>
<td>string</td>
<td>Provide the ticket number as the value.</td>
</tr>
<tr>
<td>ticketStatus</td>
<td>string</td>
<td>Provide the ticket status as the value.</td>
</tr>
<tr>
<td>accountStatus</td>
<td>string</td>
<td>Provide the account status as the value.</td>
</tr>
<tr>
<td>startDate</td>
<td>string</td>
<td>Provide the start date as the value.</td>
</tr>
<tr>
<td>updateDate</td>
<td>string</td>
<td>Provide the update date as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| **misisdn** (mandatory)    | ``string`` (query) | Provide the msisdn number as the value. For example - 123456789 |
| **shortMessage** (mandatory)    | ``string`` (query) | Provide the short message as the value. |
| **shortCodeNumber** (mandatory)    | ``string`` (query) | Provide from short code number as the value. For example - 12345 |
| {{< expand id="testing3" atext="recipients (array)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>email</td>
<td>string</td>
<td>Provide the email address of the recipient as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| **templateType** (mandatory)    | ``string`` (query) | Provide the type of template as the value. For example - WELCOME |
| **EventName** (mandatory)    | ``string`` (query) | Provide the name of the event as the value. For example - ProductUpdate |
| **EventCode** (mandatory)    | ``string`` (query) | Provide from event code as the value. For example - Success |
{{< tabs "uniqueid2" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:123e4567-e89b-12d3-a456-426614174000
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:smppUserSms
{{< / highlight >}}
{{< /tab >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
  "activityId": "accountCreation",
  "channel": "sms",
  "from": "CRM",
  "message": "test sms",
  "shortCode": "12345",
  "messageKey": "sms123",
  "notificationType": "User",
  "content": {
    "message": "",
    "from": "CRM",
    "data": {
      "userId": "10000190",
      "mobNumber": "99219703",
      "accountNumber": "10000190",
      "password": "uudkzkix",
      "expiryDate": "15-01-2021 11:23:00",
      "total": "456",
      "plan": "F&F Offer 60GB17.5K ACE",
      "email": "karthikeyantest003@yopmail.com",
      "msisdn": "234501000389",
      "segment": "Prepaid",
      "amount": "$5638",
      "voucherCode": "12ER4Y",
      "addOnName": "msisdn",
      "ticketNo": "987456",
      "tickekStatus": "active",
      "accountStatus": "active",
      "startDate": "15-10-2020 09:30:00",
      "updateDate": "05-12-2020 12:39:00"
    }
  },
  "msisdn": "234501000389",
  "shortMessage": "test sms",
  "shortCodeNumber": "12345",
  "recipients": [
    "venkatesh@yopmail.com"
  ],
  "templateType": "WELCOME",
  "EventName": "ProductMsisdnListUpdated",
  "EventCode": "Success"
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
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - smppBulkUserSms |
| **source** (mandatory) | ``string`` (header)      |    Provide the source as the value. |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

#### *Request Body Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| **activityId** (mandatory)    | ``string`` (query) | Provide the activity id as the value. For example - accountCreation |
| **channel** (mandatory)    | ``string`` (query) | Provide the channel of notification as the value. For example - SMS |
| **from** (mandatory)    | ``string`` (query) | Provide from whom the notification will be sent as the value. |
| **message** (mandatory)    | ``string`` (query) | Provide the message as the value. |
| **shortCode** (mandatory)    | ``string`` (query) | Provide the short code of the notification as the value. For example - 12345 |
| **messageKey** (mandatory)    | ``string`` (query) | Provide the message key of the notification as the value. For example - sms123 |
| **notificationType** (mandatory)    | ``string`` (query) | Provide the type of notification as the value. |
| {{< expand id="testing4" atext="content (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>message</td>
<td>string</td>
<td>Provide the message of the notification as the value.</td>
</tr>
<tr>
<td>from</td>
<td>string</td>
<td>Provide the from whom the notification will be sent as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing1" atext="data (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>userId</td>
<td>string</td>
<td>Provide the user id as the value.</td>
</tr>
<tr>
<td>mobNumber</td>
<td>string</td>
<td>Provide the mobile phone number as the value.</td>
</tr>
<tr>
<td>accountNumber</td>
<td>string</td>
<td>Provide the account number as the value.</td>
</tr>
<tr>
<td>password</td>
<td>string</td>
<td>Provide the password as the value.</td>
</tr>
<tr>
<td>expiryDate</td>
<td>string</td>
<td>Provide the expiry date as the value.</td>
</tr>
<tr>
<td>total</td>
<td>string</td>
<td>Provide the total notifications to be sent as the value.</td>
</tr>
<tr>
<td>plan</td>
<td>string</td>
<td>Provide the type of plan as the value. For example - F&F Offer 60GB17.5K ACE</td>
</tr>
<tr>
<td>email</td>
<td>string</td>
<td>Provide the email as the value.</td>
</tr>
<tr>
<td>msidn</td>
<td>string</td>
<td>Provide the msidn number as the value.</td>
</tr>
<tr>
<td>segment</td>
<td>string</td>
<td>Provide the segment as the value. For example - Prepaid</td>
</tr>
<tr>
<td>voucherCode</td>
<td>string</td>
<td>Provide the voucher code as the value.</td>
</tr>
<tr>
<td>addOnName</td>
<td>string</td>
<td>Provide the add on name as the value. For example - msidn</td>
</tr>
<tr>
<td>ticketNo</td>
<td>string</td>
<td>Provide the ticket number as the value.</td>
</tr>
<tr>
<td>ticketStatus</td>
<td>string</td>
<td>Provide the ticket status as the value.</td>
</tr>
<tr>
<td>accountStatus</td>
<td>string</td>
<td>Provide the account status as the value.</td>
</tr>
<tr>
<td>startDate</td>
<td>string</td>
<td>Provide the start date as the value.</td>
</tr>
<tr>
<td>updateDate</td>
<td>string</td>
<td>Provide the update date as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| **misisdn** (mandatory)    | ``string`` (query) | Provide the msisdn number as the value. For example - 123456789 |
| **shortMessage** (mandatory)    | ``string`` (query) | Provide the short message as the value. |
| **shortCodeNumber** (mandatory)    | ``string`` (query) | Provide from short code number as the value. For example - 12345 |
| {{< expand id="testing5" atext="recipients (array)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>email</td>
<td>string</td>
<td>Provide the email address of the recipient as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| **templateType** (mandatory)    | ``string`` (query) | Provide the type of template as the value. For example - WELCOME |
| **EventName** (mandatory)    | ``string`` (query) | Provide the name of the event as the value. For example - ProductUpdate |
| **EventCode** (mandatory)    | ``string`` (query) | Provide from event code as the value. For example - Success |
{{< tabs "uniqueid3" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:123e4567-e89b-12d3-a456-426614174000
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:smppBulkUserSms
{{< / highlight >}}
{{< /tab >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
  "activityId": "accountCreation",
  "channel": "sms",
  "from": "CRM",
  "message": "test sms",
  "shortCode": "12345",
  "messageKey": "sms123",
  "notificationType": "User",
  "content": {
    "message": "",
    "from": "CRM",
    "data": {
      "userId": "10000190",
      "mobNumber": "99219703",
      "accountNumber": "10000190",
      "password": "uudkzkix",
      "expiryDate": "15-01-2021 11:23:00",
      "total": "123",
      "plan": "F&F Offer 60GB17.5K ACE",
      "email": "karthikeyantest003@yopmail.com",
      "msisdn": "234501000389",
      "segment": "Prepaid",
      "amount": "$2658",
      "voucherCode": "12ER4Y",
      "addOnName": "msisdn",
      "ticketNo": "987456",
      "tickekStatus": "active",
      "accountStatus": "active",
      "startDate": "15-10-2020 09:30:00",
      "updateDate": "05-12-2020 12:39:00"
    }
  },
  "msisdn": "234501000389",
  "shortMessage": "test sms",
  "shortCodeNumber": "12345",
  "recipients": [
    "venkatesh@yopmail.com"
  ],
  "templateType": "WELCOME",
  "EventName": "ProductMsisdnListUpdated",
  "EventCode": "Success"
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

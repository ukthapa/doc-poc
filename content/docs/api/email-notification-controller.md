---
title: "Email Notification Controller"
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
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **requestorChannel** (mandatory) | ``string`` (header)      |    Provide the requestorChannel. |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **serviceProvider** (mandatory) | ``string`` (header)      |    Provide the name of the service provider. |

#### *Request Body Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| {{< expand id="testing1" atext="header (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>correlationIdrelation</td>
<td>string</td>
<td>Provide the correlation id as the value. For example - S0643</td>
</tr>
<tr>
<td>operation</td>
<td>string</td>
<td>Provide the operation as the value. For example - notification</td>
</tr>
<tr>
<td>requestorChannel</td>
<td>string</td>
<td>Provide the requestor channel as the value. For example - CRM</td>
</tr>
<tr>
<td>srDate</td>
<td>string</td>
<td>Provide the srDate as the value.</td>
</tr>
<tr>
<td>serviceProvider</td>
<td>string</td>
<td>Provide the service provider name as the value. For example - MOM</td>
</tr>
<tr>
<td>backEndChannel</td>
<td>string</td>
<td>Provide the back end channel as the value. For example - MOM</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing10" atext="message (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>activityId</td>
<td>string</td>
<td>Provide the activity id as the value. For example - accountCreation</td>
</tr>
<tr>
<td>channel</td>
<td>string</td>
<td>Provide the channel as the value.</td>
</tr>
<tr>
<td>notificationType</td>
<td>string</td>
<td>Provide the type of notification as the value. For example - SMS</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing2" atext="content (object)">}}
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
<td>Provide the notification message as the value.</td>
</tr>
<tr>
<td>from</td>
<td>string</td>
<td>Provide from where the notification is sent as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing3" atext="data (object)">}}
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
<td>LastName</td>
<td>string</td>
<td>Provide the last name as the value.</td>
</tr>
<tr>
<td>email</td>
<td>string</td>
<td>Provide the email address as the value.</td>
</tr>
<tr>
<td>cc</td>
<td>string</td>
<td>Provide the email address to whom the email will be copied as the value.</td>
</tr>
<tr>
<td>bcc</td>
<td>string</td>
<td>Provide the email address to whom the email will be sent as bcc.</td>
</tr>
<tr>
<td>salutation</td>
<td>string</td>
<td>Provide the salutation as the value. For example - Mr.</td>
</tr>
<tr>
<td>middleName</td>
<td>string</td>
<td>Provide the middle name as the value.</td>
</tr>
<tr>
<td>accountNumber</td>
<td>string</td>
<td>Provide the account number as the value.</td>
</tr>
<tr>
<td>MobNumber</td>
<td>string</td>
<td>Provide the mobile phone number as the value.</td>
</tr>
<tr>
<td>imsi</td>
<td>string</td>
<td>Provide the imsi number as the value. For example - Mb234</td>
</tr>
<tr>
<td>imei</td>
<td>string</td>
<td>Provide imei as the value. For example - S81233SSN</td>
</tr>
<tr>
<td>plan</td>
<td>string</td>
<td>Provide the plan as the value. For example - monthly plan</td>
</tr>
<tr>
<td>userId</td>
<td>string</td>
<td>Provide the user id as the value.</td>
</tr>
<tr>
<td>password</td>
<td>string</td>
<td>Provide the password as the value.</td>
</tr>
<tr>
<td>createDate</td>
<td>string</td>
<td>Provide the create date as the value.</td>
</tr>
<tr>
<td>paymentMethod</td>
<td>string</td>
<td>Provide the payment method as the value.</td>
</tr>
<tr>
<td>paymentReceiver</td>
<td>string</td>
<td>Provide the payment receiver name as the value.</td>
</tr>
<tr>
<td>total</td>
<td>string</td>
<td>Provide the total amount as the value.</td>
</tr>
<tr>
<td>balance</td>
<td>string</td>
<td>Provide the balance as the value.</td>
</tr>
<tr>
<td>treceipt</td>
<td>string</td>
<td>Provide the treceipt number as the value.</td>
</tr>
<tr>
<td>userExpiryDate</td>
<td>string</td>
<td>Provide the user expiry date as the value.</td>
</tr>
<tr>
<td>autoRegAccountName</td>
<td>string</td>
<td>Provide the auto registered account name as the value.</td>
</tr>
<tr>
<td>userPaymentBalancebalance</td>
<td>string</td>
<td>Provide the user payment balance as the value.</td>
</tr>
<tr>
<td>billIndex</td>
<td>string</td>
<td>Provide the bill index number as the value.</td>
</tr>
<tr>
<td>invoiceNumber</td>
<td>string</td>
<td>Provide the invoice number as the value.</td>
</tr>
<tr>
<td>partenrId</td>
<td>string</td>
<td>Provide the partner ID as the value. For example - PTR_NTR</td>
</tr>
<tr>
<td>environment</td>
<td>string</td>
<td>Provide the environment as the value. For example - Dev</td>
</tr>
<tr>
<td>comment</td>
<td>string</td>
<td>Provide the comment if any as the value.</td>
</tr>
<tr>
<td>suppportEmail</td>
<td>string</td>
<td>Provide the support email id as the value.</td>
</tr>
<tr>
<td>partnerContactNumber</td>
<td>string</td>
<td>Provide the contact number of the partner as the value.</td>
</tr>
<tr>
<td>partnerEmailId</td>
<td>string</td>
<td>Provide the email id of the partner as the value.</td>
</tr>
<tr>
<td>partnerStatus</td>
<td>string</td>
<td>Provide the status of the partner as the value.</td>
</tr>
<tr>
<td>loginUrl</td>
<td>string</td>
<td>Provide the login URL as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing4" atext="attachments (array)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>fileName</td>
<td>string</td>
<td>Provide the file name as the value.</td>
</tr>
<tr>
<td>filePath</td>
<td>string</td>
<td>Provide the file path as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing8" atext="recipients (array)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>to</td>
<td>string</td>
<td>Provide the email address to whom the notification will be sent as the value.</td>
</tr>
<tr>
<td>name</td>
<td>string</td>
<td>Provide the name of the customer as the value.</td>
</tr>
<tr>
<td>cc</td>
<td>string</td>
<td>Provide the email address of the customer to whom the email will copied as the value.</td>
</tr>
<tr>
<td>bcc</td>
<td>string</td>
<td>Provide the email address of the customer to whom the email will sent as bcc.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| **templateType** (mandatory) | ``string``       |    Provide the template type as the value. For example - WELCOME |
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
        "correlationId": "SO643"
        "operation": "notification",
        "requestorChannel": "CRM",
        "srDate": "2020-06-02T15:01:00Z",
        "serviceProvider": "MOM",
		"backendChannel": "MOM"    
  },
  "message": {
    "activityId": "accountCreation",
    "channel": "string",
    "notificationType": "SMS",
    "content": {
      "message": "Account creation",
      "from": "CRM",
      "data": {
        "firstName": "Shanthamma",
        "lastName": "shivanna",
        "email": "shanti@gmail.com",
        "cc": "kiran@gmail.com",
        "bcc": "supritha@gmail.com",
        "salutation": "ms",
        "middleName": "Kavitha",
        "accountNumber": "10000190",
        "mobNumber": "8710890667",
        "imsi": "Mb234",
        "imei": "S81233",
        "plan": "monthlyPlan",
        "userId": "1234S",
        "password": "rt#67",
        "createDate": "15-01-2021 11:23:00",
        "paymentMethod": "PhonePay",
        "paymentReceiver": "Shanthi",
        "total": "100",
        "balance": "24",
        "treceipt": "165",
        "userExpiryDate": "19-01-2022 11:23:00",
        "autoRegAccountName": "Shanthamma",
        "userPaymentBalance": "67",
        "billIndex": "000025",
        "invoiceNumber": "5678",
        "partnerId": "PTR_NTR",
        "environment": "Dev",
        "comment": "",
        "supportEmail": "suuport@xyz.com",
        "partnerContactNumber": "8734567503",
        "partnerEmail": "shanti@gmail.com",
        "partnerStatus": "Approved",
        "loginUrl": "http://localhost:8080/csmart-crmservices/crm/v1/login"
      },
      "attachments": [
        {
          "fileName": "details.docx",
          "filePath": "C:/Users/Documents"
        }
      ]
    },
    "recipients": [
      {
        "to": "rohan@gmail.com",
        "name": "Rohan",
        "cc": [
          "sunil@gmail.com"
        ],
        "bcc": [
          "kavitha@gmail.com"
        ]
      }
    ],
    "templateType": "WELCOME"
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

This service is used to send simple email to the partner. It requires EmailResult object as request body. If successful the system will send the email to the partner.

<section>

#### *Request Body Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| {{< expand id="testing6" atext="header (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>correlationIdrelation</td>
<td>string</td>
<td>Provide the correlation id as the value. For example - S0643</td>
</tr>
<tr>
<td>operation</td>
<td>string</td>
<td>Provide the operation as the value. For example - notification</td>
</tr>
<tr>
<td>requestorChannel</td>
<td>string</td>
<td>Provide the requestor channel as the value. For example - CRM</td>
</tr>
<tr>
<td>srDate</td>
<td>string</td>
<td>Provide the srDate as the value.</td>
</tr>
<tr>
<td>serviceProvider</td>
<td>string</td>
<td>Provide the service provider name as the value. For example - MOM</td>
</tr>
<tr>
<td>backEndChannel</td>
<td>string</td>
<td>Provide the back end channel as the value. For example - MOM</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing7" atext="message (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>activityId</td>
<td>string</td>
<td>Provide the activity id as the value. For example - accountCreation</td>
</tr>
<tr>
<td>channel</td>
<td>string</td>
<td>Provide the channel as the value.</td>
</tr>
<tr>
<td>notificationType</td>
<td>string</td>
<td>Provide the type of notification as the value. For example - SMS</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing11" atext="content (object)">}}
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
<td>Provide the notification message as the value.</td>
</tr>
<tr>
<td>from</td>
<td>string</td>
<td>Provide from where the notification is sent as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing9" atext="data (object)">}}
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
<td>LastName</td>
<td>string</td>
<td>Provide the last name as the value.</td>
</tr>
<tr>
<td>email</td>
<td>string</td>
<td>Provide the email address as the value.</td>
</tr>
<tr>
<td>cc</td>
<td>string</td>
<td>Provide the email address to whom the email will be copied as the value.</td>
</tr>
<tr>
<td>bcc</td>
<td>string</td>
<td>Provide the email address to whom the email will be sent as bcc.</td>
</tr>
<tr>
<td>salutation</td>
<td>string</td>
<td>Provide the salutation as the value. For example - Mr.</td>
</tr>
<tr>
<td>middleName</td>
<td>string</td>
<td>Provide the middle name as the value.</td>
</tr>
<tr>
<td>accountNumber</td>
<td>string</td>
<td>Provide the account number as the value.</td>
</tr>
<tr>
<td>MobNumber</td>
<td>string</td>
<td>Provide the mobile phone number as the value.</td>
</tr>
<tr>
<td>imsi</td>
<td>string</td>
<td>Provide the imsi number as the value. For example - Mb234</td>
</tr>
<tr>
<td>imei</td>
<td>string</td>
<td>Provide imei as the value. For example - S81233SSN</td>
</tr>
<tr>
<td>plan</td>
<td>string</td>
<td>Provide the plan as the value. For example - monthly plan</td>
</tr>
<tr>
<td>userId</td>
<td>string</td>
<td>Provide the user id as the value.</td>
</tr>
<tr>
<td>password</td>
<td>string</td>
<td>Provide the password as the value.</td>
</tr>
<tr>
<td>createDate</td>
<td>string</td>
<td>Provide the create date as the value.</td>
</tr>
<tr>
<td>paymentMethod</td>
<td>string</td>
<td>Provide the payment method as the value.</td>
</tr>
<tr>
<td>paymentReceiver</td>
<td>string</td>
<td>Provide the payment receiver name as the value.</td>
</tr>
<tr>
<td>total</td>
<td>string</td>
<td>Provide the total amount as the value.</td>
</tr>
<tr>
<td>balance</td>
<td>string</td>
<td>Provide the balance as the value.</td>
</tr>
<tr>
<td>treceipt</td>
<td>string</td>
<td>Provide the treceipt number as the value.</td>
</tr>
<tr>
<td>userExpiryDate</td>
<td>string</td>
<td>Provide the user expiry date as the value.</td>
</tr>
<tr>
<td>autoRegAccountName</td>
<td>string</td>
<td>Provide the auto registered account name as the value.</td>
</tr>
<tr>
<td>userPaymentBalancebalance</td>
<td>string</td>
<td>Provide the user payment balance as the value.</td>
</tr>
<tr>
<td>billIndex</td>
<td>string</td>
<td>Provide the bill index number as the value.</td>
</tr>
<tr>
<td>invoiceNumber</td>
<td>string</td>
<td>Provide the invoice number as the value.</td>
</tr>
<tr>
<td>partenrId</td>
<td>string</td>
<td>Provide the partner ID as the value. For example - PTR_NTR</td>
</tr>
<tr>
<td>environment</td>
<td>string</td>
<td>Provide the environment as the value. For example - Dev</td>
</tr>
<tr>
<td>comment</td>
<td>string</td>
<td>Provide the comment if any as the value.</td>
</tr>
<tr>
<td>suppportEmail</td>
<td>string</td>
<td>Provide the support email id as the value.</td>
</tr>
<tr>
<td>partnerContactNumber</td>
<td>string</td>
<td>Provide the contact number of the partner as the value.</td>
</tr>
<tr>
<td>partnerEmailId</td>
<td>string</td>
<td>Provide the email id of the partner as the value.</td>
</tr>
<tr>
<td>partnerStatus</td>
<td>string</td>
<td>Provide the status of the partner as the value.</td>
</tr>
<tr>
<td>loginUrl</td>
<td>string</td>
<td>Provide the login URL as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
{{< tabs "uniqueid3" >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
  "header": {
     "correlationId": "SO643"
        "operation": "notification",
        "requestorChannel": "CRM",
        "srDate": "2020-06-02T15:01:00Z",
        "serviceProvider": "MOM",
		"backendChannel": "MOM"
  },
  "message": {
    "subject": "Account Creation",
    "templateType": "WELCOME",
    "data": {
      "firstName": "Shanthi",
        "lastName": "shivanna",
        "email": "shanti@gmail.com",
        "cc": "kiran@gmail.com",
        "bcc": "supritha@gmail.com",
        "salutation": "ms",
        "middleName": "Kavitha",
        "accountNumber": "10000190",
        "mobNumber": "8710890443",
        "imsi": "Mb234",
        "imei": "S81233",
        "plan": "monthlyPlan",
        "userId": "1234S",
        "password": "rt#67",
        "createDate": "15-01-2021 11:23:00",
        "paymentMethod": "PhonePay",
        "paymentReceiver": "Sunil",
        "total": "100",
        "balance": "24",
        "treceipt": "165",
        "userExpiryDate": "19-01-2022 11:23:00",
        "autoRegAccountName": "Shanthamma",
        "userPaymentBalance": "67",
        "billIndex": "000025",
        "invoiceNumber": "5678",
        "partnerId": "PTR_NTR",
        "environment": "Dev",
        "comment": "",
        "supportEmail": "suuport@gmail.com",
        "partnerContactNumber": "8734567503",
        "partnerEmail": "ptr@gamil.com",
        "partnerStatus": "Approved",
        "loginUrl": "http://192.168.1.71:8080/csmart-crmservices/crm/v1/login"
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

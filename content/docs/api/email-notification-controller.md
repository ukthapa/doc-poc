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

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **EmailResult** (mandatory)    | ``string`` (body)      |   Provide the result of the email as the value. |

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

---
title: "Authentication Services"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "CRM"
weight: 201
toc: false
---

## GET </crm/v1/auth/email>
<section>

This service allows you to verify the customer's email ID. It requires input parameters like, email, correlationId, source, srdate, operation and destination. On successful verification the system will validate the email ID while signing up already exists in the system or not. If not the appropriate error code will be returned.

### Request Parameters
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| -----:|
| email     | string (header) | Provide the customer's email ID as the value. For example - adarsha_cds1@yopmail.com |
| correlationId     | string (header)      |   Provide the correlationId as the value. For example - SO-100 |
| Source | string (header)      |    Provide the source as the value. For example - Selfcare |
| srdate | string (header)      |    Provide the date as the value. For example - 11-09-2021 |
| Operation | string (header)      |    Provide the operation as the value. For example - emailExists |
| destination | string (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:SO-100
email:adarsha_cds1@yopmail.com
operation:emailExists
destination:CRM
source:Selfcare
srDate:11-09-2021

{{< / highlight >}}
{{< /tab >}}
{{< tab "Error" >}}
{{< highlight java "linenos=table" >}}
### Downstream error
{
  "response": {
    "success": "false",
    "result": {
      "arguments": {
        "statusCode": "500",
        "errorCode": "Downstream error",
        "errorMessage": "Not Able to connect with CRM."
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

## POST </crm/v1/auth/otp>
<section>

This service is a validation service used when the customer wants to create a new password or has forgotten the password. It verifies the OTP to received for password generation.

This service requires correlationId, source, srdate, operation and destination along with the email ID, OTP and encrypted data in the API body. If the valid OTP is provided by the customer it will verify and allow to proceed with password creation successfully. If the OTP provided is wrong the appropriate error code will be returned.

### Request Parameters
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| -----:|
| correlationId     | string (header)      |   Provide the correlationId as the value. For example - SO-100 |
| Source | string (header)      |    Provide the source as the value. For example - Selfcare |
| srdate | string (header)      |    Provide the date as the value. For example - 11-09-2021 |
| Operation | string (header)      |    Provide the operation as the value. For example - emailExists |
| destination | string (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid" >}}
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
    "email":"adarsha_cds3@yopmail.com",
    "encryptedOtp":"e1aa84d4a0a00d21f960b8938a23cb890e35609b080174b74753839587cbce42",
    "otp" : "115695"
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

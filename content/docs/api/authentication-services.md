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

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /crm/v1/auth/email
{{% /method-block %}}

This service allows you to verify the customer's email ID. It requires input parameters like, email, correlationId, source, srdate, operation and destination. On successful verification the system will validate the email ID while signing up already exists in the system or not. If not the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **email** (mandatory)    | ``string`` (header) | Provide the customer's email ID as the value. For example - adarsha_cds1@yopmail.com |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

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
{{< tab "Success Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "response": "Email already exists."
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

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
  /crm/v1/auth/otp
{{% /method-block %}}

This service is a validation service used when the customer wants to create a new password or has forgotten the password. It verifies the OTP to received for password generation.

This service requires correlationId, source, srdate, operation and destination along with the email ID, OTP and encrypted data in the API body. If the valid OTP is provided by the customer it will verify and allow to proceed with password creation successfully. If the OTP provided is wrong the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (body)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (body)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (body)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (body)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (body)      |    Provide the destination as the value. |

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
    "email":"adarsha_cds3@yopmail.com",
    "encryptedOtp":"e1aa84d4a0a00d21f960b8938a23cb890e35609b080174b74753839587cbce42",
    "otp" : "115695"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Success Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "message": "successfully verified OTP"
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
{{< /tabs >}}
</section>

---
title: "Customer Engagement Services"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "CRM"
weight: 202
toc: false
---

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
  /crm/v1/login
{{% /method-block %}}

This service is an authentication service for the user to login to the application.

It requires correlationid, srdate, source, operation and destination as input parameters along with email, password and source in the API body to allow the customer to login into the system. If incorrect credentials are provided the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |
| **type** (mandatory) | ``string`` (header)      |    Provide the type of OTP. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (body)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (body)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (body)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (body)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (body)      |    Provide the destination as the value. |
| **type** (mandatory) | ``string`` (body)      |    Provide the type of OTP. |

{{< tabs "uniqueid1" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:SO-101
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:verifyOTP
type:numbers
{{< / highlight >}}
{{< /tab >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
  "email": "string",
  "password": "string",
  "source": "Selfcare",
  "fireBaseMessagingToken": "string",
  "deviceId": "string"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "success": "true",
      "accessToken": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJ2ZW5rYXRlc2hAeW9wbWFpbC5jb20iLCJqdGkiOiJzYW50aG9zaCIsImlhdCI6MTU4Njc3MDg5MiwiZXhwIjoxNTg5MzQzMDkyfQ.jzLUoZP5HWkk6bxvohFhUYSpEETpTSJyUTA109ekuMw",
      "response": "User logged in correctly",
      "firstName": "Ravi",
      "lastName": "emos",
      "segment": "Individual",
      "platform": "Postpaid",
      "accountNumber": "ACC10533",
      "email": "venkatesh@yopmail.com",
      "mobile": "918 290 9949",
      "contactId": "11937",
      "pushNotifications": false,
      "doNotDisturb": false,
      "roaming": false,
      "accountId": "11936",
      "profileImage": "http://crm.covalensedigital.net:1212/storage/2020/February/week4/96140_download.png"
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
        "errorCode": "BAD_REQUEST",
        "errorMessage": "Invalid username/password"
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
  /crm/v1/signup
{{% /method-block %}}

This service is a registration service which enables to onboard the customer.

It requires correlationId, srdate, source, operation and destination along with the customer's details required to create the account in the API body. If successful the customers will be on boarded. If failed the appropriate error code will be returned.

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
| **correlationId** (mandatory)    | ``string`` (body)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (body)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (body)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (body)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (body)      |    Provide the destination as the value. |

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
  "acctInfo": {
    "title": "string",
    "firstName": "string",
    "middleName": "string",
    "lastName": "string",
    "phone": "string",
    "mobilePhone": "string",
    "gender": "string",
    "companyName": "string",
    "department": "string",
    "designation": "string",
    "emailAddress": "string",
    "docIdNumberMsgId": "string",
    "docIdTypeEquipType": "string",
    "accountId": "string",
    "assignedUserId": "string",
    "platform": "string",
    "Type": "string",
    "ServiceType": "string"
  },
  "addressInfo": {
    "streetAddress": "string",
    "city": "string",
    "postalCode": "string",
    "state": "string",
    "country": "string"
  },
  "paymentDetail": {
    "gateway": "string",
    "firstName": "string",
    "lastName": "string",
    "email": "string",
    "cardNo": "string",
    "expiryMonth": "string",
    "expiryYear": "string",
    "cvv": "string"
  },
  "lineItems": [
    {
      "packageId": "string",
      "productGroupId": "string",
      "productId": "string",
      "price": "string",
      "qty": "string",
      "isInventory": "string",
      "inventoryAttributes": {
        "msisdn": "string",
        "icicid": "string",
        "imsi": "string",
        "sim": "string"
      }
    }
  ],
  "paymentInfo": {
    "amount": "string",
    "description": "string",
    "reasonCode": "string",
    "paymentType": "string",
    "transId": "string",
    "effectiveT": "string"
  },
  "orderType": "string",
  "orderId": "string",
  "password": "string",
  "element1": "string",
  "element2": "string",
  "element3": "string",
  "element4": "string"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "salesOrder": {
        "salesorder_no": "SO2542"
      }
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
        "errorCode": "BAD_REQUEST",
        "errorMessage": "Attribute 'Platform' not found in request."
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

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
  /crm/v1/signup/kyc
{{% /method-block %}}

This service is a registration service which enables to on-board the customer.

It requires correlationId, srdate, source, operation and destination along with the customer's details required to create account in the API body. If successful the customers will be on-boarded. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **Data** (mandatory)    | ``string`` (header)      |   Provide the registration data of the customer. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |
| **type** (mandatory) | ``string`` (header)      |    Provide the type of OTP. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **Data** (mandatory)    | ``string`` (body)      |   Provide the registration data of the customer. |
| **correlationId** (mandatory)    | ``string`` (body)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (body)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (body)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (body)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (body)      |    Provide the destination as the value. |
| **type** (mandatory) | ``string`` (header)      |    Provide the type of OTP. |

{{< tabs "uniqueid4" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
Data:string
correlationId:SO-101
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:verifyOTP
type:numbers
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "salesOrder": {
        "salesorder_no": "SO2542"
      }
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
        "errorCode": "BAD_REQUEST",
        "errorMessage": "Attribute 'Platform' not found in request."
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

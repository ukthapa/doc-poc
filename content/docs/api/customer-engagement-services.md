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
| **email** (mandatory)    | ``string`` (body)      |   Provide the email Id as the value. For example - ag_cds_p@yopmail.com |
| **Source** (mandatory) | ``string`` (body)      |    Provide the source as the value. For example - app |
| **password** (mandatory) | ``string`` (body)      |    Provide the password as the value. For example - ag |

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
    "email": "ag_cds_p@yopmail.com",
    "password": "ag",
    "source": "app"
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

#### *Request Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| **orderID** (mandatory)    | ``string`` (query) | Provide the order ID as the value. For example - Portal-5445 |
| **orderType** (mandatory)    | ``string`` (query) | Provide the type of order as the value. For example - New |
| {{< expand id="testing1" atext="AcctInfo (object)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>ComnpanyName</td>
<td>string</td>
<td>Provide the company name as the value.</td>
</tr>
<tr>
<td>FirstName</td>
<td>string</td>
<td>Provide the first name as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| **units** (optional) | ``string`` (query)      |    Provide the units as the value. |
| {{< expand id="testing2" atext="Someother">}}
<table><thead><tr><th>s2122dsa</th><th>2312213</th><th>2323121</th></tr></thead><tbody><tr><td>sadasdsa</td><td>sadssd</td><td>sasaddsa</td></tr></tbody></table>
{{< /expand >}} |

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
  "OrderId": "Portal-5445",
  "OrderType": "NEW",
  "AcctInfo": {
    "CompanyName": "companyName",
    "FirstName": "FirstName",
    "LastName": "LastName",
    "MiddleName": "",
    "MobilePhone": "19216811479862",
    "Phone": "",
    "DocIdTypeEquipType": "SSN",
    "Title": "Mr.",
    "Department": "",
    "Designation": "",
    "DocIdNumberMsgId": "878-78-7878",
    "Gender": "Male",
    "EmailAddress": "adarsha_cds8@yopmail.com",
    "Platform": "Postpaid",
    "Type": "Residential",
    "ServiceType": "VoLTE"
  },
  "AddressInfo": {
    "City": "Bengaluru",
    "Country": "India",
    "PostalCode": "560034",
    "State": "Karnataka",
    "StreetAddress": "Jakkasandra, Teacher's Colony, 1st Block Koramangala, Koramangala, Bengaluru, Bangalore Urban, Karnataka, India"
  },
  "PackageListId": "653113",
  "LineItems": [
    {
      "packageId": "685782",
      "productGroupId": "685770",
      "productId": "650390",
      "price": "10",
      "qty": "1",
      "isInventory": "1",
      "inventoryAttributes": {
        "SIM": "116402905"
      }
    },
    {
      "packageId": "685782",
      "productGroupId": "685770",
      "productId": "650994",
      "price": "0",
      "qty": "1",
      "isInventory": "0"
    },
    {
      "packageId": "685782",
      "productGroupId": "685770",
      "productId": "650996",
      "price": "0",
      "qty": "1",
      "isInventory": "0"
    },
    {
      "packageId": "685782",
      "productGroupId": "685770",
      "productId": "650998",
      "price": "0",
      "qty": "1",
      "isInventory": "0"
    },
    {
      "packageId": "685782",
      "productGroupId": "685770",
      "productId": "650999",
      "price": "100",
      "qty": "1",
      "isInventory": "0"
    },
    {
      "packageId": "685782",
      "productGroupId": "685770",
      "productId": "651000",
      "price": "0",
      "qty": "1",
      "isInventory": "0"
    },
    {
      "packageId": "685782",
      "productGroupId": "685770",
      "productId": "651001",
      "price": "0",
      "qty": "1",
      "isInventory": "0"
    },
    {
      "packageId": "685782",
      "productGroupId": "685770",
      "productId": "651003",
      "price": "0",
      "qty": "1",
      "isInventory": "0"
    },
    {
      "packageId": "685782",
      "productGroupId": "651494",
      "productId": "651494",
      "price": "0",
      "qty": "1",
      "isInventory": "0"
    },
    {
      "packageId": "685782",
      "productGroupId": "651495",
      "productId": "651495",
      "price": "0",
      "qty": "1",
      "isInventory": "0"
    },
    {
      "packageId": "685782",
      "productGroupId": "651496",
      "productId": "651496",
      "price": "0",
      "qty": "1",
      "isInventory": "0"
    }
  ],
  "Password": "ag"
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
| **Data** (mandatory)    | ``string`` (query)      |   Provide the registration data of the customer. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |
| **type** (mandatory) | ``string`` (header)      |    Provide the type of OTP. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **Data** (mandatory)    | ``string`` (query)      |   Provide the registration data of the customer. |
| **correlationId** (mandatory)    | ``string`` (body)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (body)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (body)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (body)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (body)      |    Provide the destination as the value. |
| **type** (mandatory) | ``string`` (header)      |    Provide the type of OTP. |

{{< tabs "uniqueid4" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
Data:query
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

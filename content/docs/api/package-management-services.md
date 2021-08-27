---
title: "Packages Management Services"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "CRM"
weight: 204
toc: false
---

{{% method-block bgcolor="primary" type="bg-blue" callmethod="GET" %}}
  /crm/v1/package/{location}
{{% /method-block %}}

This service is used to fetch the packages based on the location of the package.

It requires location, correlationid, source, srdate, operation and destination as input parameters. If successful the list of the package available in the particular location provided will be fetched. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **location** (mandatory)    | ``string`` (path)      |   Provide the location of the package as the value. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - getPackageDetails |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |
| **param** (mandatory)    | ``object`` (query)      |   Provide the parameter as the value. Available values are, **platform** and **packagetype**. For example - "additionalProp1": "platform" |

{{< tabs "uniqueid1" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
location:path
correlationId:123e4567-e89b-12d3-a456-426614174000
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:getPackageDetails
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": [
      {
        "packageid": "7573",
        "name": "GSM Connection",
        "products": [
          {
            "id": "7567",
            "name": "Voice_Recurring",
            "description": "Voice_Recurring -                          Synced from BRM",
            "price": "6.00",
            "mandatory": "no",
            "platform": "",
            "servicetype": "VOICE",
            "serviceCode": "/service/telco/gsm/telephony",
            "productType": "Root Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/November/week4/91345_22401_bolton-2.png",
            "reviewRating": "",
            "reviewCount": "0"
          },
          {
            "id": "7571",
            "name": "Data Recurring",
            "description": "Data_Recurring - Synced from BRM",
            "price": "5.00",
            "mandatory": "no",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gsm/data",
            "productType": "Service",
            "productImage": "",
            "reviewRating": "",
            "reviewCount": "0"
          },
          {
            "id": "82287",
            "name": "Data 5GB",
            "description": "Data 5GB",
            "price": "5.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gprs/data",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82291_22404_bolton-1.png",
            "reviewRating": "4",
            "reviewCount": "5"
          },
          {
            "id": "82288",
            "name": "Data 10GB",
            "description": "Data 10GB",
            "price": "10.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gprs/data",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82292_22400_bolton-1.png",
            "reviewRating": "5",
            "reviewCount": "1"
          },
          {
            "id": "82289",
            "name": "Data 20GB",
            "description": "Data 20GB",
            "price": "20.00",
            "mandatory": "no",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gprs/data",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82293_22403_bolton-1.png",
            "reviewRating": "",
            "reviewCount": "0"
          },
          {
            "id": "82290",
            "name": "Data 1GB",
            "description": "Data 1GB",
            "price": "2.00",
            "mandatory": "no",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gprs/data",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82294_22403_bolton-1.png",
            "reviewRating": "5",
            "reviewCount": "2"
          },
          {
            "id": "7569",
            "name": "SMS_Recurring",
            "description": "SMS_Recurring.",
            "price": "5.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "GSM",
            "serviceCode": "/service/telco/gsm/sms",
            "productType": "Product",
            "productImage": "",
            "reviewRating": "",
            "reviewCount": "0"
          },
          {
            "id": "7568",
            "name": "Voice_Usage",
            "description": "Voice_Usage",
            "price": "0.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "VOICE",
            "serviceCode": "/service/telco/gsm/telephony",
            "productType": "Root Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82245_22401_bolton-2.png",
            "reviewRating": "4.5",
            "reviewCount": "2"
          },
          {
            "id": "7572",
            "name": "Data_Usage",
            "description": "Data_Usage",
            "price": "0.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gprs/data",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82243_22445_bolton-1.png",
            "reviewRating": "",
            "reviewCount": "0"
          },
          {
            "id": "8268",
            "name": "SMS_Usage",
            "description": "SMS_Usage",
            "price": "0.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "SMS",
            "serviceCode": "/service/telco/gsm/sms",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82244_22444_bolton-3.png",
            "reviewRating": "5",
            "reviewCount": "1"
          }
        ],
        "description": "",
        "platform": "Postpaid"
      },
      {
        "packageid": "12122",
        "name": "GSM Connection Premium",
        "products": [
          {
            "id": "7567",
            "name": "Voice_Recurring",
            "description": "Voice_Recurring                          - Synced from BRM",
            "price": "6.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "VOICE",
            "serviceCode": "/service/telco/gsm/telephony",
            "productType": "Root Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/November/week4/91345_22401_bolton-2.png",
            "reviewRating": "",
            "reviewCount": "0"
          },
          {
            "id": "82287",
            "name": "Data 5GB",
            "description": "Data 5GB",
            "price": "5.00",
            "mandatory": "no",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gprs/data",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82291_22404_bolton-1.png",
            "reviewRating": "4",
            "reviewCount": "5"
          },
          {
            "id": "82288",
            "name": "Data 10GB",
            "description": "Data 10GB",
            "price": "10.00",
            "mandatory": "no",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gprs/data",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82292_22400_bolton-1.png",
            "reviewRating": "5",
            "reviewCount": "1"
          },
          {
            "id": "82289",
            "name": "Data 20GB",
            "description": "Data 20GB",
            "price": "20.00",
            "mandatory": "no",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gprs/data",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82293_22403_bolton-1.png",
            "reviewRating": "",
            "reviewCount": "0"
          },
          {
            "id": "82290",
            "name": "Data 1GB",
            "description": "Data 1GB",
            "price": "2.00",
            "mandatory": "no",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gprs/data",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82294_22403_bolton-1.png",
            "reviewRating": "5",
            "reviewCount": "2"
          },
          {
            "id": "7568",
            "name": "Voice_Usage",
            "description": "Voice_Usage",
            "price": "0.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "VOICE",
            "serviceCode": "/service/telco/gsm/telephony",
            "productType": "Root Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82245_22401_bolton-2.png",
            "reviewRating": "4.5",
            "reviewCount": "2"
          },
          {
            "id": "7569",
            "name": "SMS_Recurring",
            "description": "SMS_Recurring.",
            "price": "5.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "GSM",
            "serviceCode": "/service/telco/gsm/sms",
            "productType": "Product",
            "productImage": "",
            "reviewRating": "",
            "reviewCount": "0"
          },
          {
            "id": "7571",
            "name": "Data Recurring",
            "description": "Data_Recurring - Synced from BRM",
            "price": "5.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gsm/data",
            "productType": "Service",
            "productImage": "",
            "reviewRating": "",
            "reviewCount": "0"
          },
          {
            "id": "8268",
            "name": "SMS_Usage",
            "description": "SMS_Usage",
            "price": "0.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "SMS",
            "serviceCode": "/service/telco/gsm/sms",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82244_22444_bolton-3.png",
            "reviewRating": "5",
            "reviewCount": "1"
          },
          {
            "id": "7572",
            "name": "Data_Usage",
            "description": "Data_Usage",
            "price": "0.00",
            "mandatory": "yes",
            "platform": "",
            "servicetype": "DATA",
            "serviceCode": "/service/telco/gprs/data",
            "productType": "Product",
            "productImage": "http://crm.covalensedigital.net:1212/storage/2019/September/week2/82243_22445_bolton-1.png",
            "reviewRating": "",
            "reviewCount": "0"
          }
        ],
        "description": "",
        "platform": "Postpaid"
      }
    ]
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

{{% method-block bgcolor="primary" type="bg-blue" callmethod="GET" %}}
​/crm​/v1​/package
{{% /method-block %}}

This service is used to fetch the details of all the packages available in the system.

It requires correlationid, token, srDate, operation, destination and source as input parameters. If successful the complete list of package details available in the system will be fetched. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - getSubscribedPackageDetails |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid2" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:123e4567-e89b-12d3-a456-426614174000
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:getSubscribedPackageDetails
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "packageId": "92125",
      "packageName": "Annual Package",
      "platform": "",
      "products": [
        {
          "id": "92098",
          "name": "IGU Annual",
          "description": "IGU Annual",
          "price": "0.00",
          "mandatory": "no",
          "platform": "",
          "servicetype": "GPRS",
          "serviceCode": "/service/telco/gprs",
          "productType": "Product",
          "productImage": "",
          "reviewRating": "5",
          "reviewCount": "2",
          "associated": "false"
        },
        {
          "id": "92099",
          "name": "CSS Hardware Annual",
          "description": "CSS Hardware Annual",
          "price": "0.00",
          "mandatory": "no",
          "platform": "",
          "servicetype": "GPRS",
          "serviceCode": "/service/telco/gprs",
          "productType": "Product",
          "productImage": "",
          "reviewRating": "5",
          "reviewCount": "1",
          "associated": "false"
        },
        {
          "id": "92100",
          "name": "CSS Software Annual",
          "description": "CSS Software Annual",
          "price": "0.00",
          "mandatory": "no",
          "platform": "",
          "servicetype": "GPRS",
          "serviceCode": "/service/telco/gprs",
          "productType": "Product",
          "productImage": "",
          "reviewRating": "",
          "reviewCount": "0",
          "associated": "false"
        },
        {
          "id": "92101",
          "name": "Commissioning Annual",
          "description": "Commissioning Annual",
          "price": "0.00",
          "mandatory": "no",
          "platform": "",
          "servicetype": "GPRS",
          "serviceCode": "/service/telco/gprs",
          "productType": "Product",
          "productImage": "",
          "reviewRating": "",
          "reviewCount": "0",
          "associated": "false"
        },
        {
          "id": "92102",
          "name": "Design Fees Annual",
          "description": "Design Fees Annual",
          "price": "0.00",
          "mandatory": "no",
          "platform": "",
          "servicetype": "GPRS",
          "serviceCode": "/service/telco/gprs",
          "productType": "Product",
          "productImage": "",
          "reviewRating": "",
          "reviewCount": "0",
          "associated": "false"
        },
        {
          "id": "92103",
          "name": "Freight Fees Annual",
          "description": "Freight Fees Annual",
          "price": "0.00",
          "mandatory": "no",
          "platform": "",
          "servicetype": "GPRS",
          "serviceCode": "/service/telco/gprs",
          "productType": "Product",
          "productImage": "",
          "reviewRating": "",
          "reviewCount": "0",
          "associated": "false"
        },
        {
          "id": "92122",
          "name": "View 100 Percent",
          "description": "View 100 Percent",
          "price": "0.00",
          "mandatory": "no",
          "platform": "",
          "servicetype": "GPRS",
          "serviceCode": "/service/telco/gprs",
          "productType": "Discount",
          "productImage": "",
          "reviewRating": "",
          "reviewCount": "0",
          "associated": "false"
        },
        {
          "id": "92145",
          "name": "Contract View",
          "description": "Contract View.",
          "price": "0.00",
          "mandatory": "no",
          "platform": "",
          "servicetype": "GPRS",
          "serviceCode": "",
          "productType": "Product",
          "productImage": "",
          "reviewRating": "",
          "reviewCount": "0",
          "associated": "true"
        }
      ]
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
  /crm/v1/package/bolton
{{% /method-block %}}

This service is used to add a bolton into the customer package.

It requires token, serviceProvider, source, srdate, operation, correlationId and destination as input parameters. If successful the new bolton will be added into the customer's package. If failed appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header)      |   Provide the bolton token as the value. |
| **serviceProvider** (mandatory)    | ``string`` (header)      |   Provide the serviceProvider as the value. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - purchaseBolton |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

#### *Request Body Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| {{< expand id="testing1" atext="boltOn (array)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>platform</td>
<td>string</td>
<td>Provide the platform as the value. For example - Postpaid</td>
</tr>
<tr>
<td>ProductId</td>
<td>string</td>
<td>Provide product id as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| **msisdn** (mandatory) | ``string``       |    Provide the msisdn number as the value. For example - 9800078903 |
{{< tabs "uniqueid3" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
token:string
serviceProvider:string
correlationId:123e4567-e89b-12d3-a456-426614174000
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:purchaseBolton
{{< / highlight >}}
{{< /tab >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}

{
    "boltOn": [
        {
            "platform": "PostPaid",
            "productId": "646735"
        }
    ],
    "msisdn": "9800078903"
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
        "salesOrderNo": "SO2538",
        "grandTotal": 599,
        "subTotal": 599,
        "hdnDiscountAmount": "",
        "preTaxTotal": 599,
        "lineItems": [
          {
            "productName": "Samsung Galaxy S10",
            "listPrice": "599.00"
          },
          {
            "productName": "MSISDN",
            "listPrice": "0.00"
          }
        ]
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

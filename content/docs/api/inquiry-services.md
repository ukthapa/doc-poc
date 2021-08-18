---
title: "Inquiry Services"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "CRM"
weight: 206
toc: false
---

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /crm/v1/services/inventory
{{% /method-block %}}

This service allows you to fetch the complete list of inventories available in the system. It requires token, destination, operation, source, sedate, correlationId, irstatus and limit as input parameters. If successful the list of inventories available in the system will be returned. In case of failure the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **irStatus** (mandatory)    | ``string`` (query) | Provide the status of the inventory. |
| **limit** (mandatory)    | ``string`` (query)      |   Provide the capacity limit of the inventory. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:SO-100
email:adarsha_cds1@yopmail.com
irStatus:reserved
limit:5
operation:emailExists
destination:CRM
source:Selfcare
srDate:11-09-2021
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": [
      {
        "imsisdn": "1900000228",
        "id": "70x585"
      },
      {
        "imsisdn": "1900000229",
        "id": "70x586"
      },
      {
        "imsisdn": "1900000230",
        "id": "70x587"
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

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
  /crm/v1/services/review
{{% /method-block %}}

This service is used to record the review comments by the customers. It requires token,serviceProvider,correlationId,srdate,source,operation,destination as input parameters. If successful the feedback from the customers are updated in the system with the customer reference.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header)      |   Provide the token of the review comment. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - emailExists |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **id** (mandatory)    | ``string`` (body)      |   Provide the id of the review comment as the value. For example - 242159 |
| **message** (mandatory)    | ``string`` (body)      |   Provide the message of the review comment as the value. For example - add review testing |
| **title** (mandatory)    | ``string`` (body)      |   Provide the title of the review comment as the value. For example - title |
| **accountNumber** (mandatory)    | ``string`` (body)      |   Provide the account number as the value. For example - MVNE204564 |
| **rating** (mandatory)    | ``string`` (body)      |   Provide the rating of the review as the value. For example - 5 |
| **screenName** (mandatory)    | ``string`` (body)      |   Provide the screen name as the value. For example - Troubleshoot |
| **type** (mandatory)    | ``string`` (body)      |   Provide the type of comment as the value. For example - Product |

{{< tabs "uniqueid1" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
token:AB110F
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
    "id": "242159",
    "message": "add review testing in 71 -2",
    "title": "title",
    "accountNumber": "MVNE204564",
    "rating": "5",
    "screenName": "Troubleshoot",
    "type": "Product"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "message": "Review submitted successfully"
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

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /crm/v1/services/location
{{% /method-block %}}

This service allows you to fetch the location of the customer.

It requires token, correlationId, srdate, source, operation, destination as input parameters. If successful the location of the customer updated in the system will be retrieved. If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header) | Provide the token as the value. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid2" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:SO-100
token:string
operation:emailExists
destination:CRM
source:Selfcare
srDate:11-09-2021
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "packagelist_no": "PKL_31",
      "name": "GSM Connection",
      "assigned_user_id": "19x1",
      "createdtime": "2019-01-25 06:53:53",
      "modifiedtime": "2019-04-03 15:44:54",
      "modifiedby": "19x25",
      "description": "",
      "location": "California",
      "active": "1",
      "source": "CRM",
      "starred": "",
      "tags": "",
      "id": "38x7574",
      "label": "GSM Connection"
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Client Error" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "false",
    "result": {
      "arguments": {
        "statusCode": "401",
        "errorCode": "INVALID_TOKEN",
        "errorMessage": "JWT strings must contain exactly 2 period characters. Found: 0"
      }
    }
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

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /crm/v1/services
{{% /method-block %}}

This service is used to fetch the details based on the operation.

It requires operation names ( promotions, troubleshoot FAQ ,offer, coupon, stores, Theme etc.). If successful the details related to the operations will be displayed. If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header) | Provide the token as the value. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |
| **resuestParams** (mandatory) | ``object`` (query)      |    Provide the request parameters as the value. |

{{< tabs "uniqueid" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
token:string
operation:emailExists
destination:CRM
source:Selfcare
srDate:11-09-2021
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "categories": [
        "Offers",
        "Promotions",
        "Coupons"
      ],
      "currentCategory": "Promotions",
      "items": [
        {
          "promotionImage": "http://localhost:1212/storage/2019/September/week3/82326_22158_Mask_Group_12.png",
          "promotionContent": "50 GB data services for $50",
          "promotionTitle": "50 GB data for $50"
        },
        {
          "promotionImage": "http://localhost:1212/storage/2019/September/week3/82325_22161_Offers_IMG_7_XXXHDPI.png",
          "promotionContent": "1000 SMS services for 10$",
          "promotionTitle": "1000 SMS for $100"
        },
        {
          "promotionImage": "http://localhost:1212/storage/2019/September/week3/82323_22166_Offers_IMG_9_XXXHDPI.png",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100 SMS for $10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$",
          "promotionTitle": "100SMS for $ 10"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
        },
        {
          "promotionImage": "http://localhost:1212/_",
          "promotionContent": "100 SMS services for 10$ duplicate",
          "promotionTitle": "1000SMS for $ 100"
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

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /crm/v1/services/promotion
{{% /method-block %}}

This service is used to fetch the list of eligible promotions for the customer.

It requires token, correlationId, srdate, source, operation, destination as input parameters. If successful all the promotions available in the system will be returned. If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header) | Provide the token as the value. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid7" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
token:string
operation:emailExists
destination:CRM
source:Selfcare
srDate:11-09-2021
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": [
      {
        "promotion_no": "PROMOTION_92",
        "promotioncontent": "Macays Offer Details",
        "publishstartdate": "2017-09-10",
        "publishenddate": "2017-09-14",
        "active": "1",
        "promotionsource": "portal",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:22",
        "modifiedtime": "2019-09-14 17:40:53",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20625",
        "promotioncategory": "Coupons",
        "promotiontitle": "Macays",
        "id": "40x20556"
      },
      {
        "promotion_no": "PROMOTION_124",
        "promotioncontent": "20 Gb Data at £10",
        "publishstartdate": "2017-09-15",
        "publishenddate": "2017-09-15",
        "active": "1",
        "promotionsource": "portal",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:28",
        "modifiedtime": "2019-12-16 22:50:48",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20624",
        "promotioncategory": "Coupons",
        "promotiontitle": "20 GB Data",
        "id": "40x20588"
      },
      {
        "promotion_no": "PROMOTION_130",
        "promotioncontent": "25% off on all stays across Europe",
        "publishstartdate": "2017-09-06",
        "publishenddate": "2017-09-06",
        "active": "1",
        "promotionsource": "portal",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:29",
        "modifiedtime": "2019-09-14 17:39:32",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20622",
        "promotioncategory": "Coupons",
        "promotiontitle": "Airbnb",
        "id": "40x20594"
      },
      {
        "promotion_no": "PROMOTION_131",
        "promotioncontent": "Netflix offer details",
        "publishstartdate": "2017-09-04",
        "publishenddate": "2017-09-04",
        "active": "1",
        "promotionsource": "portal",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:29",
        "modifiedtime": "2019-09-14 17:38:45",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20621",
        "promotioncategory": "Coupons",
        "promotiontitle": "Netflix",
        "id": "40x20595"
      },
      {
        "promotion_no": "PROMOTION_132",
        "promotioncontent": "Dominos offer details",
        "publishstartdate": "2017-09-07",
        "publishenddate": "2017-09-07",
        "active": "1",
        "promotionsource": "portal",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:29",
        "modifiedtime": "2019-09-14 17:39:46",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20623",
        "promotioncategory": "Coupons",
        "promotiontitle": "Dominos",
        "id": "40x20596"
      },
      {
        "promotion_no": "PROMOTION_139",
        "promotioncontent": "50 GB data £50",
        "publishstartdate": "2019-07-16",
        "publishenddate": "2019-07-21",
        "active": "1",
        "promotionsource": "portal",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:31",
        "modifiedtime": "2019-12-13 15:38:04",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20618",
        "promotioncategory": "Promotions",
        "promotiontitle": "50 GB data £50",
        "id": "40x20603"
      },
      {
        "promotion_no": "PROMOTION_141",
        "promotioncontent": "100 SMS services for £10",
        "publishstartdate": "2019-07-16",
        "publishenddate": "2021-07-23",
        "active": "1",
        "promotionsource": "portal",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:31",
        "modifiedtime": "2019-12-16 18:42:39",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20752",
        "promotioncategory": "Promotions",
        "promotiontitle": "100 SMS for £10",
        "id": "40x20605"
      },
      {
        "promotion_no": "PROMOTION_145",
        "promotioncontent": "SMS services for £100",
        "publishstartdate": "2019-07-16",
        "publishenddate": "2021-07-23",
        "active": "1",
        "promotionsource": "portal",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:32",
        "modifiedtime": "2019-12-16 18:42:53",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20751",
        "promotioncategory": "Promotions",
        "promotiontitle": "1000 SMS for £100",
        "id": "40x20609"
      },
      {
        "promotion_no": "PROMOTION_146",
        "promotioncontent": "Every Friday 50% OFF on Movie Tickets.",
        "publishstartdate": "2019-08-01",
        "publishenddate": "2020-10-31",
        "active": "1",
        "promotionsource": "",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:32",
        "modifiedtime": "2019-12-16 18:46:36",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20615",
        "promotioncategory": "Offers",
        "promotiontitle": "Every Friday 50% OFF on Movie Tickets.",
        "id": "40x20610"
      },
      {
        "promotion_no": "PROMOTION_147",
        "promotioncontent": "Victor Mobile Offers - Pay Monthly, Build your own Package.",
        "publishstartdate": "2019-08-01",
        "publishenddate": "2019-12-31",
        "active": "1",
        "promotionsource": "",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:32",
        "modifiedtime": "2019-12-16 18:45:29",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20616",
        "promotioncategory": "Offers",
        "promotiontitle": "Victor Mobile Offers - Pay Monthly, Build your own Package.",
        "id": "40x20611"
      },
      {
        "promotion_no": "PROMOTION_148",
        "promotioncontent": "Instant Discount of £10 on your First Ride.",
        "publishstartdate": "2019-07-01",
        "publishenddate": "2019-10-31",
        "active": "1",
        "promotionsource": "",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:32",
        "modifiedtime": "2019-12-16 18:47:39",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "20614",
        "promotioncategory": "Offers",
        "promotiontitle": "Instant Discount of £10 on your First Ride.",
        "id": "40x20612"
      },
      {
        "promotion_no": "PROMOTION_149",
        "promotioncontent": "Welcome to Victor Mobile!  All New Activations are eligible upto 50% discounted rate.",
        "publishstartdate": "2019-09-11",
        "publishenddate": "2019-10-31",
        "active": "1",
        "promotionsource": "",
        "assigned_user_id": "19x1",
        "createdtime": "2019-09-14 17:05:33",
        "modifiedtime": "2019-12-16 22:47:50",
        "modifiedby": "19x1",
        "source": "CRM",
        "starred": "",
        "tags": "",
        "promotionimage": "",
        "promotioncategory": "Offers",
        "promotiontitle": "Welcome to Victor Mobile!  All New Activations are eligible upto 50% discounted rate.",
        "id": "40x20613"
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

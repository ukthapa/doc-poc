---
title: "Voucher Services"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "CRM"
weight: 209
toc: false
---

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
  /crm/v1/services/redeem/voucher
{{% /method-block %}}

This service is allows the user to redeem the voucher.

It requires token,serviceProvider,correlationId,srdate,source,operation,destination as input parameters along with two important attribute voucher code and voucher pin in the request body. If successful the voucher would be redeemed. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header)      |   Provide the token of the voucher as the value. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - redeemVoucher |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **voucherCode** (mandatory)    | ``string`` (body)      |   Provide the code of the voucher as the value. For example - June_07JK68 |
| **voucherPin** (mandatory)    | ``string`` (body)      |   Provide the pin of the voucher as the value. For example - K54- |

{{< tabs "uniqueid1" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
toekn:string
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
	"voucherCode": "June_07JK68#_",
	"voucherPin":"K54-"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "message": "Voucher redeemed successfully!"
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

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
  /crm/v1/services/voucher/info
{{% /method-block %}}

This service is used to fetch the voucher information.

It requires token,serviceProvider,correlationId,srdate,source,operation,destination as input parameters. If successful the voucher information will be returned with respect to voucher code and voucher pin. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header)      |   Provide the token of the voucher as the value. |
| **serviceProvider** (mandatory)    | ``string`` (header)      |   Provide the name of the service provider. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - voucherInfo |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **voucherCode** (mandatory)    | ``string`` (body)      |   Provide the code of the voucher as the value. For example - June_07JK68 |
| **voucherPin** (mandatory)    | ``string`` (body)      |   Provide the pin of the voucher as the value. For example - K54- |

{{< tabs "uniqueid2" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
toekn:string
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
  "voucherCode": "June_07JK68",
  "voucherPin": "K54-"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "voucherBenefitsMessage": "Voucher Benefits:",
      "voucherBenefits": [
        "cSMART_Voice_Product_Premium"
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

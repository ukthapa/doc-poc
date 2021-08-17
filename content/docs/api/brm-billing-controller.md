---
title: "BRM Billing Controller"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "BRM"
weight: 301
toc: false
---

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /brm/v1/billing/balance
{{% /method-block %}}

This service allows you to fetch the balance details of an account number from BRM.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **accountNo** (optional)    | ``string`` (query) | Provide the account number of which you want to view the balance details. |
| **deviceId** (optional)    | ``string`` (query)      |   Provide the device ID. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
accountNo:string
deviceId:string
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "result": {
      "success": "true",
      "arguments": {
        "BALANCE_GROUPS": {
          "elem": 0,
          "BALANCES": [
            {
              "elem": 1000199,
              "END_T": 0,
              "START_T": 1623239431,
              "CREDIT_FLOOR": "",
              "CREDIT_LIMIT": 0,
              "RESOURCE_ID": 1000199,
              "TYPE_STR": "None",
              "CURRENT_BAL": -100,
              "INFO": "Product description not found",
              "AMOUNT_ORIG": "",
              "DESCR": "PostPaid_Deposit"
            },
            {
              "elem": 840,
              "END_T": 0,
              "START_T": 1623177000,
              "CREDIT_FLOOR": "",
              "CREDIT_LIMIT": 1000,
              "RESOURCE_ID": 840,
              "TYPE_STR": "None",
              "CURRENT_BAL": -45.15,
              "INFO": "Product description not found",
              "AMOUNT_ORIG": "",
              "DESCR": "USD"
            },
            {
              "elem": 5000001,
              "END_T": 1630089000,
              "START_T": 1627410600,
              "CREDIT_FLOOR": -6000,
              "CREDIT_LIMIT": 0,
              "RESOURCE_ID": 5000001,
              "TYPE_STR": "Second",
              "CURRENT_BAL": -6000,
              "INFO": "100_MINS_Voice_Postpaid_CO",
              "AMOUNT_ORIG": -6000,
              "DESCR": "Limited_Voice_Bank"
            },
            {
              "elem": 6000001,
              "END_T": 1630089000,
              "START_T": 1627410600,
              "CREDIT_FLOOR": -50,
              "CREDIT_LIMIT": 0,
              "RESOURCE_ID": 6000001,
              "TYPE_STR": "None",
              "CURRENT_BAL": -50,
              "INFO": "50_Sms_Postpaid_CO",
              "AMOUNT_ORIG": -50,
              "DESCR": "Limited_Sms_Bank"
            }
          ],
          "BAL_GRP_OBJ": "0.0.0.1 /balance_group 43104763 0"
        },
        "ERROR_NUM": 0,
        "POID": "0.0.0.1 /account 43103483 0"
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
      "success": "false",
      "arguments": {
        "errorCode": "6000003",
        "errorMessage": "BRM Error -Invalid account number"
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
        "errorCode": "6000003",
        "errorMessage": "BRM Error -ERR_NAP_CONNECT_FAILED"
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /brm/v1/billing/accountdetails
{{% /method-block %}}

This service allows you to fetch the account information of a particular account number and device ID from BRM.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **accountNo** (mandatory)    | ``string`` (query) | Provide the account number of which you want to view the balance details. |
| **deviceId** (mandatory)    | ``string`` (query)      |   Provide the device ID. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
accountNo:string
deviceId:string
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "arguments": {
        "START_T": 1635359400,
        "EXPIRATION_T": 1638037800,
        "AAC_PACKAGE": "PT_Postpaid_PKG",
        "AUTO_RENEW_PLAN_NAME": "PT_Postpaid_PKG",
        "BALANCE_GROUPS": {
          "elem": 0,
          "BALANCES": [
            {
              "elem": 1000199,
              "END_T": 0,
              "START_T": 1623239431,
              "CREDIT_FLOOR": "",
              "CREDIT_LIMIT": 0,
              "RESOURCE_ID": 1000199,
              "TYPE_STR": "None",
              "CURRENT_BAL": -100,
              "INFO": "Product description not found",
              "AMOUNT_ORIG": "",
              "DESCR": "PostPaid_Deposit"
            },
            {
              "elem": 840,
              "END_T": 0,
              "START_T": 1623177000,
              "CREDIT_FLOOR": "",
              "CREDIT_LIMIT": 1000,
              "RESOURCE_ID": 840,
              "TYPE_STR": "None",
              "CURRENT_BAL": -45.15,
              "INFO": "Product description not found",
              "AMOUNT_ORIG": "",
              "DESCR": "USD"
            },
            {
              "elem": 5000001,
              "END_T": 1627410600,
              "START_T": 1624818600,
              "CREDIT_FLOOR": -6000,
              "CREDIT_LIMIT": 0,
              "RESOURCE_ID": 5000001,
              "TYPE_STR": "Second",
              "CURRENT_BAL": -6000,
              "INFO": "100_MINS_Voice_Postpaid_CO",
              "AMOUNT_ORIG": -6000,
              "DESCR": "Limited_Voice_Bank"
            },
            {
              "elem": 6000001,
              "END_T": 1627410600,
              "START_T": 1624818600,
              "CREDIT_FLOOR": -50,
              "CREDIT_LIMIT": 0,
              "RESOURCE_ID": 6000001,
              "TYPE_STR": "None",
              "CURRENT_BAL": -50,
              "INFO": "50_Sms_Postpaid_CO",
              "AMOUNT_ORIG": -50,
              "DESCR": "Limited_Sms_Bank"
            },
            {
              "elem": 4000001,
              "END_T": 1627410600,
              "START_T": 1625077800,
              "CREDIT_FLOOR": -5368709120,
              "CREDIT_LIMIT": 0,
              "RESOURCE_ID": 4000001,
              "TYPE_STR": "Byte",
              "CURRENT_BAL": -5368709050,
              "INFO": "5_GB_Limited_Postpaid_CO",
              "AMOUNT_ORIG": -5368709120,
              "DESCR": "Limited_Data_Bank"
            }
          ],
          "BAL_GRP_OBJ": "0.0.0.1 /balance_group 43104763 0"
        },
        "AMOUNT": 0,
        "CSMART_FLD_DEPOSIT": 100,
        "EFFECTIVE_T": 1623239431,
        "ACCOUNT_NO": "VKPOSTPAID1181",
        "NAMEINFO": {
          "elem": 1,
          "LAST_CANON": "souza",
          "ZIP": 560034,
          "MIDDLE_CANON": "",
          "EMAIL_ADDR": "linda@yopmail.com",
          "STATE": "TX",
          "TAXPKG_TYPE": 0,
          "CANON_COUNTRY": "IN",
          "LAST_NAME": "souza",
          "FIRST_NAME": "lucrécia",
          "COMPANY": "Linda",
          "GEOCODE": "",
          "CITY": "Amarillo",
          "CONTACT_TYPE": "Primary Contact",
          "COUNTRY": "India",
          "SALUTATION": "",
          "ADDRESS": "Hilltop Drive, 4398",
          "CANON_COMPANY": "linda",
          "MIDDLE_NAME": "",
          "PHONES": {
            "elem": 1,
            "PHONE": "815-436-4650",
            "TYPE": 1
          },
          "TITLE": "",
          "SERVICE_OBJ": "0.0.0.0  0 0",
          "FIRST_CANON": "lucrecia"
        },
        "DESCR": "test",
        "ERROR_NUM": 0,
        "POID": "0.0.0.1 /account 43103483 12"
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
      "success": "false",
      "arguments": {
        "errorCode": "6000003",
        "errorMessage": "BRM Error -Invalid account number"
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
        "errorCode": "6000003",
        "errorMessage": "BRM Error -ERR_NAP_CONNECT_FAILED"
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /brm/v1/billing/planSwitchHistory/{accountNo}
{{% /method-block %}}

This service allows you to fetch the plan switch History information of a given account number within a given start and end date from BRM.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **accountNo** (mandatory)    | ``string`` (query) | Provide the account number of which you want to view the balance details. |
| **start** (optional)    | ``string`` (query)      |   Provide the start date. |
| **end** (optional)    | ``string`` (query)      |   Provide the end date. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
accountNo:string
startDate:01.01.2019
endDate:31.12.2019
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "arguments": {
        "RESULTS": [
          {
            "elem": 0,
            "DD_ACTIVATION_DATE": 1585593000,
            "TYPE_STR": "cSMART Plan Change",
            "OWNER_NAME": "Vivek",
            "CSMART_FLD_TO_PLAN": "BIG 5 Promo - MIFI_40GB20K",
            "CSMART_FLD_FROM_PLAN": "BIG 5 Promo - MIFI_40GB20K"
          },
          {
            "elem": 1,
            "DD_ACTIVATION_DATE": 1585593000,
            "TYPE_STR": "cSMART Plan Change",
            "OWNER_NAME": "",
            "CSMART_FLD_TO_PLAN": "BIG 5 Promo - MIFI_40GB20K",
            "CSMART_FLD_FROM_PLAN": "BIG 5 Promo - MIFI_40GB20K"
          },
          {
            "elem": 2,
            "DD_ACTIVATION_DATE": 1600239297,
            "TYPE_STR": "Immediate",
            "OWNER_NAME": "",
            "CSMART_FLD_TO_PLAN": "Basic package Postpaid",
            "CSMART_FLD_FROM_PLAN": "Basic package Postpaid"
          },
          {
            "elem": 3,
            "DD_ACTIVATION_DATE": 1600240718,
            "TYPE_STR": "Immediate",
            "OWNER_NAME": "",
            "CSMART_FLD_TO_PLAN": "Basic package Postpaid",
            "CSMART_FLD_FROM_PLAN": "Basic package Postpaid"
          },
          {
            "elem": 4,
            "DD_ACTIVATION_DATE": 1600237146,
            "TYPE_STR": "Immediate",
            "OWNER_NAME": "",
            "CSMART_FLD_TO_PLAN": "Basic package Postpaid",
            "CSMART_FLD_FROM_PLAN": "Basic package Postpaid"
          }
        ],
        "POID": "0.0.0.1 /event/activity/csmart/plan_change -1 0"
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
      "success": "false",
      "arguments": {
        "errorCode": "6000003",
        "errorMessage": "BRM Error -Invalid account number"
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
        "errorCode": "6000003",
        "errorMessage": "BRM Error -ERR_NAP_CONNECT_FAILED"
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

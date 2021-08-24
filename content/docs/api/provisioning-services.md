---
title: "Provisioning Services"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "BRM"
weight: 303
toc: false
---

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
​/brm​/v1​/service​/getBeId
{{% /method-block %}}

This service allows you to fetch the list of bill details available in the system.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:SO-100
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
    "result": {
      "success": "true",
      "arguments": {
        "BALANCES": [
          {
            "elem": 0,
            "SYMBOL": "$",
            "RESOURCE_ID": 36,
            "NAME": "Australian Dollar"
          },
          {
            "elem": 1,
            "SYMBOL": "oS",
            "RESOURCE_ID": 40,
            "NAME": "Austrian Schilling"
          },
          {
            "elem": 2,
            "SYMBOL": "BF",
            "RESOURCE_ID": 56,
            "NAME": "Belgian Franc"
          },
          {
            "elem": 3,
            "SYMBOL": "Can$",
            "RESOURCE_ID": 124,
            "NAME": "Canadian Dollar"
          },
          {
            "elem": 4,
            "SYMBOL": "mk",
            "RESOURCE_ID": 246,
            "NAME": "Finnish Markka"
          },
          {
            "elem": 5,
            "SYMBOL": "F",
            "RESOURCE_ID": 250,
            "NAME": "French Franc"
          },
          {
            "elem": 6,
            "SYMBOL": "DM",
            "RESOURCE_ID": 280,
            "NAME": "Deutsche Mark"
          },
          {
            "elem": 7,
            "SYMBOL": "Dr",
            "RESOURCE_ID": 300,
            "NAME": "Greek Drachma"
          },
          {
            "elem": 8,
            "SYMBOL": "IRL",
            "RESOURCE_ID": 372,
            "NAME": "Irish Pound"
          },
          {
            "elem": 9,
            "SYMBOL": "L.",
            "RESOURCE_ID": 380,
            "NAME": "Italian Lira"
          },
          {
            "elem": 10,
            "SYMBOL": "Yen",
            "RESOURCE_ID": 392,
            "NAME": "Japanese Yen"
          },
          {
            "elem": 11,
            "SYMBOL": "LuxF",
            "RESOURCE_ID": 442,
            "NAME": "Luxembourg Franc"
          },
          {
            "elem": 12,
            "SYMBOL": "f.",
            "RESOURCE_ID": 528,
            "NAME": "Netherlands Guilder"
          },
          {
            "elem": 13,
            "SYMBOL": "₦",
            "RESOURCE_ID": 566,
            "NAME": "Nigerian Naira"
          },
          {
            "elem": 14,
            "SYMBOL": "Esc.",
            "RESOURCE_ID": 620,
            "NAME": "Portugese Escudo"
          },
          {
            "elem": 15,
            "SYMBOL": "Pts",
            "RESOURCE_ID": 724,
            "NAME": "Spanish Peseta"
          },
          {
            "elem": 16,
            "SYMBOL": "SFr.",
            "RESOURCE_ID": 756,
            "NAME": "Swiss Franc"
          },
          {
            "elem": 17,
            "SYMBOL": "L",
            "RESOURCE_ID": 826,
            "NAME": "British Pound Sterling"
          },
          {
            "elem": 18,
            "SYMBOL": "$",
            "RESOURCE_ID": 840,
            "NAME": "US Dollar"
          },
          {
            "elem": 19,
            "SYMBOL": "E",
            "RESOURCE_ID": 978,
            "NAME": "Euro"
          },
          {
            "elem": 20,
            "SYMBOL": "SDR",
            "RESOURCE_ID": 999,
            "NAME": "Special Drawing Right"
          },
          {
            "elem": 21,
            "SYMBOL": "NonCur",
            "RESOURCE_ID": 100001,
            "NAME": "PO balance"
          },
          {
            "elem": 22,
            "SYMBOL": "NonCur",
            "RESOURCE_ID": 100002,
            "NAME": "MINUTES balance"
          },
          {
            "elem": 23,
            "SYMBOL": "Hrs",
            "RESOURCE_ID": 1000001,
            "NAME": "async bulk hours"
          },
          {
            "elem": 24,
            "SYMBOL": "Hrs",
            "RESOURCE_ID": 1000002,
            "NAME": "isdn bulk hours"
          },
          {
            "elem": 25,
            "SYMBOL": "Mil",
            "RESOURCE_ID": 1000003,
            "NAME": "Frequent Flier Miles"
          },
          {
            "elem": 26,
            "SYMBOL": "Gam",
            "RESOURCE_ID": 1000004,
            "NAME": "Free Game"
          },
          {
            "elem": 27,
            "SYMBOL": "Aud",
            "RESOURCE_ID": 1000005,
            "NAME": "Minute Streamed Audio"
          },
          {
            "elem": 28,
            "SYMBOL": "Vid",
            "RESOURCE_ID": 1000006,
            "NAME": "Minute Streamed Video"
          },
          {
            "elem": 29,
            "SYMBOL": "Art",
            "RESOURCE_ID": 1000007,
            "NAME": "Articles Downloaded"
          },
          {
            "elem": 30,
            "SYMBOL": "Mon",
            "RESOURCE_ID": 1000008,
            "NAME": "paid month"
          },
          {
            "elem": 31,
            "SYMBOL": "Mbu",
            "RESOURCE_ID": 1000009,
            "NAME": "MB Used"
          },
          {
            "elem": 32,
            "SYMBOL": "Min",
            "RESOURCE_ID": 1000010,
            "NAME": "Free Domestic Minutes"
          },
          {
            "elem": 33,
            "SYMBOL": "Wrn",
            "RESOURCE_ID": 1000011,
            "NAME": "Warning"
          },
          {
            "elem": 34,
            "SYMBOL": "PQ",
            "RESOURCE_ID": 1000012,
            "NAME": "Paid Quarter"
          },
          {
            "elem": 35,
            "SYMBOL": "Art",
            "RESOURCE_ID": 1000018,
            "NAME": "Artist Royalty"
          },
          {
            "elem": 36,
            "SYMBOL": "Son",
            "RESOURCE_ID": 1000019,
            "NAME": "Songs Downloaded"
          },
          {
            "elem": 37,
            "SYMBOL": "Min",
            "RESOURCE_ID": 1000020,
            "NAME": "Free Asia Minutes"
          },
          {
            "elem": 38,
            "SYMBOL": "Pro",
            "RESOURCE_ID": 1000021,
            "NAME": "Producer Royalty"
          },
          {
            "elem": 39,
            "SYMBOL": "Pre",
            "RESOURCE_ID": 1000022,
            "NAME": "Pre-discount dollars"
          },
          {
            "elem": 40,
            "SYMBOL": "Art",
            "RESOURCE_ID": 1000023,
            "NAME": "ERP Active"
          },
          {
            "elem": 41,
            "SYMBOL": "Cas",
            "RESOURCE_ID": 1000024,
            "NAME": "ERP Causal"
          },
          {
            "elem": 42,
            "SYMBOL": "Sel",
            "RESOURCE_ID": 1000025,
            "NAME": "ERP SelfService"
          },
          {
            "elem": 43,
            "SYMBOL": "Min",
            "RESOURCE_ID": 1000026,
            "NAME": "Customer Service Minute"
          },
          {
            "elem": 44,
            "SYMBOL": "Pcm",
            "RESOURCE_ID": 1000027,
            "NAME": "Direct Parent Commission"
          },
          {
            "elem": 45,
            "SYMBOL": "Dco",
            "RESOURCE_ID": 1000028,
            "NAME": "Direct Parent Counter"
          },
          {
            "elem": 46,
            "SYMBOL": "Hcm",
            "RESOURCE_ID": 1000029,
            "NAME": "Hierarchy Commission"
          },
          {
            "elem": 47,
            "SYMBOL": "Hco",
            "RESOURCE_ID": 1000030,
            "NAME": "Hierarchy Counter"
          },
          {
            "elem": 48,
            "SYMBOL": "Mbt",
            "RESOURCE_ID": 1000031,
            "NAME": "MB Transferred"
          },
          {
            "elem": 49,
            "SYMBOL": "Kbu",
            "RESOURCE_ID": 1000090,
            "NAME": "KB Used"
          },
          {
            "elem": 50,
            "SYMBOL": "pts",
            "RESOURCE_ID": 1000091,
            "NAME": "Loyalty Points"
          },
          {
            "elem": 51,
            "SYMBOL": "tks",
            "RESOURCE_ID": 1000092,
            "NAME": "Tokens"
          },
          {
            "elem": 52,
            "SYMBOL": "bsc",
            "RESOURCE_ID": 1000093,
            "NAME": "Basic Content Accessed"
          },
          {
            "elem": 53,
            "SYMBOL": "prc",
            "RESOURCE_ID": 1000094,
            "NAME": "Premium Content Accessed"
          },
          {
            "elem": 54,
            "SYMBOL": "MIN",
            "RESOURCE_ID": 1000095,
            "NAME": "Free Seconds"
          },
          {
            "elem": 55,
            "SYMBOL": "sav",
            "RESOURCE_ID": 1000096,
            "NAME": "Saving Resource Id"
          },
          {
            "elem": 56,
            "SYMBOL": "MFUc",
            "RESOURCE_ID": 1000097,
            "NAME": "Monthly Fee & Usage Counter"
          },
          {
            "elem": 57,
            "SYMBOL": "CMFUc",
            "RESOURCE_ID": 1000098,
            "NAME": "Copy of MFUC"
          },
          {
            "elem": 58,
            "SYMBOL": "CDc",
            "RESOURCE_ID": 1000099,
            "NAME": "Contract Day Counter"
          },
          {
            "elem": 59,
            "SYMBOL": "CDCd",
            "RESOURCE_ID": 1000100,
            "NAME": "CDC for Discount"
          },
          {
            "elem": 60,
            "SYMBOL": "Lc",
            "RESOURCE_ID": 1000101,
            "NAME": "Line Counter"
          },
          {
            "elem": 61,
            "SYMBOL": "CHAGc",
            "RESOURCE_ID": 1000102,
            "NAME": "Child Aggregation Counter"
          },
          {
            "elem": 62,
            "SYMBOL": "sms",
            "RESOURCE_ID": 1000103,
            "NAME": "Short Message Service"
          },
          {
            "elem": 63,
            "SYMBOL": "sms",
            "RESOURCE_ID": 1000104,
            "NAME": "Dup Short Message Service"
          },
          {
            "elem": 64,
            "SYMBOL": "MIN",
            "RESOURCE_ID": 1000105,
            "NAME": "Dup Free Seconds"
          },
          {
            "elem": 65,
            "SYMBOL": "Kbu",
            "RESOURCE_ID": 1000106,
            "NAME": "Dup KB Used"
          },
          {
            "elem": 66,
            "SYMBOL": "OTT",
            "RESOURCE_ID": 1000107,
            "NAME": "OTT Pay Per Views count"
          },
          {
            "elem": 67,
            "SYMBOL": "DEP",
            "RESOURCE_ID": 1000200,
            "NAME": "Deposit charge"
          },
          {
            "elem": 68,
            "SYMBOL": "SKY",
            "RESOURCE_ID": 1000201,
            "NAME": "Sky"
          },
          {
            "elem": 69,
            "SYMBOL": "ESPN",
            "RESOURCE_ID": 1000202,
            "NAME": "ESPN"
          },
          {
            "elem": 70,
            "SYMBOL": "SPOTIFY",
            "RESOURCE_ID": 1000203,
            "NAME": "SPOTIFY"
          },
          {
            "elem": 71,
            "SYMBOL": "NOWTV",
            "RESOURCE_ID": 1000204,
            "NAME": "NOWTV"
          },
          {
            "elem": 72,
            "SYMBOL": "PVIDEO",
            "RESOURCE_ID": 1000205,
            "NAME": "PVIDEO"
          }
        ],
        "ERROR_NUM": 1,
        "POID": "0.0.0.1 /config/beid 7168533 0"
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
      "arguments": [
        {
          "statusCode": "400",
          "errorCode": "400 BAD_REQUEST",
          "errorMessage": "Header 'source' not present in the request."
        }
      ]
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
​/brm​/v1​/service​/getProvisioningTag
{{% /method-block %}}

This service allows you to fetch the list of provisioning tags available in the system. It requires correlationId, source, srdate, operation and destination as input parameters. If successful the complete list of provisioning tag details available in the system will be fetched. If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid7" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:SO-100
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
    "result": {
      "success": "true",
      "arguments": {
        "SERVICES": [
          {
            "elem": 0,
            "EXT_RA": [
              {
                "elem": 0,
                "NAME": "FRIENDS_FAMILY"
              },
              {
                "elem": 1,
                "NAME": "HOME_REGION"
              },
              {
                "elem": 2,
                "NAME": "SERVICELEVEL"
              },
              {
                "elem": 3,
                "NAME": "HOME_CELL"
              },
              {
                "elem": 4,
                "NAME": "DISCOUNT_MODEL"
              },
              {
                "elem": 5,
                "NAME": "RATEPLAN"
              },
              {
                "elem": 6,
                "NAME": "DISCOUNTACCOUNT"
              }
            ],
            "NAME": "/config/telco/gsm/telephony",
            "POID": "0.0.0.1 /config/telco/gsm/telephony 33715 1"
          },
          {
            "elem": 1,
            "EXT_RA": {
              "elem": 0,
              "NAME": "HOME_REGION"
            },
            "NAME": "/config/telco/gsm/data",
            "POID": "0.0.0.1 /config/telco/gsm/data 34739 0"
          },
          {
            "elem": 2,
            "EXT_RA": [
              {
                "elem": 0,
                "NAME": "FRIENDS_FAMILY"
              },
              {
                "elem": 1,
                "NAME": "HOME_CELL"
              },
              {
                "elem": 2,
                "NAME": "HOME_REGION"
              },
              {
                "elem": 3,
                "NAME": "SERVICELEVEL"
              },
              {
                "elem": 4,
                "NAME": "RATEPLAN"
              }
            ],
            "NAME": "/config/telco/gprs",
            "POID": "0.0.0.1 /config/telco/gprs 47806 0"
          }
        ],
        "ERROR_NUM": 0,
        "POID": "0.0.0.1 /search -1 0"
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
      "arguments": [
        {
          "statusCode": "400",
          "errorCode": "400 BAD_REQUEST",
          "errorMessage": "Header 'source' not present in the request."
        }
      ]
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

{{% method-block bgcolor="warning" type="bg-orange" callmethod="PUT" %}}
  /brm/v1/service/modification
{{% /method-block %}}

This service is used to modify the status of the customer in BRM.

<section>

#### *Request Body Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| {{< expand id="testing1" atext="accounts (array)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>poid</td>
<td>string</td>
<td>Provide the poid number as the value. For example - 0.0.0.1 /account -1 0</td>
</tr>
<tr>
<td>accountNo</td>
<td>string</td>
<td>Provide the account number as the value.</td>
</tr>
<tr>
<td>programName</td>
<td>string</td>
<td>Provide the program name as the value. For example - CSMART</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing2" atext="nameInfo (array)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>elem</td>
<td>string</td>
<td>Set the value as 1 if you want to enable elem.</td>
</tr>
<tr>
<td>address</td>
<td>string</td>
<td>Provide the address as the value.</td>
</tr>
<tr>
<td>city</td>
<td>string</td>
<td>Provide the city as the value.</td>
</tr>
<tr>
<td>company</td>
<td>string</td>
<td>Provide the company as the value. For example - SSN</td>
</tr>
<tr>
<td>contactType</td>
<td>string</td>
<td>Provide the type of account as the value. For example - Account holder</td>
</tr>
<tr>
<td>country</td>
<td>string</td>
<td>Provide the country as the value.</td>
</tr>
<tr>
<td>emailAddr</td>
<td>string</td>
<td>Provide the email address as the value.</td>
</tr>
<tr>
<td>firstName</td>
<td>string</td>
<td>Provide the first name as the value.</td>
</tr>
<tr>
<td>lastName</td>
<td>string</td>
<td>Provide the last name as the value.</td>
</tr>
<tr>
<td>middleName</td>
<td>string</td>
<td>Provide the middle name as the value.</td>
</tr>
<tr>
<td>salutation</td>
<td>string</td>
<td>Provide the salutation as the value. For example - Ms.</td>
</tr>
<tr>
<td>State</td>
<td>string</td>
<td>Provide the state as the value. For example - karnataka</td>
</tr>
<tr>
<td>zip</td>
<td>string</td>
<td>Provide the zip code as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing2" atext="phones (array)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>elem</td>
<td>string</td>
<td>Set the value as 1 if you want to enable elem.</td>
</tr>
<tr>
<td>Country</td>
<td>string</td>
<td>Provide the country as the value.</td>
</tr>
<tr>
<td>phone</td>
<td>string</td>
<td>Provide the phone number as the value.</td>
</tr>
<tr>
<td>State</td>
<td>string</td>
<td>Provide the state as the value.</td>
</tr>
<tr>
<td>type</td>
<td>string</td>
<td>Provide the type as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
| {{< expand id="testing2" atext="phones (array)">}}
<table><thead>
<tr>
<th>Name</th>
<th>Type</th>
<th>Description</th>
</tr></thead>
<tbody>
<tr>
<td>elem</td>
<td>string</td>
<td>Set the value as 1 if you want to enable elem.</td>
</tr>
<tr>
<td>name</td>
<td>string</td>
<td>Provide the name of the customer as the value.</td>
</tr>
<tr>
<td>value</td>
<td>string</td>
<td>Provide the email id as the value.</td>
</tr>
<tr>
<td>subscriberPreferenceId</td>
<td>string</td>
<td>Provide the id as the value.</td>
</tr>
</tbody>
</table>
{{< /expand >}} |
<section>
{{< tabs "uniqueid1" >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
    "accounts": [
        {
            "poid": "0.0.0.1 /account -1 0",
            "accountNo": "CRMPREPAID1001",
            "programName": "CSMART",
            "nameInfo": [
                {
                    "elem": "1",
                    "address": "BAN",
                    "city": "bangalore",
                    "company": "CVL",
                    "contactType": "Account holder",
                    "country": "India",
                    "emailAddr": "linda@yopmail.com",
                    "firstName": "Naga",
                    "lastName": "Lakshmi",
                    "middleName": "",
                    "salutation": "Ms",
                    "state": "Karnataka",
                    "zip": "562125",
                    "phones": [
                        {
                            "elem": "1",
                            "phone": "9916198722",
                            "type": "1"
                        }
                    ]
                }
            ],
            "profiles": [
                {
                    "elem": "0",
                    "autoRenewFlags": "1",
                    "deviceId": "190909001",
                    "subscriberPreferences": [
                        {
                            "elem": "0",
                            "name": "Customer Name",
                            "value": "NagaLakshmi",
                            "subscriberPreferenceId": "1"
                        },
                        {
                            "elem": "1",
                            "name": "Customer Email",
                            "value": "linda@yopmail.com",
                            "subscriberPreferenceId": "2"
                        },
                        {
                            "elem": "2",
                            "name": "Customer Phone",
                            "value": "9916198722",
                            "subscriberPreferenceId": "3"
                        }
                    ]
                }
            ],
            "billInfo": [
                {
                    "elem": "0",
                    "actgFutureDom": "5"
                }
            ]
        }
    ]
}
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
            "DESCR": "Account modified Successfully",
            "ERROR_NUM": 0,
            "POID": "0.0.0.1 /profile/csmart 19483041 25"
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

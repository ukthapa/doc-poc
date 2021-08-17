---
title: "Invoice Service"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "BRM"
weight: 304
toc: false
---

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
/brm/v1/invoice/balance/{accountNo}
{{% /method-block %}}

This service allows you to fetch the balance of the customer from BRM.

It requires accountNo, correlationid, srdate, source, operation and destination as input parameters. If successful it will return balance of the customer. If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **accountNo** (mandatory)    | ``string`` (path) | Provide the account number of which you want to view the balance details. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
accountNo:string
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
        "BALANCE_GROUPS": [
          {
            "elem": 0,
            "BILLINFO_OBJ": "0.0.0.1 /billinfo 7147340 0",
            "BALANCES": [
              {
                "elem": 840,
                "VALID_TO": 0,
                "RESOURCE_ID": 840,
                "TYPE_STR": "None",
                "CURRENT_BAL": 30,
                "VALID_FROM": 1583865000,
                "AMOUNT_ORIG": 0,
                "DESCR": "USD"
              },
              {
                "elem": 1000009,
                "VALID_TO": 1590431400,
                "RESOURCE_ID": 1000009,
                "TYPE_STR": "Byte",
                "CURRENT_BAL": 21474836480,
                "VALID_FROM": 1588271400,
                "AMOUNT_ORIG": 21474836480,
                "DESCR": "MB Used"
              },
              {
                "elem": 1000010,
                "VALID_TO": 1590431400,
                "RESOURCE_ID": 1000010,
                "TYPE_STR": "Second",
                "CURRENT_BAL": 60000,
                "VALID_FROM": 1588271400,
                "AMOUNT_ORIG": 60000,
                "DESCR": "Free Domestic Minutes"
              }
            ],
            "BAL_GRP_OBJ": "0.0.0.1 /balance_group 7144652 8"
          }
        ],
        "ERROR_NUM": 0,
        "POID": "0.0.0.1 /account 7144268 12"
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
/brm/v1/invoice/viewInvoice/{billNo}
{{% /method-block %}}

This service allows you to fetch the invocie information based on the invoice number.

It requires billNo, correlationid, srdate, source, operation and destination as input parameters. If successful it will return the invoice details. If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **billNo** (mandatory)    | ``string`` (path) | Provide the bill number of which you want to view the invoice details. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
billNo:string
correlationId:SO-100
operation:emailExists
destination:CRM
source:Selfcare
srDate:11-09-2021
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<invoice>
    <POID>0.0.0.1 /bill 6049459 0</POID>
    <BILLINFO elem="0">
        <CREATED_T>1566821850</CREATED_T>
        <MOD_T>1566821852</MOD_T>
        <BILL_NO>B1-4083</BILL_NO>
        <NAME>PIN Bill</NAME>
        <CURRENCY>840</CURRENCY>
        <CURRENT_TOTAL>402</CURRENT_TOTAL>
        <END_T>1564252200</END_T>
        <DUE_T>1566844200</DUE_T>
        <AR_HIERARCHY_SIZE>0</AR_HIERARCHY_SIZE>
        <PARENT>0.0.0.0  0 0</PARENT>
        <PREVIOUS_TOTAL>0</PREVIOUS_TOTAL>
        <START_T>1561660200</START_T>
        <SUBORDS_TOTAL>0</SUBORDS_TOTAL>
        <TOTAL_DUE>402</TOTAL_DUE>
        <DUE>402</DUE>
        <CURRENCY_SECONDARY>0</CURRENCY_SECONDARY>
        <FLAGS>64</FLAGS>
        <AR_BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 0</AR_BILLINFO_OBJ>
        <BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 3</BILLINFO_OBJ>
        <ADJUSTED>0</ADJUSTED>
        <DISPUTED>0</DISPUTED>
        <RECVD>0</RECVD>
        <WRITEOFF>0</WRITEOFF>
        <TRANSFERED>0</TRANSFERED>
        <TSTAMP_VAL>1566821850</TSTAMP_VAL>
        <POID>0.0.0.1 /billinfo 6047411 6</POID>
        <ACTUAL_LAST_BILL_T>0</ACTUAL_LAST_BILL_T>
        <LAST_BILL_OBJ>0.0.0.1 /bill 6049459 0</LAST_BILL_OBJ>
        <LAST_BILL_T>1564252200</LAST_BILL_T>
        <PAYINFO_OBJ>0.0.0.1 /payinfo/invoice 6046387 0</PAYINFO_OBJ>
        <PAY_TYPE>10001</PAY_TYPE>
        <ACTG_TYPE>2</ACTG_TYPE>
        <PARENT_FLAGS>0</PARENT_FLAGS>
        <BILL_OBJ>0.0.0.1 /bill 6049459 3</BILL_OBJ>
    </BILLINFO>
    <PREVIOUS_TOTAL>0</PREVIOUS_TOTAL>
    <ACCTINFO elem="0">
        <ACCOUNT_NO>ACC51821</ACCOUNT_NO>
        <CURRENCY>840</CURRENCY>
        <CURRENCY_SECONDARY>0</CURRENCY_SECONDARY>
        <LOCALE>en_US</LOCALE>
        <GROUP_OBJ>0.0.0.0  0 0</GROUP_OBJ>
        <ACCOUNT_OBJ>0.0.0.1 /account 6048947 8</ACCOUNT_OBJ>
        <CUSTOMER_TYPE>0</CUSTOMER_TYPE>
    </ACCTINFO>
    <END_T>1566820377</END_T>
    <OVERDUE_AMOUNT>0</OVERDUE_AMOUNT>
    <CURRENCIES elem="840">
        <BEID_STR_CODE>USD</BEID_STR_CODE>
        <NAME>US Dollar</NAME>
        <ROUNDING>2</ROUNDING>
        <ROUNDING_MODE>0</ROUNDING_MODE>
        <STATUS>1</STATUS>
        <SYMBOL>$</SYMBOL>
        <TOLERANCE_AMOUNT_MIN>0.01</TOLERANCE_AMOUNT_MIN>
        <TOLERANCE_AMOUNT_MAX>0.05</TOLERANCE_AMOUNT_MAX>
        <TOLERANCE_PERCENT>0.04</TOLERANCE_PERCENT>
    </CURRENCIES>
    <INV_FLAGS>1</INV_FLAGS>
    <NAMEINFO elem="1">
        <SALUTATION></SALUTATION>
        <LAST_NAME>akkisetty</LAST_NAME>
        <FIRST_NAME>venkatesh</FIRST_NAME>
        <MIDDLE_NAME></MIDDLE_NAME>
        <TITLE></TITLE>
        <COMPANY>venkatesh akkisetty</COMPANY>
        <ADDRESS>Covalense Technologies</ADDRESS>
        <CITY>Bengaluru</CITY>
        <STATE>Karnataka</STATE>
        <ZIP>560034</ZIP>
        <COUNTRY>India</COUNTRY>
        <NAME>venkatesh akkisetty</NAME>
    </NAMEINFO>
    <INV_INFO elem="0">
        <DELIVERY_DESCR>venkatesh.akkisetty@yopmail.com</DELIVERY_DESCR>
        <DELIVERY_PREFER>0</DELIVERY_PREFER>
        <EMAIL_ADDR>venkatesh.akkisetty@yopmail.com</EMAIL_ADDR>
        <INV_INSTR></INV_INSTR>
        <INV_TERMS>0</INV_TERMS>
    </INV_INFO>
    <PARENT>0.0.0.0  0 0</PARENT>
    <DEVICES elem="1">
        <DEVICE_ID>No Device</DEVICE_ID>
        <ACCOUNT_OBJ>0.0.0.1 /account 6048947 0</ACCOUNT_OBJ>
        <SERVICES elem="0">
            <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/telephony 6048691 0</SERVICE_OBJ>
            <ACCOUNT_OBJ>0.0.0.1 /account 6048947 0</ACCOUNT_OBJ>
            <AR_ITEMS elem="2">
                <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/telephony 6048691 0</SERVICE_OBJ>
                <ITEM_NO>B1-4083,2</ITEM_NO>
                <NAME>Usage</NAME>
                <ITEM_TOTAL>0</ITEM_TOTAL>
                <DUE_T>1566844200</DUE_T>
                <DUE>0</DUE>
                <DISPUTED>0</DISPUTED>
                <EVENT_POID_LIST></EVENT_POID_LIST>
                <ACCOUNT_OBJ>0.0.0.1 /account 6048947 0</ACCOUNT_OBJ>
                <BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 0</BILLINFO_OBJ>
                <AR_BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 2</AR_BILLINFO_OBJ>
                <BILL_OBJ>0.0.0.1 /bill 6049459 0</BILL_OBJ>
                <EFFECTIVE_T>1564252200</EFFECTIVE_T>
                <CREATED_T>1566821850</CREATED_T>
                <ITEM_OBJ>0.0.0.1 /item/usage 6047667 0</ITEM_OBJ>
            </AR_ITEMS>
            <AR_ITEMS elem="3">
                <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/telephony 6048691 0</SERVICE_OBJ>
                <ITEM_NO>B1-4083,3</ITEM_NO>
                <NAME>telephony</NAME>
                <ITEM_TOTAL>0</ITEM_TOTAL>
                <DUE_T>1566844200</DUE_T>
                <DUE>0</DUE>
                <DISPUTED>0</DISPUTED>
                <EVENT_POID_LIST></EVENT_POID_LIST>
                <ACCOUNT_OBJ>0.0.0.1 /account 6048947 0</ACCOUNT_OBJ>
                <BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 0</BILLINFO_OBJ>
                <AR_BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 2</AR_BILLINFO_OBJ>
                <BILL_OBJ>0.0.0.1 /bill 6049459 0</BILL_OBJ>
                <EFFECTIVE_T>1564252200</EFFECTIVE_T>
                <CREATED_T>1566821850</CREATED_T>
                <ITEM_OBJ>0.0.0.1 /item/telephony 6049715 0</ITEM_OBJ>
            </AR_ITEMS>
            <AR_ITEMS elem="0">
                <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/telephony 6048691 0</SERVICE_OBJ>
                <ITEM_NO>B1-4083,4</ITEM_NO>
                <NAME>Cycle forward</NAME>
                <ITEM_TOTAL>402</ITEM_TOTAL>
                <DUE_T>1566844200</DUE_T>
                <DUE>402</DUE>
                <DISPUTED>0</DISPUTED>
                <EVENT_POID_LIST></EVENT_POID_LIST>
                <ACCOUNT_OBJ>0.0.0.1 /account 6048947 4</ACCOUNT_OBJ>
                <BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 0</BILLINFO_OBJ>
                <AR_BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 0</AR_BILLINFO_OBJ>
                <BILL_OBJ>0.0.0.1 /bill 6049459 0</BILL_OBJ>
                <EFFECTIVE_T>1564252200</EFFECTIVE_T>
                <CREATED_T>1566821851</CREATED_T>
                <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 2</ITEM_OBJ>
                <EVENTS elem="0">
                    <END_T>1561660200</END_T>
                    <START_T>1561660200</START_T>
                    <CREATED_T>1566821852</CREATED_T>
                    <NET_QUANTITY>1</NET_QUANTITY>
                    <SYS_DESCR>Cycle Forward Fees (srvc): Voice_Usage</SYS_DESCR>
                    <RERATE_OBJ>0.0.0.0  0 0</RERATE_OBJ>
                    <SESSION_OBJ>0.0.0.1 /event/session 319016701735483447 0</SESSION_OBJ>
                    <TIMEZONE_ADJ_END_T>1566821852</TIMEZONE_ADJ_END_T>
                    <RATED_TIMEZONE_ID>IST</RATED_TIMEZONE_ID>
                    <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 0</ITEM_OBJ>
                    <EVENT_OBJ>0.0.0.1 /event/billing/product/fee/cycle/cycle_forward_monthly 319016701735488243 0</EVENT_OBJ>
                    <BAL_IMPACTS elem="0">
                        <RESOURCE_ID>1000010</RESOURCE_ID>
                        <QUANTITY>1</QUANTITY>
                        <RATE_TAG>Rate 1</RATE_TAG>
                        <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 0</ITEM_OBJ>
                        <AMOUNT>-100</AMOUNT>
                        <IMPACT_TYPE>1</IMPACT_TYPE>
                        <DISCOUNT>0</DISCOUNT>
                        <TAX_CODE></TAX_CODE>
                    </BAL_IMPACTS>
                    <TOTAL elem="1000010">
                        <AMOUNT>-100</AMOUNT>
                    </TOTAL>
                    <LABEL>Rate 1</LABEL>
                </EVENTS>
                <EVENTS elem="1">
                    <END_T>1564252200</END_T>
                    <START_T>1564252200</START_T>
                    <CREATED_T>1566821852</CREATED_T>
                    <NET_QUANTITY>1</NET_QUANTITY>
                    <SYS_DESCR>Cycle Forward Fees (srvc): Voice_Usage</SYS_DESCR>
                    <RERATE_OBJ>0.0.0.0  0 0</RERATE_OBJ>
                    <SESSION_OBJ>0.0.0.1 /event/session 319016701735483447 0</SESSION_OBJ>
                    <TIMEZONE_ADJ_END_T>1566821852</TIMEZONE_ADJ_END_T>
                    <RATED_TIMEZONE_ID>IST</RATED_TIMEZONE_ID>
                    <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 0</ITEM_OBJ>
                    <EVENT_OBJ>0.0.0.1 /event/billing/product/fee/cycle/cycle_forward_monthly 319016701735486323 0</EVENT_OBJ>
                    <BAL_IMPACTS elem="0">
                        <RESOURCE_ID>1000010</RESOURCE_ID>
                        <QUANTITY>1</QUANTITY>
                        <RATE_TAG>Rate 1</RATE_TAG>
                        <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 0</ITEM_OBJ>
                        <AMOUNT>-100</AMOUNT>
                        <IMPACT_TYPE>1</IMPACT_TYPE>
                        <DISCOUNT>0</DISCOUNT>
                        <TAX_CODE></TAX_CODE>
                    </BAL_IMPACTS>
                    <TOTAL elem="1000010">
                        <AMOUNT>-100</AMOUNT>
                    </TOTAL>
                    <LABEL>Rate 1</LABEL>
                </EVENTS>
                <EVENTS elem="2">
                    <END_T>1564252200</END_T>
                    <START_T>1564252200</START_T>
                    <CREATED_T>1566821851</CREATED_T>
                    <NET_QUANTITY>1</NET_QUANTITY>
                    <SYS_DESCR>Cycle Forward Fees (srvc): Voice_Recurring</SYS_DESCR>
                    <RERATE_OBJ>0.0.0.0  0 0</RERATE_OBJ>
                    <SESSION_OBJ>0.0.0.1 /event/session 319016701735483447 0</SESSION_OBJ>
                    <TIMEZONE_ADJ_END_T>1566821851</TIMEZONE_ADJ_END_T>
                    <RATED_TIMEZONE_ID>IST</RATED_TIMEZONE_ID>
                    <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 0</ITEM_OBJ>
                    <EVENT_OBJ>0.0.0.1 /event/billing/product/fee/cycle/cycle_forward_monthly 319016701735487859 0</EVENT_OBJ>
                    <BAL_IMPACTS elem="0">
                        <RESOURCE_ID>840</RESOURCE_ID>
                        <QUANTITY>1</QUANTITY>
                        <RATE_TAG>Rate 1</RATE_TAG>
                        <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 0</ITEM_OBJ>
                        <AMOUNT>201</AMOUNT>
                        <IMPACT_TYPE>1</IMPACT_TYPE>
                        <DISCOUNT>0</DISCOUNT>
                        <TAX_CODE></TAX_CODE>
                    </BAL_IMPACTS>
                    <TOTAL elem="840">
                        <AMOUNT>201</AMOUNT>
                    </TOTAL>
                    <LABEL>Rate 1</LABEL>
                </EVENTS>
                <EVENTS elem="3">
                    <END_T>1561660200</END_T>
                    <START_T>1561660200</START_T>
                    <CREATED_T>1566821851</CREATED_T>
                    <NET_QUANTITY>1</NET_QUANTITY>
                    <SYS_DESCR>Cycle Forward Fees (srvc): Voice_Usage</SYS_DESCR>
                    <RERATE_OBJ>0.0.0.0  0 0</RERATE_OBJ>
                    <SESSION_OBJ>0.0.0.1 /event/session 319016701735483447 0</SESSION_OBJ>
                    <TIMEZONE_ADJ_END_T>1566821851</TIMEZONE_ADJ_END_T>
                    <RATED_TIMEZONE_ID>IST</RATED_TIMEZONE_ID>
                    <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 0</ITEM_OBJ>
                    <EVENT_OBJ>0.0.0.1 /event/billing/product/fee/cycle/cycle_forward_monthly 319016701735489139 0</EVENT_OBJ>
                    <BAL_IMPACTS elem="0">
                        <RESOURCE_ID>1000010</RESOURCE_ID>
                        <QUANTITY>1</QUANTITY>
                        <RATE_TAG>Rate 1</RATE_TAG>
                        <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 0</ITEM_OBJ>
                        <AMOUNT>-100</AMOUNT>
                        <IMPACT_TYPE>1</IMPACT_TYPE>
                        <DISCOUNT>0</DISCOUNT>
                        <TAX_CODE></TAX_CODE>
                    </BAL_IMPACTS>
                    <TOTAL elem="1000010">
                        <AMOUNT>-100</AMOUNT>
                    </TOTAL>
                    <LABEL>Rate 1</LABEL>
                </EVENTS>
                <EVENTS elem="4">
                    <END_T>1561660200</END_T>
                    <START_T>1561660200</START_T>
                    <CREATED_T>1566821851</CREATED_T>
                    <NET_QUANTITY>1</NET_QUANTITY>
                    <SYS_DESCR>Cycle Forward Fees (srvc): Voice_Recurring</SYS_DESCR>
                    <RERATE_OBJ>0.0.0.0  0 0</RERATE_OBJ>
                    <SESSION_OBJ>0.0.0.1 /event/session 319016701735483447 0</SESSION_OBJ>
                    <TIMEZONE_ADJ_END_T>1566821851</TIMEZONE_ADJ_END_T>
                    <RATED_TIMEZONE_ID>IST</RATED_TIMEZONE_ID>
                    <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 0</ITEM_OBJ>
                    <EVENT_OBJ>0.0.0.1 /event/billing/product/fee/cycle/cycle_forward_monthly 319016701735486579 0</EVENT_OBJ>
                    <BAL_IMPACTS elem="0">
                        <RESOURCE_ID>840</RESOURCE_ID>
                        <QUANTITY>1</QUANTITY>
                        <RATE_TAG>Rate 1</RATE_TAG>
                        <ITEM_OBJ>0.0.0.1 /item/cycle_forward 6047859 0</ITEM_OBJ>
                        <AMOUNT>201</AMOUNT>
                        <IMPACT_TYPE>1</IMPACT_TYPE>
                        <DISCOUNT>0</DISCOUNT>
                        <TAX_CODE></TAX_CODE>
                    </BAL_IMPACTS>
                    <TOTAL elem="840">
                        <AMOUNT>201</AMOUNT>
                    </TOTAL>
                    <LABEL>Rate 1</LABEL>
                </EVENTS>
            </AR_ITEMS>
            <TAX_INFO>
                <REALTIME_TAX_AMOUNT>0</REALTIME_TAX_AMOUNT>
                <DEFERRED_TAX_AMOUNT>0</DEFERRED_TAX_AMOUNT>
                <AMOUNT_ADJUSTED>0</AMOUNT_ADJUSTED>
                <TOTALS>402</TOTALS>
                <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/telephony 6048691 0</SERVICE_OBJ>
            </TAX_INFO>
            <BALANCE_GROUPS elem="0">
                <POID>0.0.0.1 /balance_group 6048179 13</POID>
                <ACCOUNT_OBJ>0.0.0.1 /account 6048947 0</ACCOUNT_OBJ>
                <BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 0</BILLINFO_OBJ>
                <EFFECTIVE_T>1561706387</EFFECTIVE_T>
                <BALANCES elem="840">
                    <RESERVED_AMOUNT>0</RESERVED_AMOUNT>
                    <CONSUMED_RESERVED_AMOUNT>0</CONSUMED_RESERVED_AMOUNT>
                    <NEXT_BAL>0</NEXT_BAL>
                    <CREDIT_PROFILE>0</CREDIT_PROFILE>
                    <CONSUMPTION_RULE>0</CONSUMPTION_RULE>
                    <CURRENT_BAL>904</CURRENT_BAL>
                    <CREDIT_FLOOR>NULL</CREDIT_FLOOR>
                    <CREDIT_LIMIT>NULL</CREDIT_LIMIT>
                    <CREDIT_THRESHOLDS>0</CREDIT_THRESHOLDS>
                    <CREDIT_THRESHOLDS_FIXED></CREDIT_THRESHOLDS_FIXED>
                    <NAME>US Dollar</NAME>
                </BALANCES>
                <REALTIME_CNTR>12</REALTIME_CNTR>
                <BALANCES elem="1000009">
                    <RESERVED_AMOUNT>0</RESERVED_AMOUNT>
                    <CONSUMED_RESERVED_AMOUNT>0</CONSUMED_RESERVED_AMOUNT>
                    <NEXT_BAL>0</NEXT_BAL>
                    <CREDIT_PROFILE>2</CREDIT_PROFILE>
                    <CONSUMPTION_RULE>0</CONSUMPTION_RULE>
                    <CURRENT_BAL>-500</CURRENT_BAL>
                    <CREDIT_FLOOR>NULL</CREDIT_FLOOR>
                    <CREDIT_LIMIT>0</CREDIT_LIMIT>
                    <CREDIT_THRESHOLDS>0</CREDIT_THRESHOLDS>
                    <CREDIT_THRESHOLDS_FIXED></CREDIT_THRESHOLDS_FIXED>
                    <NAME>MB Used</NAME>
                </BALANCES>
                <BALANCES elem="1000010">
                    <RESERVED_AMOUNT>0</RESERVED_AMOUNT>
                    <CONSUMED_RESERVED_AMOUNT>0</CONSUMED_RESERVED_AMOUNT>
                    <NEXT_BAL>0</NEXT_BAL>
                    <CREDIT_PROFILE>2</CREDIT_PROFILE>
                    <CONSUMPTION_RULE>0</CONSUMPTION_RULE>
                    <CURRENT_BAL>-100</CURRENT_BAL>
                    <CREDIT_FLOOR>NULL</CREDIT_FLOOR>
                    <CREDIT_LIMIT>0</CREDIT_LIMIT>
                    <CREDIT_THRESHOLDS>0</CREDIT_THRESHOLDS>
                    <CREDIT_THRESHOLDS_FIXED></CREDIT_THRESHOLDS_FIXED>
                    <NAME>Free Domestic Minutes</NAME>
                </BALANCES>
                <BALANCES elem="1000103">
                    <RESERVED_AMOUNT>0</RESERVED_AMOUNT>
                    <CONSUMED_RESERVED_AMOUNT>0</CONSUMED_RESERVED_AMOUNT>
                    <NEXT_BAL>0</NEXT_BAL>
                    <CREDIT_PROFILE>2</CREDIT_PROFILE>
                    <CONSUMPTION_RULE>0</CONSUMPTION_RULE>
                    <CURRENT_BAL>-50</CURRENT_BAL>
                    <CREDIT_FLOOR>NULL</CREDIT_FLOOR>
                    <CREDIT_LIMIT>0</CREDIT_LIMIT>
                    <CREDIT_THRESHOLDS>0</CREDIT_THRESHOLDS>
                    <CREDIT_THRESHOLDS_FIXED></CREDIT_THRESHOLDS_FIXED>
                    <NAME>Short Message Service</NAME>
                </BALANCES>
            </BALANCE_GROUPS>
        </SERVICES>
        <ACCOUNT_NO>ACC51821</ACCOUNT_NO>
    </DEVICES>
    <DEVICES elem="2">
        <DEVICE_ID>No Device</DEVICE_ID>
        <ACCOUNT_OBJ>0.0.0.1 /account 6048947 0</ACCOUNT_OBJ>
        <SERVICES elem="0">
            <SERVICE_OBJ>0.0.0.0  0 0</SERVICE_OBJ>
            <ACCOUNT_OBJ>0.0.0.1 /account 6048947 0</ACCOUNT_OBJ>
            <AR_ITEMS elem="1">
                <SERVICE_OBJ>0.0.0.0  0 0</SERVICE_OBJ>
                <ITEM_NO>B1-4083,1</ITEM_NO>
                <NAME>Usage</NAME>
                <ITEM_TOTAL>0</ITEM_TOTAL>
                <DUE_T>1566844200</DUE_T>
                <DUE>0</DUE>
                <DISPUTED>0</DISPUTED>
                <EVENT_POID_LIST></EVENT_POID_LIST>
                <ACCOUNT_OBJ>0.0.0.1 /account 6048947 0</ACCOUNT_OBJ>
                <BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 0</BILLINFO_OBJ>
                <AR_BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 0</AR_BILLINFO_OBJ>
                <BILL_OBJ>0.0.0.1 /bill 6049459 0</BILL_OBJ>
                <EFFECTIVE_T>1564252200</EFFECTIVE_T>
                <CREATED_T>1566821850</CREATED_T>
                <ITEM_OBJ>0.0.0.1 /item/misc 6047155 0</ITEM_OBJ>
            </AR_ITEMS>
            <TAX_INFO>
                <REALTIME_TAX_AMOUNT>0</REALTIME_TAX_AMOUNT>
                <DEFERRED_TAX_AMOUNT>0</DEFERRED_TAX_AMOUNT>
                <AMOUNT_ADJUSTED>0</AMOUNT_ADJUSTED>
                <TOTALS>0</TOTALS>
                <SERVICE_OBJ>0.0.0.0  0 0</SERVICE_OBJ>
            </TAX_INFO>
            <BALANCE_GROUPS elem="0">
                <POID>0.0.0.1 /balance_group 6048179 13</POID>
                <ACCOUNT_OBJ>0.0.0.1 /account 6048947 0</ACCOUNT_OBJ>
                <BILLINFO_OBJ>0.0.0.1 /billinfo 6047411 0</BILLINFO_OBJ>
                <EFFECTIVE_T>1561706387</EFFECTIVE_T>
                <BALANCES elem="840">
                    <RESERVED_AMOUNT>0</RESERVED_AMOUNT>
                    <CONSUMED_RESERVED_AMOUNT>0</CONSUMED_RESERVED_AMOUNT>
                    <NEXT_BAL>0</NEXT_BAL>
                    <CREDIT_PROFILE>0</CREDIT_PROFILE>
                    <CONSUMPTION_RULE>0</CONSUMPTION_RULE>
                    <CURRENT_BAL>904</CURRENT_BAL>
                    <CREDIT_FLOOR>NULL</CREDIT_FLOOR>
                    <CREDIT_LIMIT>NULL</CREDIT_LIMIT>
                    <CREDIT_THRESHOLDS>0</CREDIT_THRESHOLDS>
                    <CREDIT_THRESHOLDS_FIXED></CREDIT_THRESHOLDS_FIXED>
                    <NAME>US Dollar</NAME>
                </BALANCES>
                <REALTIME_CNTR>12</REALTIME_CNTR>
                <BALANCES elem="1000009">
                    <RESERVED_AMOUNT>0</RESERVED_AMOUNT>
                    <CONSUMED_RESERVED_AMOUNT>0</CONSUMED_RESERVED_AMOUNT>
                    <NEXT_BAL>0</NEXT_BAL>
                    <CREDIT_PROFILE>2</CREDIT_PROFILE>
                    <CONSUMPTION_RULE>0</CONSUMPTION_RULE>
                    <CURRENT_BAL>-500</CURRENT_BAL>
                    <CREDIT_FLOOR>NULL</CREDIT_FLOOR>
                    <CREDIT_LIMIT>0</CREDIT_LIMIT>
                    <CREDIT_THRESHOLDS>0</CREDIT_THRESHOLDS>
                    <CREDIT_THRESHOLDS_FIXED></CREDIT_THRESHOLDS_FIXED>
                    <NAME>MB Used</NAME>
                </BALANCES>
                <BALANCES elem="1000010">
                    <RESERVED_AMOUNT>0</RESERVED_AMOUNT>
                    <CONSUMED_RESERVED_AMOUNT>0</CONSUMED_RESERVED_AMOUNT>
                    <NEXT_BAL>0</NEXT_BAL>
                    <CREDIT_PROFILE>2</CREDIT_PROFILE>
                    <CONSUMPTION_RULE>0</CONSUMPTION_RULE>
                    <CURRENT_BAL>-100</CURRENT_BAL>
                    <CREDIT_FLOOR>NULL</CREDIT_FLOOR>
                    <CREDIT_LIMIT>0</CREDIT_LIMIT>
                    <CREDIT_THRESHOLDS>0</CREDIT_THRESHOLDS>
                    <CREDIT_THRESHOLDS_FIXED></CREDIT_THRESHOLDS_FIXED>
                    <NAME>Free Domestic Minutes</NAME>
                </BALANCES>
                <BALANCES elem="1000103">
                    <RESERVED_AMOUNT>0</RESERVED_AMOUNT>
                    <CONSUMED_RESERVED_AMOUNT>0</CONSUMED_RESERVED_AMOUNT>
                    <NEXT_BAL>0</NEXT_BAL>
                    <CREDIT_PROFILE>2</CREDIT_PROFILE>
                    <CONSUMPTION_RULE>0</CONSUMPTION_RULE>
                    <CURRENT_BAL>-50</CURRENT_BAL>
                    <CREDIT_FLOOR>NULL</CREDIT_FLOOR>
                    <CREDIT_LIMIT>0</CREDIT_LIMIT>
                    <CREDIT_THRESHOLDS>0</CREDIT_THRESHOLDS>
                    <CREDIT_THRESHOLDS_FIXED></CREDIT_THRESHOLDS_FIXED>
                    <NAME>Short Message Service</NAME>
                </BALANCES>
            </BALANCE_GROUPS>
        </SERVICES>
        <ACCOUNT_NO>ACC51821</ACCOUNT_NO>
    </DEVICES>
    <FIELD elem="0">
        <ACCOUNT_OBJ>0.0.0.1 /account 6048947 8</ACCOUNT_OBJ>
        <RATE_PLAN_NAME>N/A</RATE_PLAN_NAME>
        <DEAL_NAME>N/A</DEAL_NAME>
        <PRODUCT_NAME>Data Recurring</PRODUCT_NAME>
        <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/data 6046475 0</SERVICE_OBJ>
    </FIELD>
    <FIELD elem="1">
        <ACCOUNT_OBJ>0.0.0.1 /account 6048947 8</ACCOUNT_OBJ>
        <RATE_PLAN_NAME>N/A</RATE_PLAN_NAME>
        <DEAL_NAME>N/A</DEAL_NAME>
        <PRODUCT_NAME>Voice_Recurring</PRODUCT_NAME>
        <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/telephony 6048691 0</SERVICE_OBJ>
    </FIELD>
    <FIELD elem="2">
        <ACCOUNT_OBJ>0.0.0.1 /account 6048947 8</ACCOUNT_OBJ>
        <RATE_PLAN_NAME>N/A</RATE_PLAN_NAME>
        <DEAL_NAME>N/A</DEAL_NAME>
        <PRODUCT_NAME>SMS_Recurring</PRODUCT_NAME>
        <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/sms 6046195 0</SERVICE_OBJ>
    </FIELD>
    <FIELD elem="3">
        <ACCOUNT_OBJ>0.0.0.1 /account 6048947 8</ACCOUNT_OBJ>
        <RATE_PLAN_NAME>N/A</RATE_PLAN_NAME>
        <DEAL_NAME>N/A</DEAL_NAME>
        <PRODUCT_NAME>Voice_Usage</PRODUCT_NAME>
        <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/telephony 6048691 0</SERVICE_OBJ>
    </FIELD>
    <FIELD elem="4">
        <ACCOUNT_OBJ>0.0.0.1 /account 6048947 8</ACCOUNT_OBJ>
        <RATE_PLAN_NAME>N/A</RATE_PLAN_NAME>
        <DEAL_NAME>N/A</DEAL_NAME>
        <PRODUCT_NAME>SMS_Usage</PRODUCT_NAME>
        <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/sms 6046195 0</SERVICE_OBJ>
    </FIELD>
    <FIELD elem="5">
        <ACCOUNT_OBJ>0.0.0.1 /account 6048947 8</ACCOUNT_OBJ>
        <RATE_PLAN_NAME>N/A</RATE_PLAN_NAME>
        <DEAL_NAME>N/A</DEAL_NAME>
        <PRODUCT_NAME>Data_Usage</PRODUCT_NAME>
        <SERVICE_OBJ>0.0.0.1 /service/telco/gsm/data 6046475 0</SERVICE_OBJ>
    </FIELD>
    <MESSAGE>Trial Invoice</MESSAGE>
    <INV_TYPE>0</INV_TYPE>
</invoice>
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
        "errorMessage": "BRM Error -Bill Number value is incorrect"
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
/brm/v1/invoice/bill/viewbill/{accountNo}
{{% /method-block %}}

This service allows you to fetch the bill details of the customer based on the account number.

It requires accountNo, number of bill, start date, end date, correlationid, srdate, source, operation and destination as input parameters. If successful it will return the bill detailsof the customer. If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **accountNo** (mandatory)    | ``string`` (path) | Provide the account number of which you want to view the balance details. |
| **noOfbill** (optional)    | ``string`` (query) | Provide the bill number. |
| **start** (optional)    | ``string`` (query) | Provide the start date. |
| **end** (optional)    | ``string`` (query) | Provide the end date. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
accountNo:string
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
        "RESULTS": [
          {
            "elem": 0,
            "END_T": 1601058600,
            "START_T": 1598380200,
            "TOTAL_VALUE": 0,
            "DUE": 0,
            "CURRENT_TOTAL": 0,
            "BILL_NO": "B1-33849",
            "DUE_T": 1602700200
          },
          {
            "elem": 1,
            "END_T": 1598380200,
            "START_T": 1595701800,
            "TOTAL_VALUE": 0,
            "DUE": 0,
            "CURRENT_TOTAL": 0,
            "BILL_NO": "B1-33845",
            "DUE_T": 1600108200
          },
          {
            "elem": 2,
            "END_T": 1595701800,
            "START_T": 1593109800,
            "TOTAL_VALUE": 0,
            "DUE": 0,
            "CURRENT_TOTAL": 0,
            "BILL_NO": "B1-33842",
            "DUE_T": 1597257000
          },
          {
            "elem": 3,
            "END_T": 1593109800,
            "START_T": 1590431400,
            "TOTAL_VALUE": 0,
            "DUE": 0,
            "CURRENT_TOTAL": 0,
            "BILL_NO": "B1-33838",
            "DUE_T": 1594837800
          },
          {
            "elem": 4,
            "END_T": 1590431400,
            "START_T": 1587839400,
            "TOTAL_VALUE": 0,
            "DUE": 0,
            "CURRENT_TOTAL": 0,
            "BILL_NO": "B1-33835",
            "DUE_T": 1592159400
          },
          {
            "elem": 5,
            "END_T": 1587839400,
            "START_T": 1585161000,
            "TOTAL_VALUE": 0,
            "DUE": 0,
            "CURRENT_TOTAL": 0,
            "BILL_NO": "B1-33831",
            "DUE_T": 1589394600
          },
          {
            "elem": 6,
            "END_T": 1585161000,
            "START_T": 1582655400,
            "TOTAL_VALUE": 0,
            "DUE": 0,
            "CURRENT_TOTAL": 0,
            "BILL_NO": "B1-33827",
            "DUE_T": 1586889000
          },
          {
            "elem": 7,
            "END_T": 1582655400,
            "START_T": 1579977000,
            "TOTAL_VALUE": 0,
            "DUE": 0,
            "CURRENT_TOTAL": 0,
            "BILL_NO": "B1-33823",
            "DUE_T": 1584383400
          },
          {
            "elem": 8,
            "END_T": 1579977000,
            "START_T": 1577298600,
            "TOTAL_VALUE": 0,
            "DUE": 0,
            "CURRENT_TOTAL": 0,
            "BILL_NO": "B1-33819",
            "DUE_T": 1581532200
          },
          {
            "elem": 9,
            "END_T": 1577298600,
            "START_T": 1574706600,
            "TOTAL_VALUE": 0,
            "DUE": 0,
            "CURRENT_TOTAL": 0,
            "BILL_NO": "B1-33815",
            "DUE_T": 1579026600
          },
          {
            "elem": 10,
            "END_T": 1574706600,
            "START_T": 1573151400,
            "TOTAL_VALUE": 0,
            "DUE": 16,
            "CURRENT_TOTAL": 16,
            "BILL_NO": "B1-8831",
            "DUE_T": 1576434600
          },
          {
            "elem": 11,
            "END_T": 1573151400,
            "START_T": 1570473000,
            "TOTAL_VALUE": 0,
            "DUE": 16,
            "CURRENT_TOTAL": 16,
            "BILL_NO": "B1-8830",
            "DUE_T": 1574879400
          },
          {
            "elem": 12,
            "END_T": 1570473000,
            "START_T": 1567881000,
            "TOTAL_VALUE": 0,
            "DUE": 16,
            "CURRENT_TOTAL": 16,
            "BILL_NO": "B1-8707",
            "DUE_T": 1573065000
          }
        ],
        "SYMBOL": "$",
        "ERROR_NUM": 0,
        "POID": "0.0.0.1 /billinfo 6068550 62"
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
/brm/v1/invoice/bill/serviceUsagedetails/{accountNo}/{accountName}
{{% /method-block %}}

This service allows you to fetch the usage of a customer for a particular account based on account name.

It requires accountNo, account name, start date, end date, correlationid, srdate, source, operation and destination as input parameters. If successful it will return the usage of a particular customer of an account . If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **accountNo** (mandatory)    | ``string`` (path) | Provide the account number of which you want to view the balance details. |
| **accountName** (mandatory)    | ``string`` (path) | Provide the name of the account. |
| **start** (optional)    | ``string`` (query) | Provide the start date. |
| **end** (optional)    | ``string`` (query) | Provide the end date. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - SO-100 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - Inventory |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
accountNo:string
accountName:string
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
        "LOGINS": {
          "elem": 0,
          "MSISDN": 8225001196,
          "SERVICES": [
            {
              "elem": 0,
              "RESULTS": [
                {
                  "elem": 0,
                  "CALLED_TO": "+919211100091",
                  "AMOUNT": 0,
                  "QUANTITY": 300,
                  "CREATED_T": 1566390627
                },
                {
                  "elem": 1,
                  "CALLED_TO": "+919211100091",
                  "AMOUNT": 0,
                  "QUANTITY": 300,
                  "CREATED_T": 1566390644
                },
                {
                  "elem": 2,
                  "CALLED_TO": "+919211100091",
                  "AMOUNT": 0,
                  "QUANTITY": 360,
                  "CREATED_T": 1566390659
                }
              ],
              "SERVICE_OBJ": "0.0.0.1 /service/telco/gsm/telephony 6066374 47"
            },
            {
              "elem": 1,
              "RESULTS": [
                {
                  "elem": 0,
                  "CALLED_TO": "+919211100091",
                  "AMOUNT": 0,
                  "CREATED_T": 1566390844
                },
                {
                  "elem": 1,
                  "CALLED_TO": "+919211100091",
                  "AMOUNT": 0,
                  "CREATED_T": 1566390846
                },
                {
                  "elem": 2,
                  "CALLED_TO": "+919211100091",
                  "AMOUNT": 0,
                  "CREATED_T": 1566390842
                },
                {
                  "elem": 3,
                  "CALLED_TO": "+919211100091",
                  "AMOUNT": 0,
                  "CREATED_T": 1566390845
                }
              ],
              "SERVICE_OBJ": "0.0.0.1 /service/telco/gsm/sms 6068166 49"
            },
            {
              "elem": 2,
              "RESULTS": [
                {
                  "elem": 0,
                  "AMOUNT": 0,
                  "BYTES_IN": 53477376,
                  "BYTES_OUT": 53477376,
                  "CREATED_T": 1566390747
                },
                {
                  "elem": 1,
                  "AMOUNT": 0,
                  "BYTES_IN": 73400320,
                  "BYTES_OUT": 73400320,
                  "CREATED_T": 1566390790
                }
              ],
              "SERVICE_OBJ": "0.0.0.1 /service/telco/gsm/data 6066982 44"
            }
          ]
        },
        "SYMBOL": "$",
        "ERROR_NUM": 0,
        "POID": "0.0.0.1 /account 6067782 30"
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

---
title: "Ticket Services"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "CRM"
weight: 207
toc: false
---

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /crm/v1/ticket/details
{{% /method-block %}}

This service allows you to fetch the list of support tickets of a particular customer.

It requires Token, Correlation ID, SEdated, Operation, Destination, Source as input parameters. If successful the list of tickets will be returned for the requested account. If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header) | Provide the token of the ticket. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - ticketDetail |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid5" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
token:string
correlationId:123e4567-e89b-12d3-a456-426614174000
operation:ticketDetail
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
        "ticket_no": "TT1524",
        "ticketstatus": "Open",
        "description": "ctg hjhg",
        "createdtime": "2020-02-14 18:19:47",
        "ticketcategories": "Request",
        "id": "17x95784"
      },
      {
        "ticket_no": "TT990",
        "ticketstatus": "Open",
        "description": "mobile test",
        "createdtime": "2019-09-13 20:15:40",
        "ticketcategories": "Request",
        "id": "17x82089"
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

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /crm/v1/ticket/issues
{{% /method-block %}}

This service allows you to retrieve the issue type of a customer existing ticket.

It requires token, correlation ID, sedated, operation, destination and source. If successful the issue type of the given ticket will be returned. If failed the appropriate error code will be returned.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header) | Provide the token of the ticket. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - issueTypes |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

{{< tabs "uniqueid9" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
token: string
correlationId:123e4567-e89b-12d3-a456-426614174000
operation:issueTypes
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
      "code": "00000",
      "issueTypes": [
        "General Enquiry",
        "Plan Enquiry"
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
/crm/v1/social/ticket
{{% /method-block %}}

This service is used to create new social media ticket for the customer. It requires correlationId, srdate, source, operation and destination as input parameters.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - create |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **ticketStatus** (mandatory)    | ``string`` (body)      |   Provide the status of the ticket as the value. For example - Open |
| **effectiveDate** (mandatory)    | ``string`` (body)      |   Provide the effective date of the ticket as the value. For example - YYYY-MM-DD |
| **ticketCategories** (mandatory)    | ``string`` (body)      |   Provide the category of the ticket as the value. For example - Plan change |
| **tickettitle** (mandatory)    | ``string`` (body)      |   Provide the title of the ticket as the value. For example - plan change |
| **description** (mandatory)    | ``string`` (body)      |   Provide the description of the ticket as the value. For example - Request for plan change |
| **subcategory** (mandatory)    | ``string`` (body)      |   Provide the sub-category of the ticket as the value. For example - sub1 |
| **status** (mandatory)    | ``string`` (body)      |   Provide the status of the ticket as the value. For example - New |
| **category** (mandatory)    | ``string`` (body)      |   Provide the category of the ticket as the value. For example - cat1 |
| **voucherType** (mandatory)    | ``string`` (body)      |   Provide the type of voucher as the value. |
| **voucherIdFormat** (mandatory)    | ``string`` (body)      |   Provide the format of the voucher as the value. |
| **passwordPattern** (mandatory)    | ``string`` (body)      |   Provide the pattern of the password as the value.  |
| **Source** (mandatory) | ``string`` (body)      |    Provide the source as the value. For example - app |

{{< tabs "uniqueid1" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:123e4567-e89b-12d3-a456-426614174000
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:create
{{< / highlight >}}
{{< /tab >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
"source": "app",
"ticketstatus": "Open",
"effectivedate": "YYYY-MM-DD",
"ticketcategories": "Plan change",
"ticket_title": "Plan change",
"description": "Plan change request for ",
"subcategory": "sub1",
"status": "New",
"category": "cat1",
"vouchertype":"",
"voucheridformat":"",
"passwordpattern":""
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "ticket_no": "TT1130",
      "assigned_user_id": "20x51",
      "parent_id": "",
      "ticketpriorities": "",
      "product_id": "",
      "ticketseverities": "",
      "ticketstatus": "Open",
      "ticketcategories": "Plan change",
      "update_log": "",
      "hours": "",
      "days": "",
      "createdtime": "2020-04-14 17:13:02",
      "modifiedtime": "2020-04-14 17:13:02",
      "modifiedby": "19x5",
      "ticket_title": "Plan change",
      "description": "Plan change request for ",
      "solution": "",
      "contact_id": "12x24218",
      "from_portal": "0",
      "effectivedate": "",
      "subcategory": "0",
      "source": "CRM",
      "starred": "0",
      "tags": "",
      "cf_1518": "",
      "cf_1520": "",
      "cf_1522": "",
      "cf_1524": "",
      "cf_1526": "",
      "internalmemo": "",
      "vendorid": "",
      "vouchertype": "",
      "requiredprefix": "",
      "rechargeinterfaces": "",
      "voucheridformat": "",
      "passwordpattern": "",
      "currencyid": "",
      "id": "17x55954",
      "label": "Plan change"
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
        "errorMessage": "Header 'operation' not present in the request."
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
/crm/v1/ticket/comment
{{% /method-block %}}

This service is allows the user to update comments for a particular ticket. It requires, token, data, correlationId, srdate, source, operation and destination as input parameters. If successful for the given ticket the comment will be added. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header)      |   Provide the token of the ticket as the value. |
| **data** (mandatory)    | ``string`` (header)      |   Provide the comment as the value. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - addTicketComment |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **ticketNo** (mandatory)    | ``string`` (body)      |   Provide the number of the ticket as the value. For example - 10057 |
| **comment** (mandatory)    | ``string`` (body)      |   Provide the comment of the ticket as the value. For example - testing |
| **contactId** (mandatory)    | ``string`` (body)      |   Provide the contact Id of the ticket as the value. For example - 649797 |

{{< tabs "uniqueid2" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:123e4567-e89b-12d3-a456-426614174000
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:addTicketComment
{{< / highlight >}}
{{< /tab >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
  "ticketNo": "10057",
  "comment": "venki testing",
  "contactId": "649797"
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "message": "Comments submitted successfully"
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
        "statusCode": "401",
        "errorCode": "INVALID_TOKEN",
        "errorMessage": "JWT strings must contain exactly 2 period characters. Found: 0"
      }
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

{{% method-block bgcolor="primary" type="bg-green" callmethod="POST" %}}
/crm/v1/ticket
{{% /method-block %}}

This service is allows the user to create a new ticket.

It requires CorrelationId, Token, SR Date, Source, Operation, Destination as input parameters. If successful the new ticket will be created. If failed the appropriate error code will be returned.

<section>

### *Request Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **token** (mandatory)    | ``string`` (header)      |   Provide the token of the ticket as the value. |
| **correlationId** (mandatory)    | ``string`` (header)      |   Provide the correlationId as the value. For example - 123e4567-e89b-12d3-a456-426614174000 |
| **Source** (mandatory) | ``string`` (header)      |    Provide the source as the value. For example - Selfcare |
| **srdate** (mandatory) | ``string`` (header)      |    Provide the date as the value. For example - 11-09-2021 |
| **Operation** (mandatory) | ``string`` (header)      |    Provide the operation as the value. For example - create |
| **destination** (mandatory) | ``string`` (header)      |    Provide the destination as the value. |

### *Request Body Parameters*
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **ticketStatus** (mandatory)    | ``string`` (body)      |   Provide the status of the ticket as the value. For example - Open |
| **effectiveDate** (mandatory)    | ``string`` (body)      |   Provide the effective date of the ticket as the value. For example - YYYY-MM-DD |
| **ticketCategories** (mandatory)    | ``string`` (body)      |   Provide the category of the ticket as the value. For example - Plan change |
| **tickettitle** (mandatory)    | ``string`` (body)      |   Provide the title of the ticket as the value. For example - plan change |
| **description** (mandatory)    | ``string`` (body)      |   Provide the description of the ticket as the value. For example - Request for plan change |
| **subcategory** (mandatory)    | ``string`` (body)      |   Provide the sub-category of the ticket as the value. For example - sub1 |
| **status** (mandatory)    | ``string`` (body)      |   Provide the status of the ticket as the value. For example - New |
| **category** (mandatory)    | ``string`` (body)      |   Provide the category of the ticket as the value. For example - cat1 |
| **voucherType** (mandatory)    | ``string`` (body)      |   Provide the type of voucher as the value. |
| **voucherIdFormat** (mandatory)    | ``string`` (body)      |   Provide the format of the voucher as the value. |
| **passwordPattern** (mandatory)    | ``string`` (body)      |   Provide the pattern of the password as the value.  |
| **Source** (mandatory) | ``string`` (body)      |    Provide the source as the value. For example - app |

{{< tabs "uniqueid3" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
correlationId:123e4567-e89b-12d3-a456-426614174000
srDate:11-09-2021
source:Selfcare
destination:CRM
operation:create
{{< / highlight >}}
{{< /tab >}}
{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
{
"source": "app",
"ticketstatus": "Open",
"effectivedate": "YYYY-MM-DD",
"ticketcategories": "Plan change",
"ticket_title": "Plan change",
"description": "Plan change request for ",
"subcategory": "sub1",
"status": "New",
"category": "cat1",
"vouchertype":"",
"voucheridformat":"",
"passwordpattern":""
}
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "ticket_no": "TT1130",
      "assigned_user_id": "20x51",
      "parent_id": "",
      "ticketpriorities": "",
      "product_id": "",
      "ticketseverities": "",
      "ticketstatus": "Open",
      "ticketcategories": "Plan change",
      "update_log": "",
      "hours": "",
      "days": "",
      "createdtime": "2020-04-14 17:13:02",
      "modifiedtime": "2020-04-14 17:13:02",
      "modifiedby": "19x5",
      "ticket_title": "Plan change",
      "description": "Plan change request for ",
      "solution": "",
      "contact_id": "12x24218",
      "from_portal": "0",
      "effectivedate": "",
      "subcategory": "0",
      "source": "CRM",
      "starred": "0",
      "tags": "",
      "cf_1518": "",
      "cf_1520": "",
      "cf_1522": "",
      "cf_1524": "",
      "cf_1526": "",
      "internalmemo": "",
      "vendorid": "",
      "vouchertype": "",
      "requiredprefix": "",
      "rechargeinterfaces": "",
      "voucheridformat": "",
      "passwordpattern": "",
      "currencyid": "",
      "id": "17x55954",
      "label": "Plan change"
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
        "errorMessage": "Header 'operation' not present in the request."
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

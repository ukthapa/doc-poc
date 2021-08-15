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
toc: true
---

## GET </crm/v1/auth/email>
<section>

The service requires email,correlationId,source,srdate,operation and destination as a input parameters. On success the system will check if the email ID provided while the sign up already exist in the system and on failure the appropriate error code will be returned.

### Response Parameters
| NAME        | TYPE           | DESCRIPTION  |
| ------------- |:-------------:| -----:|
| email      | string (header) | Provide email ID as the value. |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |


{{< tabs "uniqueid" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
### Bad Request
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
{{< tab "Error" >}}
{{< highlight java "linenos=table" >}}
### Downstream error
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
{{< tab "Response Header" >}}
{{< highlight java "linenos=table" >}}

### SUCCESS
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
{{< /tabs >}}
</section>

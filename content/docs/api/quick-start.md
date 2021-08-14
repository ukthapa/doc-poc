---
title: "Quick Start"
description: "One page summary of how to start a new  project."
lead: "One page summary of how to start a new  project."
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "api"
weight: 2
toc: false
---


### TABs
## Example
<section>
## Error
All successful responses are returned with HTTP Status code 200. In case of failure, Razorpay API returns a JSON error response with the parameters that detail the reason for the failure.

### Response Parameters
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |


{{< tabs "uniqueid" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
URL url = new URL("http://example.com");
HttpURLConnection con = (HttpURLConnection) url.openConnection();
con.setRequestMethod("GET");
{{< / highlight >}}
{{< /tab >}}

{{< tab "Request Body" >}}
{{< highlight java "linenos=table" >}}
public class ParameterStringBuilder {
    public static String getParamsString(Map<String, String> params)
      throws UnsupportedEncodingException{
        StringBuilder result = new StringBuilder();
        for (Map.Entry<String, String> entry : params.entrySet()) {
          result.append(URLEncoder.encode(entry.getKey(), "UTF-8"));
          result.append("=");
          result.append(URLEncoder.encode(entry.getValue(), "UTF-8"));
          result.append("&");
        }
        String resultString = result.toString();
        return resultString.length() > 0
          ? resultString.substring(0, resultString.length() - 1)
          : resultString;
    }
}

{{< / highlight >}}
{{< /tab >}}

{{< tab "Response Header" >}}
{{< highlight java "linenos=table" >}}
BufferedReader in = new BufferedReader(
  new InputStreamReader(con.getInputStream()));
  String inputLine;
  StringBuffer content = new StringBuffer();
  while ((inputLine = in.readLine()) != null) {
      content.append(inputLine);
  }
in.close();
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

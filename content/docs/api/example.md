---
title: "Example"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "LS"
weight: 502
toc: false
---

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /forecast/v1/weather
{{% /method-block %}}

This service is used to fetch the weather information's based on latitude and longitude.

It requires latitude and longitude coordinates as input parameters. The service will fetch the weather information for the given longitude and latitude from integrated weather forecast application.

<section>

#### *Request Parameters*
| NAME        | TYPE         | DESCRIPTION  |
|------------- |:-------------:| ----- |
| **lat** (mandatory)    | ``string`` (query) | Provide the latitude as the value. |
| **lon** (mandatory)    | ``string`` (query)      |   Provide the longitude as the value. |
| {{< expand id="testing1" atext="Sometag">}}
<table><thead><tr><th>sdsa</th><th>sasad</th><th>ss</th></tr></thead><tbody><tr><td>sdsa</td><td>sasad</td><td>ss</td></tr></tbody></table>
{{< /expand >}} |
| **units** (optional) | ``string`` (query)      |    Provide the units as the value. |
| {{< expand id="testing2" atext="Someother">}}
<table><thead><tr><th>s2122dsa</th><th>2312213</th><th>2323121</th></tr></thead><tbody><tr><td>sadasdsa</td><td>sadssd</td><td>sasaddsa</td></tr><tr><td>sadasdsa</td><td>sadssd</td><td>sasaddsa</td></tr><tr><td>sadasdsa</td><td>sadssd</td><td>sasaddsa</td></tr><tr><td>sadasdsa</td><td>sadssd</td><td>sasaddsa</td></tr><tr><td>sadasdsa</td><td>sadssd</td><td>sasaddsa</td></tr><tr><td>sadasdsa</td><td>sadssd</td><td>sasaddsa</td></tr><tr><td>sadasdsa</td><td>sadssd</td><td>sasaddsa</td></tr><tr><td>sadasdsa</td><td>sadssd</td><td>sasaddsa</td></tr><tr><td>sadasdsa</td><td>sadssd</td><td>sasaddsa</td></tr></tbody></table>
{{< /expand >}} | string (query) | Description detail content |


{{< tabs "uniqueid" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
lat:string
lon:string
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "visibility": 10000,
      "timezone": 32400,
      "main": {
        "temp": 21.3,
        "feels_like": 21.89,
        "temp_min": 21.29,
        "temp_max": 25.51,
        "pressure": 1013,
        "humidity": 92
      },
      "clouds": {
        "all": 3
      },
      "sys": {
        "type": 2,
        "id": 2019346,
        "country": "JP",
        "sunrise": 1626810299,
        "sunset": 1626861326
      },
      "dt": 1626865943,
      "coord": {
        "lon": 139,
        "lat": 35
      },
      "weather": [
        {
          "id": 800,
          "main": "Clear",
          "description": "clear sky",
          "icon": "01n"
        }
      ],
      "name": "Shuzenji",
      "cod": 200,
      "id": 1851632,
      "base": "stations",
      "wind": {
        "speed": 0.93,
        "deg": 290,
        "gust": 1.3
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
    "success": "false",
    "result": {
      "apiStatus": "ERROR",
      "httpStatus": "BAD_REQUEST",
      "errorCode": 0,
      "message": "400 Bad Request",
      "code": "001"
    }
  }
}
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

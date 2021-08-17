---
title: "Live Services"
description: ""
lead: ""
date: 2020-11-16T13:59:39+01:00
lastmod: 2020-11-16T13:59:39+01:00
draft: false
images: []
menu:
  docs:
    parent: "LS"
weight: 501
toc: false
---

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
  /forecast/v1/weather
{{% /method-block %}}

This service is used to fetch the weather information's based on latitude and longitude.

It requires latitude and longitude coordinates as input parameters. The service will fetch the weather information for the given longitude and latitude from integrated weather forecast application.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **lat** (mandatory)    | ``string`` (query) | Provide the latitude as the value. |
| **lon** (mandatory)    | ``string`` (query)      |   Provide the longitude as the value. |
| **units** (optional) | ``string`` (query)      |    Provide the units as the value. |

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

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
/unibit/v1/finance/{exchangeName}
{{% /method-block %}}

This service is used to fetch the stock exchange information.

It requires exchange name as input parameter. The service will fetch the stock exchange information for the given name.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **exchangeName** (mandatory)    | ``string`` (path) | Provide the name of the exchange as the value. |

{{< tabs "uniqueid1" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
exchangeName:string
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": [
      {
        "ticker": "20MICRONS.NS",
        "companyName": "20 Microns Limited",
        "exchange": "National Stock Exchange of India",
        "exchangeShort": "NSE",
        "currency": "INR",
        "timezone": "Asia/Kolkata"
      },
      {
        "ticker": "21STCENMGM.NS",
        "companyName": "21ST CENTURY MG/SH VTG",
        "exchange": "National Stock Exchange of India",
        "exchangeShort": "NSE",
        "currency": "INR",
        "timezone": "Asia/Kolkata"
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

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
/forecast/v1/weather/{country}/{city}
{{% /method-block %}}

This service is used to fetch the weather forecast based on a specific country and city.

It requires country name, city name and unit as input parameter. The service will return the weather information for a given country and city from a pre integrated weather forecast application.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **country** (mandatory)    | ``string`` (path) | Provide the name of the country as the value. |
| **city** (mandatory)    | ``string`` (path) | Provide the name of the city as the value. |
| **units** (optional)    | ``string`` (query) | Provide the unit as the value. |

{{< tabs "uniqueid3" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
country:India
city:Bangalore
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "rain": {
        "1h": 1.04
      },
      "visibility": 5000,
      "timezone": 19800,
      "main": {
        "temp": 26.97,
        "feels_like": 29.96,
        "temp_min": 26.97,
        "temp_max": 26.97,
        "pressure": 1001,
        "humidity": 83
      },
      "clouds": {
        "all": 90
      },
      "sys": {
        "type": 1,
        "id": 9207,
        "country": "IN",
        "sunrise": 1626826476,
        "sunset": 1626873174
      },
      "dt": 1626865911,
      "coord": {
        "lon": 80.6167,
        "lat": 16.5167
      },
      "weather": [
        {
          "id": 300,
          "main": "Drizzle",
          "description": "light intensity drizzle",
          "icon": "09d"
        },
        {
          "id": 501,
          "main": "Rain",
          "description": "moderate rain",
          "icon": "10d"
        }
      ],
      "name": "Vijayawada",
      "cod": 200,
      "id": 1253184,
      "base": "stations",
      "wind": {
        "speed": 5.14,
        "deg": 260
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

{{% method-block bgcolor="success" type="bg-blue" callmethod="GET" %}}
/news/v1/headlines/{country}
{{% /method-block %}}

This service is used to fetch the latest information from a news source based on the Countr.y

It requires country name and category as input parameters. The service will return the latest headlines and articles from a news source of a particular country based on categories.

<section>

#### *Request Parameters*
| NAME        | TYPE          | DESCRIPTION  |
| ------------- |:-------------:| ----- |
| **country** (mandatory)    | ``string`` (path) | Provide the name of the country as the value. |
| **category** (optional)    | ``string`` (query) | Provide the category of the news as the value. |

{{< tabs "uniqueid4" >}}
{{< tab "Request Header" >}}
{{< highlight java "linenos=table" >}}
country:India
category:Sports
{{< / highlight >}}
{{< /tab >}}
{{< tab "Response" >}}
{{< highlight java "linenos=table" >}}
{
  "response": {
    "success": "true",
    "result": {
      "totalResults": 38,
      "articles": [
        {
          "source": {
            "id": null,
            "name": "NDTV News"
          },
          "author": null,
          "title": "\"No Need To Panic\": AIIMS Chief Says Human-To-Human Bird Flu Transmission Rare - NDTV",
          "description": "As the country reported the first confirmed case of human death due to avian influenza, AIIMS chief Dr Randeep Guleria on Wednesday said that human-to-human transmission of the H5N1 virus is very rare and there is no need to panic.",
          "url": "https://www.ndtv.com/india-news/aiims-chief-randeep-guleria-says-human-to-human-bird-flu-transmission-rare-no-need-to-panic-2491508",
          "urlToImage": "https://c.ndtvimg.com/2021-06/4gdvpero_-aiims-chief-dr-randeep-guleria_625x300_26_June_21.jpg",
          "publishedAt": "2021-07-21T09:58:14Z",
          "content": "Bird flu is usually transmitted to poultry through migratory birds, said AIIMS chief. (File)\r\nNew Delhi: As the country reported the first confirmed case of human death due to avian influenza, AIIMS … [+4082 chars]"
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

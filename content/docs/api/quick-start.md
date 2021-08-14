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
{{< tab "HTML" >}}
{{< highlight html "linenos=table,hl_lines=8 15-17" >}}
  <!DOCTYPE html>
  <title>Title</title>
  <style>body {width: 500px;}</style>
  <script type="application/javascript">
    function $init() {return true;}
  </script>
  <body>
    <p checked class="title" id='title'>Title</p>
    <!-- here goes the rest of the page -->
  </body>
{{< / highlight >}}
{{< /tab >}}

{{< tab "Java" >}}
{{< highlight java "linenos=table,hl_lines=8 15-17" >}}
    public String manipulate(Mode mode) {
        switch(mode) {
        case FOO:
            String result = foo();
            tweak(result);
            return result;
        case BAR:
            String result = bar();  // Compiler error
            twiddle(result);
            return result;
        case BAZ:
            String rsult = bar();   // Whoops, typo!
            twang(result);  // No compiler error
            return result;
        }
    }
{{< / highlight >}}
{{< /tab >}}

{{< tab "Windows" >}}
{{< highlight html "linenos=table,hl_lines=8 15-17" >}}
  <main>
      <article>
          <header>
              <h1>{{.Title}}</h1>
              {{with .Params.subtitle}}
              <span>{{.}}</span>
          </header>
          <div>
              {{.Content}}
          </div>
          <aside>
              {{.TableOfContents}}
          </aside>
      </article>
  </main>
{{< / highlight >}}
{{< /tab >}}
{{< /tabs >}}
</section>

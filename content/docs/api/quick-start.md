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
toc: true
---

### TABs

Tabs let you organize content by context, for example installation instructions for each supported platform.

```tpl
{{</* tabs "uniqueid" */>}}
{{</* tab "macOS" */>}} # macOS Content {{</* /tab */>}}
{{</* tab "Linux" */>}} # Linux Content {{</* /tab */>}}
{{</* tab "Windows" */>}} # Windows Content {{</* /tab */>}}
{{</* /tabs */>}}
```

## Example

{{< tabs "uniqueid" >}}
{{< tab "HTML" >}}

## HTML
{{< btn-copy text="git clone https://github.com/h-enk/doks-child-theme.git my-doks-site" >}}
```bash
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
```
{{< /tab >}}

{{< tab "Java" >}}

## Java

This is tab **Java** content.

Dolor sit, sumo unique argument um no. Gracie nominal id xiv. Romanesque acclimates
investiture. Ornateness bland it ex enc, est yeti am bongo detract re. Pro ad
prompts feud gait, quid exercise emeritus bis e. In pro quints consequent, denim
fastidious copious quo ad. Stet probates in duo.
{{< /tab >}}

{{< tab "Windows" >}}

## Windows

This is tab **Windows** content.

{{< btn-copy text="git clone https://github.com/h-enk/doks-child-theme.git my-doks-site" >}}

```bash
git clone https://github.com/h-enk/doks-child-theme.git my-doks-site
```
{{< /tab >}}
{{< /tabs >}}

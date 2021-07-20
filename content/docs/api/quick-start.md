---
title: "Quick Start"
description: "One page summary of how to start a new Doks project."
lead: "One page summary of how to start a new Doks project."
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

## Requirements

Doks uses npm to centralize dependency management, making it [easy to update] resources, build tooling, plugins, and build scripts:

- Download and install [Node.js](https://nodejs.org/) (it includes npm) for your platform.

## Start a new Doks project

Create a new site, change directories, install dependencies, and start development server.

### Create a new site

Doks is available as a child theme, and a starter theme:

- Use the Doks child theme, if you do __not__ plan to customize a lot, and/or need future Doks updates.
- Use the Doks starter theme, if you plan to customize a lot, and/or do __not__ need future Doks updates.

Not quite sure? Use the Doks child theme.

#### Doks child theme

{{< btn-copy text="git clone https://github.com/h-enk/doks-child-theme.git my-doks-site" >}}

```bash
git clone https://github.com/h-enk/doks-child-theme.git my-doks-site
```

#### Doks starter theme

{{< btn-copy text="git clone https://github.com/h-enk/doks.git my-doks-site" >}}

```bash
git clone https://github.com/h-enk/doks.git my-doks-site
```

### Change directories

{{< btn-copy text="cd my-doks-site" >}}

```bash
cd my-doks-site
```

### Install dependencies

{{< btn-copy text="npm install" >}}

```bash
npm install
```

### Start development server

{{< btn-copy text="npm run start" >}}

```bash
npm run start
```

Doks will start the Hugo development webserver accessible by default at `http://localhost:1313`. Saved changes will live reload in the browser.

## Other commands

Doks comes with commands for common tasks. [Commands →]({{< relref "commands" >}})


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

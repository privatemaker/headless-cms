Headless CMS Hugo Module
========================

- ![Hugo Requirements](https://img.shields.io/badge/dynamic/json?color=important&label=requirements&query=requirements&logo=hugo&style=flat-square&url=https://api.razonyang.com/v1/hugo/modules/github.com/privatemaker/headless-cms)

## Installation

First import the module and append the `HeadlessCMSConfig` to the `home` output 
in your `hugo.yaml` or `config/_default/config.yaml` file.

```
module:
  imports:
  - path: github.com/privatemaker/headless-cms
outputs:
  home:
  - HTML
  - RSS
  - HeadlessCMSConfig
```

Second create file `content/admin/_index.md` with following content:

```
---
title: Your Headless CMS
layout: headless-cms
---
```

You can access it on `/admin` for example, `http://localhost:1313/admin/`

## Configuration

Lastly, in your `hugo.yaml` or `config/_default/params.yaml` file, insert and
edit in your CMS config values.

```
params:
  headless_cms:
    backend:
      name: git-gateway
    collections:
      blog:
        create: true
        fields:
          - label: Title
            name: title
            widget: string
        ...
```

Find the full list of variables for Decap CMS (Sveltia uses same specification) here:

- [Configuation](https://decapcms.org/docs/configuration-options/)
- [Widgets](https://decapcms.org/docs/widgets/)


**Credits**

Based on module code of [decap-cms](https://github.com/hugomods/decap-cms) by Hugomods.

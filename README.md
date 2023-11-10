Headless CMS Hugo Module
========================

- ![Hugo Requirements](https://img.shields.io/badge/dynamic/json?color=important&label=requirements&query=requirements&logo=hugo&style=flat-square&url=https://api.razonyang.com/v1/hugo/modules/github.com/privatemaker/headless-cms)

A Hugo Module for installing the following popular [Headless
CMS](https://en.wikipedia.org/wiki/Headless_CMS) engines:

- [Decap CMS](https://www.decapcms.org)
- [Sveltia CMS](https://github.com/sveltia/sveltia-cms)

## Installation

Assuming your Hugo site is already using [Hugo
Modules](https://gohugo.io/hugo-modules/), then import the module and append the
`HeadlessCMSConfig` to the `home` output in your `hugo.yaml` or
`config/_default/config.yaml` file.

```yaml
module:
  imports:
  - path: github.com/privatemaker/headless-cms

outputs:
  home:
  - HTML
  - RSS
  - HeadlessCMSConfig
```

Next create file `content/admin/_index.md` with following content:

```yaml
---
title: Your Headless CMS
layout: headless-cms
---
```

You can access it on `/admin` for example, `http://localhost:1313/admin/`

## Configuration

Lastly, in the `params:` section of your site's `hugo.yaml` or
`config/_default/params.yaml` file, insert and edit in your CMS config values.

```yaml
params:
  headless_cms:
    engine: "sveltia"
    site_url: "https://your-site.org"
    ...
    backend:
      name: "github"
      repo: "org/repo"
    collections:
      blog:
        create: true
        fields:
          - label: "Title"
            name: "title"
            widget: "string"
        ...
```

The default value of `engine: "sveltia"` to draw attention to the great
project, but if you need more stability and full functionality use `decap` engine.
The full list of config variables for both Decap and Sveltia CMS (the later uses the 
same specification) is here:

- [Configuation](https://decapcms.org/docs/configuration-options/)
- [Widgets](https://decapcms.org/docs/widgets/)

I am happy to receive pull-requests for other Headless CMS engines.

**Credits**

Based on module code of [decap-cms](https://github.com/hugomods/decap-cms) by Hugomods.

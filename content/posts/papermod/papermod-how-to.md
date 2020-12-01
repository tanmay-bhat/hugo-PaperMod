---
title: "Papermod - How To's Guide"
summary: FAQs
date: 2020-09-18T11:30:03+05:30
showtoc: true
tocOpen: true
aliases: ["/papermod-how-to-guide"]
tags: ["PaperMod"]
author: "Aditya Telange"
draft: true
---

## Intro

-   **We'll be using `yml/yaml` format for all examples down below, I recommend using `yml` over `toml` as it is easier to read.**

-   You can find any [YML to TOML](https://www.google.com/search?q=yml+to+toml) converters if necessary.

---

## Override theme template

By Hugo's Lookup Order, you can override any part of a theme that you want. The following is a quick example.

Let's say you wish the `list` was different. All you have to do is copy the `list` template:

```shell
your-site/themes/papermod/layouts/_defaults/list.html
```

And paste it under your own `layouts` folder:

```shell
your-site/layouts/_defaults/list.html
```

Then you're free to make any changes you want to the `list`.
When Hugo builds your site, your copy of `list.html` will be used instead of the theme's `list.html`.

---

## Enable Social-Metadata and SEO

These include OpenGraph, Twitter Cards and Schema.

```yml
params:
    env: production
```

or set `HUGO_ENV` as "production" in system env-vars

---

## Archive Page

```shell
.
├── config.yml
├── content/
│   ├── archives.md   <--- Create archive.md here
│   └── posts/
├── static/
└── themes/
    └── hugo-PaperMod/
```

and add the following to it

```yml
---
title: "Archive"
layout: "archives"
url: "/archives/"
summary: archives
---

```

---

## Custom Head / Footer

Custom css/js can be added by way mentioned below.

```
.(site root)
├── config.yml
├── content/
├── theme/hugo-PaperMod/
└── layouts
    ├── partials
    │   ├── comments.html
    │   ├── extend_footer.html <---
    │   └── extend_head.html   <---
    └── robots.txt
```

Create a html page in directory structure as shown above.

Contents of `extend_head.html` will be added to `head` of page.

and contents of `extend_footer.html` will be added to bottom of page.

---

## Pin a Post

Post can be pinned/ displayed top on the list by adding a `weight=<num>` var to page-variables

example:

```yml
---
title: "My Important post"
date: 2020-09-15T11:30:03+00:00
weight: 1
---

```

```yml
---
title: "My 2nd Important post"
date: 2020-09-15T11:30:03+00:00
weight: 2
---

```

---

## Adding Custom Favicon(s)

We support the following paths under `/static` directory
and can be added accordingly.

-   `favicon.ico`
-   `favicon-16x16.png`
-   `favicon-32x32.png`
-   `apple-touch-icon.png`
-   `safari-pinned-tab.svg`
-   `site.webmanifest`

1. Favicon(s) can be generated by [Favicon.io](https://favicon.io)

    and can be simply put in `/static` folder.

2. Other way is to add favicon(s) NOT located in `/static` folder.

    In site config add the following:

    ```
    params:
    assets:
        favicon: "<link / absolute url>"
        favicon16x16:  "<link / absolute url>"
        favicon32x32:  "<link / absolute url>"
        apple_touch_icon:  "<link / absolute url>"
        safari_pinned_tab:  "<link / absolute url>"
    ```

    - `absolute url` means direct links to external resource: ex. https://web.site/someimage.png

    example:

    ```
    params:
    assets:
        favicon: "/favicon.ico"
        favicon16x16:  "/favicon-16x16.png"
        favicon32x32:  "/favicon-32x32.png"
        apple_touch_icon:  "/apple-touch-icon.png"
        safari_pinned_tab:  "/safari-pinned-tab.svg"
    ```

---

## References

-   [Override a Hugo theme](https://zwbetz.com/override-a-hugo-theme/)
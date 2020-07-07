RTidbits
<a href='https://github.com/arisp99/RTidbits'><img src='logo.png' align="right" height="139" /></a>
================

  - [Package Development](#package-development)
      - [Important Commands](#important-commands)
          - [Package Creation](#package-creation)
          - [CI and Testing](#ci-and-testing)
      - [Websites](#websites)
  - [Badges](#badges)
      - [Commands](#commands)
  - [Logos](#logos)
  - [R Markdown](#r-markdown)
      - [Websites](#websites-1)
  - [Example Yaml Headers](#example-yaml-headers)
      - [HTML](#html)
      - [PrettyDoc](#prettydoc)
      - [PDF](#pdf)
      - [Multiple Outputs](#multiple-outputs)
  - [Figures](#figures)
  - [Misc](#misc)

<!-- Code for website -->

<!-- ```{r, echo = F} -->

<!-- htmltools::img(src = knitr::image_uri("logo.png"),  -->

<!--                alt = 'logo',  -->

<!--                style = 'position:absolute; top:0; right:0; height:130px; padding:10px;') -->

<!-- ``` -->

# Package Development

## Important Commands

### Package Creation

``` r
usethis::create_package()
usethis::use_readme_rmd()
usethis::use_mit_license("Aris Paschalidis")
usethis::use_spell_check()
usethis::use_namespace()
usethis::use_pipe()
usethis::use_lifecycle_badge("Experimental")
```

### CI and Testing

``` r
usethis::use_travis()
usethis::use_testthat()
usethis::use_github_actions()

## Note can add more specific actions using
usethis::use_github_action("check-standard")
```

## Websites

The following list of sites are particularly handy in package
development:

  - [R Packages](http://r-pkgs.had.co.nz/)
  - [Usethis Reference
    Page](https://usethis.r-lib.org/reference/index.html)
  - [Devtools Reference
    Page](https://devtools.r-lib.org/reference/index.html)

# Badges

Badges are written in R Markdown with the following structure:

``` markdown
[![Badge Name]](url to badge image)(url when click on badge)
```

Some examples:

[![Build
Status](https://travis-ci.com/arisp99/CAvaccines.svg?branch=master)](https://travis-ci.com/arisp99/CAvaccines)

<!-- [![R build status](https://github.com/OJWatson/coiaf/workflows/R-CMD-check/badge.svg)](https://github.com/OJWatson/coiaf/actions) -->

[![Lifecycle:
stable](https://img.shields.io/badge/lifecycle-stable-brightgreen.svg)](https://www.tidyverse.org/lifecycle/#stable)

[![License:
MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

The package [`badger`](https://github.com/GuangchuangYu/badger) has a
nice list of badges that can be added.

## Commands

``` r
usethis::use_lifecycle_badge()
usethis::use_travis_badge()
usethis::use_github_actions_badge()
```

# Logos

The package [`hexSticker`](https://github.com/GuangchuangYu/hexSticker)
is very neat for making logos. An example is provided below:

``` r
hexSticker::sticker("logo_background.jpg", package = "RTidbits", filename = "logo.png", 
    s_x = 0.96, s_y = 0.9, s_width = 1.4, p_size = 6.5, p_x = 1, p_y = 1.6, p_color = "#ed7980", 
    h_color = "#f6ca32", h_fill = "#18478c", white_around_sticker = T)
```

The website [TinEye](https://labs.tineye.com/color/) may also come in
handy for color matching.

In order to properly format and store the logo in the right place, the
following may come in handy

``` r
usethis::use_logo("~/Desktop/logo.png")
```

# R Markdown

## Websites

  - [R Markdown Book](https://bookdown.org/yihui/rmarkdown/)
  - [R Markdown Cheat
    Sheet](https://rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf)
  - [Hadley
    Chapter](https://r4ds.had.co.nz/r-markdown.html#introduction-18)
  - [Knitr Options](https://yihui.org/knitr/options/)

# Example Yaml Headers

## HTML

``` yaml
---
html_document:
  highlight: pygments
  toc: true
  toc_float: true
  number_sections: true
---
```

## PrettyDoc

``` yaml
---
prettydoc::html_pretty:
  theme: hpstr
  highlight: vignette
  toc: true
  number_sections: true
---
```

## PDF

``` yaml
---
pdf_document:
  toc: true
  toc_depth: 2
  number_sections: true
---
```

## Multiple Outputs

In order to specifiy multiple outputs, it is as easy as just having both
the html and pdf code above, for example. If however, specific
instructions are not given for one of the outputs, the user must include
`output_type: default`.

If multiple outputs are specified, and the user does not specify which,
the first output will be built. In order to build all the outputs at
once, the following must be used

``` r
rmarkdown::render("path/to/markdown", output_format = "all")
```

# Figures

Figures can be included using the [`knitr`](https://yihui.org/knitr/)
package

``` r
knitr::include_graphics("path/to/image")
```

Note that html documents will not accept pdf files; the image must be a
png file.

# Misc

In order to ensure that documentation is being built with roxygen2, Go
to Tools -\> Project Options -\> Build Tools and check the box that says
“generate documentation with roxygen”

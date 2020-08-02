RTidbits
<a href='https://github.com/arisp99/RTidbits'><img src='logo.png' align="right" height="139" /></a>
================

  - [Package Development](#package-development)
      - [Package Creation](#package-creation)
      - [CI and Testing](#ci-and-testing)
      - [Useful Websites](#useful-websites)
      - [Badges](#badges)
  - [R Markdown](#r-markdown)
      - [Useful Websites](#useful-websites-1)
      - [Yaml Headers](#yaml-headers)
      - [Figures](#figures)
  - [ggplot2](#ggplot2)
      - [Useful Packages and Websites](#useful-packages-and-websites)
      - [Options](#options)
      - [Other Info](#other-info)
  - [Misc](#misc)

<!-- Code for Website -->

<!-- ```{r, echo = F} -->

<!-- htmltools::img(src = knitr::image_uri("logo.png"),  -->

<!--                alt = 'logo',  -->

<!--                style = 'position:absolute; top:0; right:0; height:130px; padding:10px;') -->

<!-- ``` -->

## Package Development

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

# Note can add more specific actions using
usethis::use_github_action("check-standard")
```

### Useful Websites

The following list of sites are particularly handy in package
development:

  - [R Packages](http://r-pkgs.had.co.nz/)
  - [usethis Reference
    Page](https://usethis.r-lib.org/reference/index.html)
  - [devtools Reference
    Page](https://devtools.r-lib.org/reference/index.html)

### Badges

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

Below are several useful functions to automatically add badges.

``` r
usethis::use_lifecycle_badge()
usethis::use_travis_badge()
usethis::use_github_actions_badge()
```

\#\#\#Logos

The package [`hexSticker`](https://github.com/GuangchuangYu/hexSticker)
is very neat for making logos. An example is provided below:

``` r
hexSticker::sticker("logo_background.jpg", package = "RTidbits", 
                    filename = "logo.png", 
                    s_x = 0.96, s_y = 0.9, s_width = 1.4,
                    p_size = 6.5, p_x = 1, p_y = 1.6, p_color = "#ed7980",
                    h_color = "#f6ca32", h_fill = "#18478c", 
                    white_around_sticker = T)
```

The website [TinEye](https://labs.tineye.com/color/) may also come in
handy for color matching.

In order to properly format and store the logo in the right place, the
following may come in handy

``` r
usethis::use_logo("~/Desktop/logo.png")
```

## R Markdown

### Useful Websites

  - [R Markdown Book](https://bookdown.org/yihui/rmarkdown/)
  - [R Markdown Cheat
    Sheet](https://rstudio.com/wp-content/uploads/2015/02/rmarkdown-cheatsheet.pdf)
  - [R For Data Science
    Chapter](https://r4ds.had.co.nz/r-markdown.html#introduction-18)
  - [Knitr Options](https://yihui.org/knitr/options/)

### Yaml Headers

HTML

``` yaml
---
html_document:
  highlight: pygments
  toc: true
  toc_float: true
  number_sections: true
---
```

PrettyDoc

``` yaml
---
prettydoc::html_pretty:
  theme: hpstr
  highlight: vignette
  toc: true
  number_sections: true
---
```

PDF

``` yaml
---
pdf_document:
  toc: true
  toc_depth: 2
  number_sections: true
---
```

In order to specify multiple outputs, it is as easy as just having both
the html and pdf code above, for example. If however, specific
instructions are not given for one of the outputs, the user must include
`output_type: default`.

If multiple outputs are specified, and the user does not specify which,
the first output will be built. In order to build all the outputs at
once, the following must be used

``` r
rmarkdown::render("path/to/markdown", output_format = "all")
```

### Figures

  - Figures can be included using the
    [`knitr`](https://yihui.org/knitr/) package. This technique is neat
    as it allows you to decide whether the image should be included or
    not. For example, you could have the options `eval =
    include_figures` and in the beginning of your markdown file define
    `include_figures` to be `TRUE` or `FALSE`.
    
    ``` r
    knitr::include_graphics("path/to/image")
    ```
    
    Note that html documents will not accept pdf files; the image must
    be a png file.

  - Another method to including figures is to include the figure as part
    of the markdown text You can do this with the following:
    
    ``` markdown
    ![figure name](path/to/figure.png)
    ```

  - Often you may need to rescale or adjust the size of the image. The
    important chunk options are `fig.width` and `fig.height`. For more
    details, see this [useful
    guide](http://zevross.com/blog/2017/06/19/tips-and-tricks-for-working-with-images-and-figures-in-r-markdown-documents/).

## ggplot2

### Useful Packages and Websites

  - [ggplot2 Website](https://ggplot2.tidyverse.org/)
  - [Graph Gallery](https://www.r-graph-gallery.com/index.html) is a
    beautiful website with tons of awesome graphs and demos
  - [ggpubr](https://github.com/kassambara/ggpubr) is a must have for
    publishing images
  - [R Color
    Palettes](https://www.datanovia.com/en/blog/top-r-color-palettes-to-know-for-great-data-visualization/)
  - [ggsci](https://github.com/nanxstats/ggsci) has several very nice
    looking themes
  - [In depth ggplot2
    tutorial](http://r-statistics.co/ggplot2-Tutorial-With-R.html)

### Options

  - My preferred theme settings can be found below
    
    ``` r
    theme_classic() +
    theme(text = element_text(family = "Times New Roman"),
          plot.title = element_text(hjust = 0.5, size = 10),
          axis.title = element_text(size = 7),
          legend.position = "bottom",
          legend.title = element_text(size = 10),
          legend.text = element_text(size = 8)) +
    labs(x = "", y = "", title = "")
    ```

  - The legend can be omitted by adding the following `guides(fill =
    FALSE)`

### Other Info

  - The `viridis` package has a popular and neat color scheme. Colors
    can be added using the `ggplot2` functions:
    `scale_colour_viridis_d()` and `scale_fill_viridis_d()`. `_d` is
    used for discrete, data `_c` is used for continuous data, and `_b`
    is used to give continuous data breaks. See more on the function’s
    [help
    page](https://ggplot2.tidyverse.org/reference/scale_viridis.html).
    Options include limits and breaks as well as the option to change
    between four main color scales: `viridis`, `magma`, `plasma`, and
    `inferno`.

![Viridis Color Scales](figures/viridis_color_scales.png)

  - If you try to specify a specific font in a `ggplot2` object, you may
    get the following error: `Error: font family '<FONT>' not found`. In
    order to get around this, the `extrafont` package can be utilized by
    running:
    
    ``` r
    extrafont::font_import()
    ```

  - The [`plotly`](https://plotly.com/r/) package can be used to make
    interactive graphs. To convert `ggplot2` graphs into interactive
    graphs, the function `ggplotly()` is used.

## Misc

  - In order to ensure that documentation is being built with roxygen2,
    Go to Tools -\> Project Options -\> Build Tools and check the box
    that says “generate documentation with roxygen”

  - There are two progress bars that I have found to be useful and easy
    to work with: [`pbapply`](https://github.com/psolymos/pbapply) and
    [`progress`](https://github.com/r-lib/progress).
    
    The following in some code that checks whether `pbapply` is
    installed. If it is, it will use a progress bar for a `lapply`,
    otherwise, it will use the standard `lapply`.
    
    ``` r
    # Function to determine if pbapply is installed. If it is installed, it will
    # display a progress bar
    list_apply <- function(x, fun, ...){
      if (requireNamespace("pbapply", quietly = TRUE)) {
        pbapply::pblapply(x, fun, ...)
        } else {
        lapply(x, fun, ...)
      }
    }
    ```
    
    Using `progress` is a little more complicated. It utilizes the
    functions `pb$new` and `pb$tick`. An example is below:
    
    ``` r
    pb <- progress::progress_bar$new(format = "working on it [:bar] :percent eta :eta",
                                     complete = "+", clear = F, 
                                     total = length(tt), width = 60)
    
    try <- lapply(tt, function(x) {
      pb$tick()
      tibble::as_tibble(x)
      })
    ```

--- 
title: "DataAtlas"
author: 
- S. Mason Garrison
date: "2024-06-22"
knit: "bookdown::render_book"
site: bookdown::bookdown_site
url: 'https\://R-Computing-Lab/data-atlas'
github-repo: R-Computing-Lab/data-atlas
twitter-handle: smasongarrison
cover-image: assets/logo.png
documentclass: book
bibliography: [book.bib, packages.bib]
biblio-style: apalike
link-citations: yes
description: "Data Atlas"
favicon: assets/favicon.ico
---


# (PART\*) Front Matter {-}

# Abstract {#abstract .unnumbered}

The adage 'A picture is worth a thousand words' is just as applicable to Behavior Genetics as it is to journalism. In this talk, I delve into the rich diverse history of data visualization techniques in the field of behavior genetics, tracing advancements from Wright's [@Wright1920] classic path diagram of guinea pigs to the contemporary usage of Manhattan plots. This survey sets the stage for the development of two resources aimed at bolstering the field's visualization toolkit. The first, an atlas employing 'ggplot2' in R, aims to guide researchers in selecting the most appropriate visualization techniques for their data. The second, a proposed R package, seeks to facilitate the integration of 'OpenMx'-compatible visualizations, streamlining the presentation of complex genetic analyses. Emphasizing practical advice, the talk will cover effective uses of path diagrams, family trees, and interaction visualizations, with the goal of improving clarity and interpretability of genetic data. This initiative aspires to democratize advanced data visualization tools, making them more accessible to the behavior genetics community and, in turn, amplifying the impact and reach of its research.





# Preface {#preface .unnumbered}

In the dynamic field of behavior genetics, the ability to visualize complex data clearly and effectively is not just a technical skill but a narrative art. This document, accompanying the talk on the historical and innovative approaches to data visualization in behavior genetics, introduces the fundamentals of employing ggplot2, a powerful and versatile package in R for creating quality graphics.

`ggplot2` is part of the `tidyverse`, an opinionated collection of `R` packages designed for data science that share an underlying design philosophy, grammar, and data structures. At the heart of `ggplot2` is the concept of a layered grammar of graphics, which allows users to create graphics in a step-by-step, clear and logical way. This framework not only simplifies plotting complex data but also encourages a deeper understanding of the graphical representation itself—making it an ideal tool for behavior geneticists seeking to unvail the hidden stories within their data.

The Data Atlas presented here is designed to serve as a practical guide through the landscape of data visualization techniques specific to the field of behavior genetics. It offers a curated selection of graphical methods that range from the foundational, such as Wright's classic path diagrams, to the advanced, like the interaction visualizations and Manhattan plots, which have become indispensable in the modern geneticist’s toolkit.

Further, this document and the accompanying talk address the development of an innovative R package tailored to integrate with [OpenMx](https://openmx.ssri.psu.edu/) and [BGmisic](https://r-computing-lab.github.io/BGmisc/), projects aimed at facilitating advanced statistical modeling of complex genetic data. This package is proposed to enhance the `ggplot2` environment, making it more conducive to the specialized needs of behavior genetics research—such as the visualization of path diagrams and family trees that are not only informative but are also aesthetically compelling.

As we proceed, this introduction will delve into the specifics of ggplot2 usage in R, demonstrating how this tool can be adapted to meet the unique challenges of visualizing behavioral and genetic data. By bridging the gap between traditional methods and contemporary demands, the resources developed aim to democratize advanced data visualization tools, thereby expanding the accessibility and impact of behavior genetics research.

<!--chapter:end:index.Rmd-->

<!-- front page -->




## How to use these notes {.unnumbered}

To navigate these notes, use the table of contents on the left side of the screen. You can open or close the table of contents using the hamburger icon (horizontal bars) at the top of the document. Additionally, there are other icons at the top of the document for searching within the text, and for adjusting the size, font, or color scheme of the page. The document will be updated unpredictably.


# Attribution {.unnumbered}

These notes lean heavily on other peoples' materials and ideas. I have done my best to document the origin of the materials and ideas. In particular, I have noted people whose work has been a major contribution as well as those who have additional contributions. You can see specific changes by examining the [edit history on the git repo](https://github.com/R-Computing-Lab/data-atlas/commits/main)

## Major Attributions {.unnumbered}

- Jenny Bryan's ([jennybryan.org](https://jennybryan.org)) [STAT 545][stat545] and [Happy Git with R](https://happygitwithr.com/);
- Mason Garrison's PSY 720 [Data Science for Psychologists](https://datascience4psych.github.io/DataScience4Psych/)


# License {#license .unnumbered}

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

<center><i class="fab fa-creative-commons fa-2x"></i><i class="fab fa-creative-commons-by fa-2x"></i><i class="fab fa-creative-commons-sa fa-2x"></i></center>

*This information is a human-readable summary of (and not a substitute for) the license. Please see <https://creativecommons.org/licenses/by-sa/4.0/legalcode> for the full legal text.*

**You are free to:**

- **Share**---copy and redistribute the material in any medium or format

- **Remix**---remix, transform, and build upon the material for any purpose, even commercially.

The licensor cannot revoke these freedoms as long as you follow the license terms.

**Under the following terms:**

- **Attribution**---You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

- **ShareAlike**---If you remix, transform, or build upon the material, you must distribute your contributions under the same license as the original.

- **No additional restrictions**---You may not apply legal terms or technological measures that legally restrict others from doing anything the license permits.

**Notices:**

You do not have to comply with the license for elements of the material in the public domain or where your use is permitted by an applicable exception or limitation.

No warranties are given. The license may not give you all of the permissions necessary for your intended use. For example, other rights such as publicity, privacy, or moral rights may limit how you use the material.





# Colophon {.unnumbered}

These notes was written in [bookdown](http://bookdown.org/) inside [RStudio](http://www.rstudio.com/ide/). The [website][course_web] is hosted with [github](https://www.github.com). The complete source is available from [github][course_git].

The book style was designed by [Desirée De Leon](https://desiree.rbind.io/).

This version of the notes was built with:


```
## Finding R package dependencies ... Done!
```

```
##  setting  value
##  version  R version 4.4.1 (2024-06-14 ucrt)
##  os       Windows 11 x64 (build 22635)
##  system   x86_64, mingw32
##  ui       RTerm
##  language (EN)
##  collate  English_United States.utf8
##  ctype    English_United States.utf8
##  tz       America/New_York
##  date     2024-06-22
##  pandoc   3.1.11 @ C:/Program Files/RStudio/resources/app/bin/quarto/bin/tools/ (via rmarkdown)
```

Along with these packages:


```{=html}
<div class="datatables html-widget html-fill-item" id="htmlwidget-c3f40e2290c7f0da15ff" style="width:100%;height:auto;"></div>
<script type="application/json" data-for="htmlwidget-c3f40e2290c7f0da15ff">{"x":{"filter":"top","vertical":false,"filterHTML":"<tr>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\" disabled=\"\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n<\/tr>","data":[["base64enc","bookdown","bslib","cachem","cli","digest","evaluate","fastmap","fontawesome","fs","glue","highr","htmltools","jquerylib","jsonlite","knitr","lifecycle","memoise","mime","R6","rappdirs","rlang","rmarkdown","sass","tinytex","xfun","yaml"],[null,"0.39","0.7.0","1.1.0","3.6.2","0.6.35","0.23","1.2.0",null,"1.6.4","1.7.0",null,"0.5.8.1","0.1.4","1.8.8","1.46","1.0.4","2.0.1","0.12","2.5.1",null,"1.1.3","2.27","0.4.9",null,"0.44","2.3.8"],["2015-07-28","2024-04-15","2024-03-29","2024-05-16","2023-12-11","2024-03-11","2023-11-01","2024-05-15","2023-08-19","2024-04-25","2024-01-09","2024-05-26","2024-04-04","2021-04-26","2023-12-04","2024-04-06","2023-11-07","2021-11-26","2021-09-28","2021-08-19","2021-01-31","2024-01-10","2024-05-17","2024-03-15","2024-05-06","2024-05-15","2023-12-11"],["CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)"]],"container":"<table class=\"cell-border stripe\">\n  <thead>\n    <tr>\n      <th>package<\/th>\n      <th>loadedversion<\/th>\n      <th>date<\/th>\n      <th>source<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":27,"autoWidth":true,"bInfo":false,"paging":false,"columnDefs":[{"name":"package","targets":0},{"name":"loadedversion","targets":1},{"name":"date","targets":2},{"name":"source","targets":3}],"order":[],"orderClasses":false,"orderCellsTop":true,"lengthMenu":[10,25,27,50,100]},"selection":{"mode":"multiple","selected":null,"target":"row","selectable":null}},"evals":[],"jsHooks":[]}</script>
```



<!--DS4P Links-->
[course_web]: https://R-Computing-Lab.github.io/data-atlas
[course_git]: https://github.com/R-Computing-Lab/data-atlas
[course_repo]: https://github.com/DataScience4Psych
[course_slides]: https://github.com/DataScience4Psych/slides
[course_syllabus]: https://smasongarrison.github.io/syllabi/ 
<!-- https://smasongarrison.github.io/syllabi/data-science.html -->
[syllabi]: https://smasongarrison.github.io/syllabi
[pl_00]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYaEAnJX20Ryy4OSie375rVY
[pl_01]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYao_7t5ycK4KDXNKaY-ECup
[pl_02]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYZmr_T3PnuxjVIlj0C0kUNI
[pl_03]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYaHmjzdRvfg0yhOIYQnfjwE
[pl_04]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYYWFcel6_vp8__RUKLxhX4y
[pl_05]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYYMIguiV1F8RagMYibTY4iW
[pl_06]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYYV_KDod3Mk9-RmtFXii9Dv
[pl_07]: https://www.youtube.com/watch?list=PLKrrdtYgOUYZxvEvQ8-PcWrOY_dwY_ETI
[pl_08]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYZgOzYB_dmauw55M7jXvsdo
[pl_09]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYbaiTmldRY2ddsLrHp3z6yO
[pl_10]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYbPw5iYzYEzoOKa7mJKNIhq
[pl_11]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYZ-u6LzBbanrNFoeLHKaLL6
[pl_12]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYbwRS-9Htmb80_t1NG-021e
[pl_13]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYbWGmSnbLIYwdLOnGm6une6
[pl_14]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYbWGmSnbLIYwdLOnGm6une6
[pl_15]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYa5MoYrV8EsWQ5jIr5ZYMpM
[pl_all]: https://www.youtube.com/playlist?list=PLKrrdtYgOUYZomNqf-1dtCDW94ySdLv-9


<!--AE Links-->
[ae01a_unvotes]: https://github.com/DataScience4Psych/ae01a_unvotes
[ae01b_covid]: https://github.com/DataScience4Psych/ae01b_covid
[ae02_bechdel]: https://github.com/DataScience4Psych/ae-02-bechdel-rmarkdown
[ae03_starwars]: https://github.com/DataScience4Psych/ae-03-starwars-dataviz
[ae08_imdb]: https://github.com/DataScience4Psych/ae-08-imdb-webscraping

<!-- Lab Links-->

[lab01_hello]: https://github.com/DataScience4Psych/lab-01-hello-r
[lab02]: https://github.com/DataScience4Psych/lab-02-plastic-waste
[lab03]: https://github.com/DataScience4Psych/lab-03-nobel-laureates
[lab04]: https://github.com/DataScience4Psych/lab-04-viz-sp-data
[lab05]: https://github.com/DataScience4Psych/lab-05-wrangle-sp-data
[lab06]: https://github.com/DataScience4Psych/lab_06_sad_plots
[lab07]: https://github.com/DataScience4Psych/lab_07_betterviz
[lab08]: https://github.com/DataScience4Psych/lab-08-uoe-art
[lab09]: https://github.com/DataScience4Psych/lab-09-slr-course-evals
[lab10]: https://github.com/DataScience4Psych/lab-10-mlr-course-evals
[lab11]: https://github.com/DataScience4Psych/lab-11-inference-smoking

<!--Slides-->
[d01_welcome]: https://datascience4psych.github.io/slides/d01_welcome/d01_welcome.html
[d02_toolkit]: https://datascience4psych.github.io/slides/d02_toolkit/d02_toolkit.html
[d03_dataviz]: https://datascience4psych.github.io/slides/d03_dataviz/d03_dataviz.html
[d04_ggplot2]: https://datascience4psych.github.io/slides/d04_ggplot2/d04_ggplot2.html
[d05_viznum]: https://datascience4psych.github.io/slides/d05_viznum/d05_viznum.html
[d06_vizcat]: https://datascience4psych.github.io/slides/d06_vizcat/d06_vizcat.html
[d07_tidy]: https://datascience4psych.github.io/slides/d07_tidy/d07_tidy.html
[d08_grammar]: https://datascience4psych.github.io/slides/d08_grammar/d08_grammar.html
[d09_wrangle]: https://datascience4psych.github.io/slides/d09_wrangle/d09_wrangle.html
[d10_dfs]: https://datascience4psych.github.io/slides/d10_dfs/d10_dfs.html
[d11_types]: https://datascience4psych.github.io/slides/d11_types/d11_types.html
[d12_import]: https://datascience4psych.github.io/slides/d12_import/d12_import.html
[d13_goodviz]: https://datascience4psych.github.io/slides/d13_goodviz/d13_goodviz.html
[d13b_moreggplot]: https://datascience4psych.github.io/slides/d13_goodviz/d13b_moreggplot.html
[d14_confound]: https://datascience4psych.github.io/slides/d14_confound/d14_confound.html
[d15_goodtalk]: https://datascience4psych.github.io/slides/d15_goodtalk/d15_goodtalk.html
[d16_webscraping]: https://datascience4psych.github.io/slides/d16_webscraping/d16_webscraping.html
[d17_functions]: https://datascience4psych.github.io/slides/d17_functions/d17_functions.html
[d18_ethics]: https://datascience4psych.github.io/slides/d18_ethics/d18_ethics.html
[d19_bias]: https://datascience4psych.github.io/slides/d19_bias/d19_bias.html


<!--externals-->

[stat545]: https://stat545.com
[r4ds]: https://r4ds.had.co.nz
[cran]: https://cloud.r-project.org

<!--chapter:end:0000_front.Rmd-->

# (PART\*) Introduction {-}

# Crash Course on the Tidyverse

This chapter contains a brief introduction to the `tidyverse` package suite, which is a collection of R packages designed to make data manipulation and visualization easier and more intuitive. The `tidyverse` packages share a common philosophy and syntax, making it easy to learn and use them together. The resulting code is self-documenting, and thus easier to maintain, read, and share, making it ideal for data analysis and visualization. 

This crash course is extremely abridged. For a more in-depth treatment of the `tidyverse`, I recommend checking out my multimedia textbook [Data Science for Psychologists](https://datascience4psych.github.io/DataScience4Psych/) and the [R for Data Science](https://r4ds.had.co.nz/) book by Hadley Wickham and Garrett Grolemund.

## What is the Tidyverse?

The `tidyverse` is a collection of R packages that share a common philosophy and syntax. The packages are designed to work together to make data manipulation and visualization easier and more intuitive. The `tidyverse` includes some of the most popular and widely used R packages, such as `ggplot2`, `dplyr`, `tidyr`, and `readr`. These packages are built on the principles of tidy data, which is a standard way of organizing data that makes it easy to work with.

###  Tidy data

>Happy families are all alike; every unhappy family is unhappy in its own way. 
>
>Leo Tolstoy

Tidy data has the following properties:

1. Each variable forms a column.
2. Each observation forms a row.
3. Each type of observational unit forms a table.

Tidy data is easy to manipulate, visualize, and model, and it is the preferred format for data analysis in the `tidyverse`. The `tidyverse` packages are designed to work with tidy data, and they provide tools and functions that make it easy to transform and visualize data in this format. Untidy data does not have these properties, and it can be more difficult to work with.


## What's the Difference between Base R and the Tidyverse?

There are some key differences between base R and the `tidyverse`. I like to think of them as different dialects. (I'll often say I was raised in based R.) Base R is powerful and flexible, but it can be difficult to learn and use, especially for beginners. The `tidyverse`, on the other hand, is designed to be easy to learn and use, with a consistent syntax and a focus on data manipulation and visualization. The `tidyverse` also includes a number of functions and tools that make common data analysis tasks easier and more intuitive.

Someone who is familiar with base R might notice several key differences when they're introduced to the tidyverse. In my experience the main differences are:

- Syntax and Readability: The tidyverse uses a more consistent and readable syntax that emphasizes clarity and the flow of operations. For example, it leverages the `%>%` pipe operator from the magrittr package extensively, allowing for code to be written in a way that is easy to read from left to right, much like a series of steps.

Pipe operators are used in many programming languages to chain together operations. In R, the pipe operator `%>%` is used to pass the output of one function to the next function as the first argument. This allows you to write code in a way that is easy to read and understand, with each step of the data analysis process clearly laid out. To use the pipe operator, you simply place it between two functions, like this:

```r
output <- function1(input) %>% function2()
```


When these pipes are chained together, they create a clear and readable sequence of operations that can be easily understood by others. This makes it easier to write and maintain code, and it can also help you avoid errors by breaking down complex tasks into smaller, more manageable steps. Here's an example of how the pipe operator can be used to chain together a series of data manipulation operations in the tidyverse:

```r
data %>% 
  filter(condition) %>% 
  select(variables) %>% 
  mutate(new_variable = expression) %>% 
  group_by(grouping_variable) %>% 
  summarize(summary_statistic)
```

Much of the rest of the differences are which functions are used for common tasks. For example:
- Data Manipulation: While base R uses functions like `subset`, `merge`, and `apply`, the tidyverse offers `dplyr` which provides functions like `filter`, `select`, `mutate`, `summarize`, and `join`. These functions are often seen as more intuitive and powerful for data manipulation tasks.

- Data Import and Tidying: Base R provides functions like `read.table` and `read.csv` for data import, and various base functions for data cleaning and reshaping (e.g., `reshape`, `aggregate`). The tidyverse, on the other hand, has `readr` for reading data and `tidyr` for tidying data. The tidying functions, such as gather and spread (now evolved into `pivot_longer` and `pivot_wider`), focus on the concept of "tidy data" where each variable forms a column, each observation forms a row, and each type of observational unit forms a table.

- Handling Factor Variables: In base R, factors are often automatically created when importing data which can lead to unexpected behaviors if not properly managed. The tidyverse's `forcats` package provides tools that make factor management more explicit and less error-prone.

- Functional Programming: Base R uses apply functions like `lapply` and `sapply` for operations on lists or vectors. The tidyverse introduces `purrr` which provides a much needed enhancment for R functional programming with a consistent and coherent set of tools for working with functions and vectors.

Other differences are more subtle but can have a big impact on the user experience, such as how graphics can be handled and how data types are stored:
- Visualization: Base R uses traditional plotting functions such as plot and hist. The tidyverse offers ggplot2, based on the grammar of graphics, which allows for building plots layer by layer and integrates well with the rest of the tidyverse data manipulation packages.

- Data Types and Storage: The tidyverse introduces tibbles via the tibble package, which are modern reimaginings of data frames. Tibbles are data frames but slightly tweaked to work better in the tidyverse; for example, they never change a variable's type when adding rows, don't use row names, and provide a better print method that shows only the first 10 rows and all columns that fit on the screen.

Overall, the tidyverse provides a coherent system of packages that facilitate data manipulation, analysis, and visualization in a way that is generally considered to be more user-friendly, especially for those new to R or programming in general. However, this can also lead to a bit of a learning curve for those deeply entrenched in base R. 


<!--chapter:end:01_intro.Rmd-->

# Introduction to ggplot2



In this chapter, we explore the power of `ggplot2` within the tidyverse package suite for creating compelling visual representations of twin studies in behavior genetics. `ggplot2`'s layer-oriented approach to building data visualizations allows researchers to intuitively map out the complexities inherent in twin data, providing insights that are crucial for both hypothesis testing and exploratory data analysis.

## Understanding ggplot2's Grammar of Graphics

`ggplot2`  is a powerful data visualization package in R that is part of the tidyverse suite of packages. It is based on the grammar of graphics, a coherent system for describing and building visualizations. The grammar of graphics is based on the idea that a plot can be decomposed into a set of independent components, such as data, aesthetics, and geoms (geometric objects). By combining these components, ggplot2 allows for the creation of complex and informative visualizations that can be easily customized and extended.

The structure of the code for plots can be summarized as follows:


``` r
ggplot(data = [[dataset]],
     mapping = aes(x = [[x-variable]],
                   y = [[y-variable]])) +
   geom_xxx() +
   other options
```

Each component of the plot is added in layers. The `ggplot()` function initializes the plot, `aes()` specifies the aesthetic mappings (how variables are mapped to visual properties), and `geom_xxx()` adds a geometric object (points, lines, bars, etc.) to the plot. Additional layers can be added to further customize the plot, such as labels, titles, and themes. We'll dive into these soon enough, but first, let's walk through a simple example to illustrate the basic structure of a ggplot2 plot. 


## Case Study: Visualizing Twin Data

To make this more concrete, let's consider an example using twin data on height from the `OpenMX` package, which is in the `twinData` data. These  3,808 pairs of twins are from the Australian National Health and Medical Research Council Twin Registry. The dataset contains information on the height, weight, and body mass index (BMI) of twins, along with their zygosity and other demographic information.






``` r
library(tidyverse)  # Load the tidyverse packages
library(OpenMx)    # Load the OpenMx package
library(BGmisc) # Load the BGmisc package
library(conflicted) # to handle conflicts
conflicted::conflicts_prefer(OpenMx::vech,dplyr::filter) # Resolve conflicts
```

``` r
data(twinData)
glimpse(twinData)
#> Rows: 3,808
#> Columns: 16
#> $ fam      <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18…
#> $ age      <int> 21, 24, 21, 21, 19, 26, 23, 29, 24, 28, 29, 19, 23, 22, 23, 2…
#> $ zyg      <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
#> $ part     <int> 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2…
#> $ wt1      <int> 58, 54, 55, 66, 50, 60, 65, 40, 60, 76, 48, 70, 51, 53, 58, 4…
#> $ wt2      <int> 57, 53, 50, 76, 48, 60, 65, 39, 57, 64, 51, 67, 51, 55, 57, 5…
#> $ ht1      <dbl> 1.70, 1.63, 1.65, 1.57, 1.61, 1.60, 1.75, 1.56, 1.76, 1.70, 1…
#> $ ht2      <dbl> 1.70, 1.63, 1.68, 1.65, 1.63, 1.57, 1.77, 1.53, 1.77, 1.73, 1…
#> $ htwt1    <dbl> 20.1, 20.3, 20.2, 26.8, 19.3, 23.4, 21.2, 16.4, 19.4, 26.3, 2…
#> $ htwt2    <dbl> 19.7, 19.9, 17.7, 27.9, 18.1, 24.3, 20.7, 16.7, 18.2, 21.4, 2…
#> $ bmi1     <dbl> 21.0, 21.1, 21.0, 23.0, 20.7, 22.1, 21.4, 19.6, 20.7, 22.9, 2…
#> $ bmi2     <dbl> 20.9, 21.0, 20.1, 23.3, 20.3, 22.3, 21.2, 19.7, 20.3, 21.4, 2…
#> $ cohort   <chr> "younger", "younger", "younger", "younger", "younger", "young…
#> $ zygosity <fct> MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, M…
#> $ age1     <int> 21, 24, 21, 21, 19, 26, 23, 29, 24, 28, 29, 19, 23, 22, 23, 2…
#> $ age2     <int> 21, 24, 21, 21, 19, 26, 23, 29, 24, 28, 29, 19, 23, 22, 23, 2…
```

I'm going to tidy up the data a bit by renaming the columns and removing some unnecessary columns. I'll also filter out any rows with missing values in the height columns. I've also added a column to represent the sex of the twins and their zygosity.


``` r
twinData_cleaned <- twinData %>% 
  rename( # Rename columns
    family = fam,
    weight_t1 = wt1,
    weight_t2 = wt2,
    height_t1 = ht1,
    height_t2 = ht2,
    bmi_t1 = bmi1,
    bmi_t2 = bmi2,
    age_t1 = age1,
    age_t2 = age2,
    heightweight_t1 = htwt1,
    heightweight_t2 = htwt2) %>% 
  select(-c(# Remove unnecessary columns
    part,
    zyg,
    age_t1,
    age_t2)) %>% 
  filter(# Remove rows with missing values
    !is.na(height_t1),
    !is.na(height_t2)) %>%
  mutate( # Create new columns
    sex = case_when(zygosity %in% c("MZFF","DZFF") ~ "F", 
                                zygosity %in% c("MZMM","DZMM") ~ "M",
                                TRUE ~ "OS"),
                    zyg = case_when(zygosity %in% c("MZFF","MZMM") ~ "MZ", 
                                    zygosity %in% c("DZFF","DZMM","DZOS") ~ "DZ",
                                TRUE ~ NA_character_ ))

glimpse(twinData_cleaned)
#> Rows: 3,667
#> Columns: 14
#> $ family          <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16,…
#> $ age             <int> 21, 24, 21, 21, 19, 26, 23, 29, 24, 28, 29, 19, 23, 22…
#> $ weight_t1       <int> 58, 54, 55, 66, 50, 60, 65, 40, 60, 76, 48, 70, 51, 53…
#> $ weight_t2       <int> 57, 53, 50, 76, 48, 60, 65, 39, 57, 64, 51, 67, 51, 55…
#> $ height_t1       <dbl> 1.70, 1.63, 1.65, 1.57, 1.61, 1.60, 1.75, 1.56, 1.76, …
#> $ height_t2       <dbl> 1.70, 1.63, 1.68, 1.65, 1.63, 1.57, 1.77, 1.53, 1.77, …
#> $ heightweight_t1 <dbl> 20.1, 20.3, 20.2, 26.8, 19.3, 23.4, 21.2, 16.4, 19.4, …
#> $ heightweight_t2 <dbl> 19.7, 19.9, 17.7, 27.9, 18.1, 24.3, 20.7, 16.7, 18.2, …
#> $ bmi_t1          <dbl> 21.0, 21.1, 21.0, 23.0, 20.7, 22.1, 21.4, 19.6, 20.7, …
#> $ bmi_t2          <dbl> 20.9, 21.0, 20.1, 23.3, 20.3, 22.3, 21.2, 19.7, 20.3, …
#> $ cohort          <chr> "younger", "younger", "younger", "younger", "younger",…
#> $ zygosity        <fct> MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, …
#> $ sex             <chr> "F", "F", "F", "F", "F", "F", "F", "F", "F", "F", "F",…
#> $ zyg             <chr> "MZ", "MZ", "MZ", "MZ", "MZ", "MZ", "MZ", "MZ", "MZ", …
```

The code structure for our plot would look like this:


``` r
ggplot(data = twinData_cleaned, mapping = aes(x = height_t1, 
                                              y = height_t2)) +
  geom_point() +
  labs(title = "Height Comparison between Twins")
```

It would produce a scatter plot comparing the height of twins with the height of twin 1 on the x-axis and the height of twin 2 on the y-axis.

<img src="02_descriptives_files/figure-html/unnamed-chunk-6-1.png" width="70%" />

### Key Components of a ggplot2 Plot

The code above demonstrates the basic structure of a ggplot2 plot. To break down the key components of the plot you can press the left and right arrows on your keyboard to navigate through the slides below. Or if you prefer, you can click on the slide to advance to the next one. Below the slides you'll find the same content in a more traditional format.



```
#> Error in df_url$link: $ operator is invalid for atomic vectors
```


#### Plot Breakdown
**Start with the `twinData_cleaned` data frame**


``` r
ggplot(data = twinData_cleaned) #<<
```

<img src="02_descriptives_files/figure-html/twin-0-1.png" width="70%" />


Start with the `twinData_cleaned` data frame, **map twin 1's height to the x-axis**


``` r
ggplot(data = twinData_cleaned,
       mapping = aes(x = height_t1)) #<<
```

<img src="02_descriptives_files/figure-html/twin-1-1.png" width="70%" />


Start with the `twinData_cleaned` data frame, map twin 1's height to the x-axis, and **and map twin 2's height to the y-axis.**


``` r
ggplot(data = twinData_cleaned,
       mapping = aes( x = height_t1,
                      y = height_t2)) #<<
```

<img src="02_descriptives_files/figure-html/twin-2-1.png" width="70%" />

Start with the `twinData_cleaned` data frame, map twin 1's height to the x-axis, and and map twin 2's height to the y-axis. **Represent each observation with a point**


``` r
ggplot(data = twinData_cleaned,
       mapping = aes( x = height_t1,
                      y = height_t2)) + 
  geom_point() #<<
```

<img src="02_descriptives_files/figure-html/twin-3-1.png" width="70%" />

Start with the `twinData_cleaned` data frame, map twin 1's height to the x-axis, and and map twin 2's height to the y-axis. Represent each observation with a point, **and map zygosity to the color of each point.**


``` r
ggplot(data = twinData_cleaned,
       mapping = aes( x = height_t1,
                      y = height_t2,
                      color = zyg)) + #<<
  geom_point() 
```

<img src="02_descriptives_files/figure-html/twin-4-1.png" width="70%" />

Start with the `twinData_cleaned` data frame, map twin 1's height to the x-axis, and and map twin 2's height to the y-axis. Represent each observation with a point, and map zygosity to the color of each point. **Title the plot "Height Comparison between Twins"**



``` r
ggplot(data = twinData_cleaned,
       mapping = aes( x = height_t1,
                      y = height_t2,
                      color = zyg)) +
  geom_point() +
  labs(title = "Height Comparison between Twins") #<<
```

<img src="02_descriptives_files/figure-html/twin-5-1.png" width="70%" />

Start with the `twinData_cleaned` data frame, map twin 1's height to the x-axis, and and map twin 2's height to the y-axis. Represent each observation with a point, and map zygosity to the color of each point. Title the plot "Height Comparison between Twins", **add the subtitle "by zygosity"**


``` r
ggplot(data = twinData_cleaned,
       mapping = aes( x = height_t1,
                      y = height_t2,
                      color = zyg)) +
  geom_point() +
  labs(title = "Height Comparison between Twins",
       subtitle = "by zygosity") #<<
```

<img src="02_descriptives_files/figure-html/twin-6-1.png" width="70%" />

Start with the `twinData_cleaned` data frame, map twin 1's height to the x-axis, and and map twin 2's height to the y-axis. Represent each observation with a point, and map zygosity to the color of each point. Title the plot "Height Comparison between Twins", add the subtitle "by zygosity", **label the x and y axes as "Height of Twin 1 (m)" and "Height of Twin 2 (m)", respectively**


``` r
ggplot(data = twinData_cleaned,
       mapping = aes( x = height_t1,
                      y = height_t2,
                      color = zyg)) +
  geom_point() +
  labs(title = "Height Comparison between Twins",
       subtitle = "by zygosity",
       x = "Height of Twin 1 (m)", y = "Height of Twin 2 (m)") #<<
```

<img src="02_descriptives_files/figure-html/twin-7-1.png" width="70%" />

Start with the `twinData_cleaned` data frame, map twin 1's height to the x-axis, and and map twin 2's height to the y-axis. Represent each observation with a point, and map zygosity to the color of each point. Title the plot "Height Comparison between Twins", add the subtitle "by zygosity", label the x and y axes as "Height of Twin 1 (m)" and "Height of Twin 2 (m)", respectively , **label the legend "Zygosity"**


``` r
ggplot(data = twinData_cleaned,
       mapping = aes( x = height_t1,
                      y = height_t2,
                      color = zyg)) +
  geom_point() +
  labs(title = "Height Comparison between Twins",
       subtitle = "by zygosity",
       x = "Height of Twin 1 (m)", y = "Height of Twin 2 (m)",
       color = "Zygosity") #<<
```

<img src="02_descriptives_files/figure-html/twin-8-1.png" width="70%" />

Start with the `twinData_cleaned` data frame, map twin 1's height to the x-axis, and and map twin 2's height to the y-axis. Represent each observation with a point, and map zygosity to the color of each point. Title the plot "Height Comparison between Twins", add the subtitle "by zygosity", label the x and y axes as "Height of Twin 1 (m)" and "Height of Twin 2 (m)", respectively , label the legend "Zygosity", and **add a caption for the data source.**


``` r
ggplot(data = twinData_cleaned,
       mapping = aes( x = height_t1,
                      y = height_t2,
                      color = zyg)) +
  geom_point() +
  labs(title = "Height Comparison between Twins",
       subtitle = "by zygosity",
       x = "Height of Twin 1 (m)", y = "Height of Twin 2 (m)",
       color = "Zygosity",
       caption = "Source: Australian National Health and Medical Research Council Twin Registry / OpenMx package") #<<
```

<img src="02_descriptives_files/figure-html/twin-9-1.png" width="70%" />


Start with the `twinData_cleaned` data frame, map twin 1's height to the x-axis, and and map twin 2's height to the y-axis. Represent each observation with a point, and map zygosity to the color of each point. Title the plot "Height Comparison between Twins", add the subtitle "by zygosity", label the x and y axes as "Height of Twin 1 (m)" and "Height of Twin 2 (m)", respectively , label the legend "Zygosity", and add a caption for the data source. **Finally, use a discrete color scale that is designed to be perceived by viewers with common forms of color blindness.**


``` r
ggplot(data = twinData_cleaned,
       mapping = aes( x = height_t1,
                      y = height_t2,
                      color = zyg)) +
  geom_point() +
  labs(title = "Height Comparison between Twins",
       subtitle = "by zygosity",
       x = "Height of Twin 1 (m)", y = "Height of Twin 2 (m)",
       color = "Zygosity",
       caption = "Source: Australian National Health and Medical Research Council Twin Registry / OpenMx package") +
  scale_color_viridis_d() #<<
```

<img src="02_descriptives_files/figure-html/twin-10-1.png" width="70%" />


<!--chapter:end:02_descriptives.Rmd-->

# (PART\*) Descriptive Statistics {-}


# Wide Form Data

Wide form data is a common way to store data, especially when it comes from family data. surveys or experiments where each family has multiple members (twins, siblings etc) In this form, each row represents a family, and each column represents a variable or measurement for a specific family member. This format is easy to understand and work with, but it can be challenging for certain types of analyses or visualizations. In this section, demonstrate straightforward ways to import, summarize, and visualize wide form data using the `twinData` dataset from the `OpenMx` package.

## Import Data

We're going to use the `twinData` dataset from the `OpenMx` package. This dataset contains 3,808 pairs of Australian twins on the 12 variables.




``` r
library(tidyverse)
library(NlsyLinks)
library(discord)
library(BGmisc)
library(OpenMx)
library(conflicted) # to handle conflicts
conflicted::conflicts_prefer(OpenMx::vech,dplyr::filter) # Resolve conflicts


data(twinData)

df_wide <- twinData
```

## Data Structure

Let's take a look at the structure of the dataset using the `class` and `glimpse` functions. 


``` r
class(df_wide)
```

```
## [1] "data.frame"
```

``` r
glimpse(df_wide)
```

```
## Rows: 3,808
## Columns: 16
## $ fam      <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18…
## $ age      <int> 21, 24, 21, 21, 19, 26, 23, 29, 24, 28, 29, 19, 23, 22, 23, 2…
## $ zyg      <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
## $ part     <int> 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2…
## $ wt1      <int> 58, 54, 55, 66, 50, 60, 65, 40, 60, 76, 48, 70, 51, 53, 58, 4…
## $ wt2      <int> 57, 53, 50, 76, 48, 60, 65, 39, 57, 64, 51, 67, 51, 55, 57, 5…
## $ ht1      <dbl> 1.7000, 1.6299, 1.6499, 1.5698, 1.6099, 1.5999, 1.7500, 1.559…
## $ ht2      <dbl> 1.7000, 1.6299, 1.6799, 1.6499, 1.6299, 1.5698, 1.7698, 1.529…
## $ htwt1    <dbl> 20.0692, 20.3244, 20.2020, 26.7759, 19.2894, 23.4375, 21.2245…
## $ htwt2    <dbl> 19.7232, 19.9481, 17.7154, 27.9155, 18.0662, 24.3418, 20.7476…
## $ bmi1     <dbl> 20.9943, 21.0828, 21.0405, 23.0125, 20.7169, 22.0804, 21.3861…
## $ bmi2     <dbl> 20.8726, 20.9519, 20.1210, 23.3043, 20.2583, 22.3454, 21.2270…
## $ cohort   <chr> "younger", "younger", "younger", "younger", "younger", "young…
## $ zygosity <fct> MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, M…
## $ age1     <int> 21, 24, 21, 21, 19, 26, 23, 29, 24, 28, 29, 19, 23, 22, 23, 2…
## $ age2     <int> 21, 24, 21, 21, 19, 26, 23, 29, 24, 28, 29, 19, 23, 22, 23, 2…
```
As we can see, the dataset contains 3808 observations of 16 variables. Most of these variables include two entries, one for twin 1 and one for twin 2. The `zygosity` variable indicates the zygosity of the twins, while other variables represent different measurements or characteristics of the twins, and denote which twin they refer to by the suffixes `1` and `2`.

We can also see that the dataset contains a mix of numeric and character variables. To improve the readability of the dataset, we are going to split the information from the zygosity variable into two separate variables: `sex` and `zyg`. This will make it easier to analyze and visualize the data later on.



``` r
df_wide <- df_wide %>% mutate(sex = 
                      case_when(zygosity %in% c("MZFF","DZFF") ~ "F", 
                                zygosity %in% c("MZMM","DZMM") ~ "M",
                                TRUE ~ "OS"),
                    zyg = case_when(zygosity %in% c("MZFF","MZMM") ~ "MZ", 
                                    zygosity %in% c("DZFF","DZMM","DZOS") ~ "DZ",
                                TRUE ~ NA_character_ ))
```

### Annotated explainaton for the code snippet above:

The provided R code uses the `tidyverse` package's `dplyr` library to manipulate a data frame named `df_wide`. The `mutate` function is used to create new variables or modify existing ones within the data frame. (In this case it is creating `sex` and over writing `zyg`. Here's an annotation of what each part of the code is doing:

1. Data Frame Assignment: `df_wide <- df_wide %>%`

  - This line indicates that we are taking the existing data frame `df_wide` and using the `%>%` operator (pipe) to pass it through additional functions. The result will be stored back into the `df_wide`.

2. Mutate Function: `mutate(sex = ..., zyg = ...)`

  - The `mutate` function is used to add new columns to the data frame or change existing ones. In this case, one new column  `sex` is being added and the existing column `zyg` is being modified.

3. Creating `sex` Column:

- `sex = case_when(...)` creates a new column named sex based on conditions applied to the zygosity column. The case_when function is similar to a series of if-else statements. For each row, it checks the conditions in order and assigns a value to sex based on the first matching condition.

4. Conditions for `sex` Column:

  - `zygosity %in% c("MZFF","DZFF") ~ "F"` condition checks if the `zygosity` value is either "MZFF" or "DZFF". If `true`, "F" (Female) is assigned to the sex column.

  - `zygosity %in% c("MZMM","DZMM") ~ "M"` checks if the zygosity value is either "MZMM" or "DZMM". If true, "M" (Male) is assigned to the sex column.

  - `TRUE ~ "OS"` is a catch-all condition that assigns "OS" (Other or Unknown sex) if none of the above conditions are met.

5. Creating `zyg` Column:

  - Similar to the sex column, `zyg = case_when(...)` overwrites an old column `zyg` that categorizes zygosity into broader categories.

6. Conditions for `zyg` Column:

  - `zygosity %in% c("MZFF","MZMM") ~ "MZ"` checks if zygosity is either "MZFF" or "MZMM" and assigns "MZ" (Monozygotic) indicating identical twins.

  - `zygosity %in% c("DZFF","DZMM","DZOS") ~ "DZ"` checks if zygosity falls into any of "DZFF", "DZMM", or "DZOS", assigning "DZ" (Dizygotic) indicating fraternal twins.

  - `TRUE ~ NA_character_` assigns a missing value (`NA`) if none of the above conditions are met, possibly used to handle cases where zygosity data is not clearly defined or is missing.

This code effectively categorizes individuals in the dataset based on zygosity into more workable groups for sex and twin status, which can (and will) be useful for further analysis and visualization.

## Summary Statistics (Wide Form)

Let's calculate summary statistics for numeric variables across the full sample. This will provide a quick overview of central tendencies and variability in the dataset. When working with wide form data, it is often helpful to start with summarizing by the data structure you already have. In this case, we will calculate summary statistics by specific twin (twin 1 or twin 2).

### Numeric Variables

Calculate summary statistics for numeric variables across the full sample. This helps provide a quick overview of central tendencies and variability.


``` r
# Calculate summary statistics for numeric variables across the full sample
summary_stats <- df_wide %>%
  summarise(across(where(is.numeric), list(
    mean = ~mean(., na.rm = TRUE),
    sd = ~sd(., na.rm = TRUE),
    median = ~median(., na.rm = TRUE),
    min = ~min(., na.rm = TRUE),
    max = ~max(., na.rm = TRUE),
    IQR = ~IQR(., na.rm = TRUE)
  ), .names = "{col}_{fn}")) %>%
  pivot_longer(
    cols = everything(),
    names_to = c("variable", "statistic"),
    names_sep = "_"
  ) %>%
  pivot_wider(
    names_from = statistic,
    values_from = value
  )

summary_stats
```

```
## # A tibble: 13 × 7
##    variable    mean        sd  median   min     max      IQR
##    <chr>      <dbl>     <dbl>   <dbl> <dbl>   <dbl>    <dbl>
##  1 fam      1904.   1099.     1904.    1    3808    1904.   
##  2 age        34.5    14.2      30    17      88      19    
##  3 part        1.93    0.265     2     0       2       0    
##  4 wt1        62.2    10.9      60    34     111      15    
##  5 wt2        65.6    12.2      65    35     127      16    
##  6 ht1         1.66    0.0896    1.65  1.34    1.98    0.130
##  7 ht2         1.69    0.0990    1.7   1.40    1.99    0.140
##  8 htwt1      22.5     3.16     21.9  13.3    41.9     3.84 
##  9 htwt2      22.8     3.19     22.3  14.2    46.2     3.78 
## 10 bmi1       21.7     0.940    21.6  18.1    26.1     1.21 
## 11 bmi2       21.8     0.939    21.7  18.6    26.8     1.18 
## 12 age1       34.5    14.2      30    17      88      19    
## 13 age2       34.5    14.2      30    17      88      19
```

As you can see in the table above, the summary statistics provide a quick overview of the central tendencies and variability in the dataset for numeric variables. The table includes the mean, standard deviation, median, minimum, maximum, and interquartile range (IQR) for each numeric variable. But they do so by the twin number, which is useful for our purposes, but... isn't the only descriptive information we'll need. We will need to calculate these statistics for the full sample, not by twin number. But we'll still going to start with the twin number, and then we'll calculate the summary statistics for the full sample.

### Frequency Tables

Create frequency tables for categorical variables like zygosity and sex, providing a clear picture of the distribution of these categories within the dataset. These numbers are easier to calculation when data are wide like this because we're actually interested in the dyad, not the individual.



``` r
# Counting 'zygosity' and calculating percentages
zygosity_summary <- df_wide %>%
  count(zyg, name = "count") %>%
  mutate(percentage = count / sum(count) * 100) %>%
  rename(category = zyg) %>%  # Renaming the column for clarity
  mutate(variable = "zygosity")  # Adding a descriptor column for the variable

# Counting 'sex' and calculating percentages
sex_summary <- df_wide %>%
  count(sex, name = "count") %>%
  mutate(percentage = count / sum(count) * 100) %>%
  rename(category = sex) %>%  # Renaming the column for clarity
  mutate(variable = "sex")  # Adding a descriptor column for the variable

# Combining both summaries into a single dataframe
combined_summary <- bind_rows(zygosity_summary, sex_summary) %>%
  select(variable, category, everything())  # Reordering columns for clarity

combined_summary
```

```
##   variable category count percentage
## 1 zygosity       DZ  2009   52.75735
## 2 zygosity       MZ  1799   47.24265
## 3      sex        F  1983   52.07458
## 4      sex        M   919   24.13340
## 5      sex       OS   906   23.79202
```
As you can see in the table above, the frequency tables provide a clear picture of the distribution of categories within the dataset for the zygosity and sex. Interestingly, there are many more same sex female twins, which make up 1983/3808 (52%) of the dataset. 

What if you want to examine these wideform by cohort? You can use the `group_by` function to group the data by cohort and then calculate the summary statistics for each cohort.


``` r
library(tidyverse)

# Grouping by 'cohort' and calculating summary statistics for each group across values that are numeric
df_summary <- df_wide %>%
    group_by(cohort) %>%
    summarise(across(where(is.numeric), list(
        mean = ~mean(., na.rm = TRUE),
        sd = ~sd(., na.rm = TRUE),
        median = ~median(., na.rm = TRUE),
        IQR = ~IQR(., na.rm = TRUE)
    ), .names = "{.col}_{.fn}")) %>%
    # Ensure only statistic columns are being pivoted
    pivot_longer(
        cols = -cohort,  # Exclude 'cohort' from pivoting
        names_to = c("variable", "statistic"),
        names_sep = "_"
    )
# lock in the variable order
variable_order <- unique(df_summary$variable)

df_summary <- df_summary  %>% 
    pivot_wider(
        names_from = statistic,
        values_from = value,
        values_fn = list(value = mean)  # Aggregate if necessary
    )

df_summary  %>% mutate(variable = factor(variable, levels = variable_order)) %>%
    arrange(variable, cohort)
```

```
## # A tibble: 26 × 6
##    cohort  variable    mean      sd median   IQR
##    <chr>   <fct>      <dbl>   <dbl>  <dbl> <dbl>
##  1 older   fam      2859    548.      2859   949
##  2 younger fam       955    551.       955   954
##  3 older   age        45.4   12.2       42    19
##  4 younger age        23.5    3.66      23     7
##  5 older   part        1.95   0.224      2     0
##  6 younger part        1.92   0.299      2     0
##  7 older   wt1        63.8   11.2       62    15
##  8 younger wt1        60.5   10.3       59    14
##  9 older   wt2        67.0   12.7       66    19
## 10 younger wt2        64.1   11.6       64    17
## # ℹ 16 more rows
```

As you can see from the table, the summary statistics are calculated for each cohort across the numeric variables. This provides a quick overview of the central tendencies and variability in the dataset for each cohort. Now, these data are still in wide form, but we can easily convert them to long form if needed.

What about descriptive statistics by zygosity and sex?


``` r
library(tidyverse)

# Grouping by 'zyg,sex' and calculating summary statistics for each group
df_summary <- df_wide %>%
    group_by(zyg,sex) %>%
    summarise(across(where(is.numeric), list(
        mean = ~mean(., na.rm = TRUE),
        sd = ~sd(., na.rm = TRUE),
        median = ~median(., na.rm = TRUE),
        IQR = ~IQR(., na.rm = TRUE)
    ), .names = "{.col}_{.fn}")) %>%
    # Ensure only statistic columns are being pivoted
    pivot_longer(
        cols = -c(zyg,sex),  # Exclude 'zygosity' from pivoting
        names_to = c("variable", "statistic"),
        names_sep = "_"
    )
```

```
## `summarise()` has grouped output by 'zyg'. You can override using the `.groups`
## argument.
```

``` r
# lock in the variable order
variable_order <- unique(df_summary$variable)

df_summary <- df_summary  %>% 
    pivot_wider(
        names_from = statistic,
        values_from = value,
        values_fn = list(value = mean)  # Aggregate if necessary
    )

df_summary  %>% mutate(variable = factor(variable, levels = variable_order)) %>%
    arrange(variable,zyg,sex)
```

```
## # A tibble: 65 × 7
## # Groups:   zyg [2]
##    zyg   sex   variable   mean     sd median   IQR
##    <chr> <chr> <fct>     <dbl>  <dbl>  <dbl> <dbl>
##  1 DZ    F     fam      2109.  1029.   2891  2048 
##  2 DZ    M     fam      2144.  1009.   1370. 2042.
##  3 DZ    OS    fam      2509.   980.   1852. 1956.
##  4 MZ    F     fam      1338.   992.   1956. 1956.
##  5 MZ    M     fam      1750.  1010.   2583  2013 
##  6 DZ    F     age        35.4   14.3    32    20 
##  7 DZ    M     age        32.3   13.9    28    16 
##  8 DZ    OS    age        32.9   13.9    28    17 
##  9 MZ    F     age        35.7   14.3    32    21 
## 10 MZ    M     age        34.4   14.1    31    18 
## # ℹ 55 more rows
```

As you can see from the table, the summary statistics are calculated for each zygosity and sex across the 
numeric variables. 

# Wide Form Data Visualization

## 1. Univariate Distributions

### Histograms

Histograms are a great way to visualize the distribution of a single variable. Here, we will create histograms for the weight of twin 1 and twin 2.


#### Histogram of Weight for Twin 1


``` r
ggplot(df_wide, aes(x = wt1)) +
  geom_histogram(bins = 30, fill = "blue", color = "black") +
  labs(x = "Weight of Twin 1", y = "Frequency", title = "Distribution of Weight for Twin 1") +
  theme_minimal()
```

```
## Warning: Removed 97 rows containing non-finite outside the scale range
## (`stat_bin()`).
```

<img src="03_wide_files/figure-html/histogram-twin1-1.png" width="768" />

#### Histogram of Weight for Twin 2 by Zygosity


``` r
ggplot(df_wide, aes(x = wt2)) +
  geom_histogram(bins = 30, fill = "red", color = "black") +
  labs(x = "Weight of Twin 2", y = "Frequency", title = "Distribution of Weight for Twin 2") +
  theme_minimal() + facet_wrap(~zyg)
```

```
## Warning: Removed 86 rows containing non-finite outside the scale range
## (`stat_bin()`).
```

<img src="03_wide_files/figure-html/histogram-twin2-1.png" width="768" />

### Density Plots

**Density Plot of Weight for Twin 1**


``` r
ggplot(df_wide, aes(x = wt1, fill = zyg)) +
  geom_density(alpha = 0.5) +
  labs(x = "Weight of Twin 1", y = "Density", title = "Density Plot of Weight for Twin 1 by Zygosity") +
  scale_fill_viridis_d(option = "viridis", begin = 0.1, end = 0.85) +
  theme_minimal()
```

```
## Warning: Removed 97 rows containing non-finite outside the scale range
## (`stat_density()`).
```

<img src="03_wide_files/figure-html/density-twin1-1.png" width="768" />


**Density Plot of Weight for Twin 2**


``` r
ggplot(df_wide, aes(x = wt2, fill = zyg)) +
  geom_density(alpha = 0.5) +
  labs(x = "Weight of Twin 2", y = "Density", title = "Density Plot of Weight for Twin 2 by Zygosity") +
  scale_fill_viridis_d(option = "viridis", begin = 0.1, end = 0.85) +
  theme_minimal() + facet_wrap(~sex)
```

```
## Warning: Removed 86 rows containing non-finite outside the scale range
## (`stat_density()`).
```

<img src="03_wide_files/figure-html/density-twin2-1.png" width="768" />


### Box Plots

**Box Plot of Weight for Twin 1**


``` r
ggplot(df_wide, aes(x = zyg, y = wt1, fill = zyg)) +
  geom_boxplot() +
  labs(x = "Zygosity", y = "Weight of Twin 1", title = "Box Plot of Weight for Twin 1 by Zygosity") +
  scale_fill_viridis_d(option = "viridis", begin = 0.1, end = 0.85) +
  theme_minimal()
```

```
## Warning: Removed 97 rows containing non-finite outside the scale range
## (`stat_boxplot()`).
```

<img src="03_wide_files/figure-html/boxplot-twin1-1.png" width="768" />

**Box Plot of Weight for Twin 2**


``` r
ggplot(df_wide, aes(x = zyg, y = wt2, fill = zyg)) +
  geom_boxplot() +
  labs(x = "Zygosity", y = "Weight of Twin 2", title = "Box Plot of Weight for Twin 2 by Zygosity") +
  scale_fill_viridis_d(option = "viridis", begin = 0.1, end = 0.85) +
  theme_minimal()
```

```
## Warning: Removed 86 rows containing non-finite outside the scale range
## (`stat_boxplot()`).
```

<img src="03_wide_files/figure-html/boxplot-twin2-1.png" width="768" />


**Paired Boxplot of Weights by Zygosity**


``` r
ggplot(df_wide, aes(x = zyg, y = wt1, fill = zyg)) +
  geom_boxplot() +
  geom_boxplot(aes(y = wt2), color = "red", fill = NA) +
  labs(x = "Zygosity", y = "Weight", title = "Paired Boxplot of Weights by Zygosity") +
  theme_minimal()
```

```
## Warning: Removed 97 rows containing non-finite outside the scale range
## (`stat_boxplot()`).
```

```
## Warning: Removed 86 rows containing non-finite outside the scale range
## (`stat_boxplot()`).
```

<img src="03_wide_files/figure-html/paired-boxplot-1.png" width="768" />


## 2. Bivariate Distributions

### Scatter 


``` r
# Basic Scatter Plot of weight of Twin 1 vs. weight of Twin 2
p <- ggplot(df_wide, aes(x=wt1, y=wt2, color=zyg)) +
  geom_point(alpha=.5) +
  labs(x = "Weight of Twin 1", 
       y = "Weight of Twin 2", 
       title = "Scatterplot of weight by Zygosity") +
  scale_color_viridis_d(option = "virdis",
                        begin = 0.1,end=.85) +
  theme_minimal()

p
```

```
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
```

```
## Warning: Removed 173 rows containing missing values or values outside the scale range
## (`geom_point()`).
```

<img src="03_wide_files/figure-html/unnamed-chunk-2-1.png" width="672" />

Adding a regression line to the scatter plot.


``` r
p + geom_smooth(method = "lm", se = FALSE)
```

```
## `geom_smooth()` using formula = 'y ~ x'
```

```
## Warning: Removed 173 rows containing non-finite outside the scale range
## (`stat_smooth()`).
```

```
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
```

```
## Warning: Removed 173 rows containing missing values or values outside the scale range
## (`geom_point()`).
```

<img src="03_wide_files/figure-html/unnamed-chunk-3-1.png" width="672" />

### Marginal Density Plots


``` r
library(ggplot2)
library(ggExtra)

# Create marginal density plots for x and y axes
p_x <- ggplot(df_wide, aes(x = wt1, fill = zyg)) +
  geom_density(alpha = 0.5) +
  theme_minimal() +
  scale_fill_viridis_d(option = "viridis", begin = 0.1, end = 0.85) +
  theme(axis.title.x = element_blank(),
        axis.text.x = element_blank(),
        axis.ticks.x = element_blank())

p_x
```

```
## Warning: Removed 97 rows containing non-finite outside the scale range
## (`stat_density()`).
```

<img src="03_wide_files/figure-html/unnamed-chunk-4-1.png" width="672" />


``` r
p_y <- ggplot(df_wide, aes(x = wt2, fill = zyg)) +
  geom_density(alpha = 0.5) +
  scale_fill_viridis_d(option = "viridis", begin = 0.1, end = 0.85) +
  coord_flip() +
  theme_minimal() +
  theme(axis.title.y = element_blank(),
        axis.text.y = element_blank(),
        axis.ticks.y = element_blank())

 p_y
```

```
## Warning: Removed 86 rows containing non-finite outside the scale range
## (`stat_density()`).
```

<img src="03_wide_files/figure-html/unnamed-chunk-5-1.png" width="672" />


``` r
# with marginal histogram
p1 <- ggMarginal(p, type="histogram")
```

```
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
```

```
## Warning: Removed 173 rows containing missing values or values outside the scale range
## (`geom_point()`).
```

```
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
```

```
## Warning: Removed 173 rows containing missing values or values outside the scale range
## (`geom_point()`).
```

``` r
p1
```

<img src="03_wide_files/figure-html/unnamed-chunk-6-1.png" width="672" />


``` r
# marginal density
p2 <- ggMarginal(p, type="density")
```

```
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
```

```
## Warning: Removed 173 rows containing missing values or values outside the scale range
## (`geom_point()`).
```

```
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
```

```
## Warning: Removed 173 rows containing missing values or values outside the scale range
## (`geom_point()`).
```

``` r
p2
```

<img src="03_wide_files/figure-html/unnamed-chunk-7-1.png" width="672" />


``` r
# marginal boxplot
p3 <- ggMarginal(p, type="boxplot")
```

```
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
```

```
## Warning: Removed 173 rows containing missing values or values outside the scale range
## (`geom_point()`).
```

```
## Warning in viridisLite::viridis(n, alpha, begin, end, direction, option):
## Option 'virdis' does not exist. Defaulting to 'viridis'.
```

```
## Warning: Removed 173 rows containing missing values or values outside the scale range
## (`geom_point()`).
```

``` r
p3
```

<img src="03_wide_files/figure-html/unnamed-chunk-8-1.png" width="672" />


## 4. Correlation Analysis

### Correlation Matrix and Correlogram



``` r
library(ggcorrplot)
corr <- round(cor(df_wide %>% select(where(is.numeric))), 2)
ggcorrplot(corr, type = "lower", lab = TRUE, lab_size = 3, method = "circle", 
           colors = c("tomato2", "white", "springgreen3"), title = "Correlation Matrix of Twin Data", ggtheme = theme_bw)
```

<img src="03_wide_files/figure-html/correlation-matrix-1.png" width="768" />

<!--chapter:end:03_wide.Rmd-->

# Long Form Data


In contrast to wide form data, long form data, also known as "tidy data," structures datasets where each row represents a single observation, and each column represents a variable. This format is highly beneficial for statistical modeling and data analysis because it simplifies the application of various data manipulation and analysis functions. As before, we'll use the `twinData` dataset from the `OpenMx` package, but we'll convert it to long form to illustrate handling and analyzing data in this format.


## Converting from Wide to Long Form



``` r
library(tidyverse)
library(NlsyLinks)
library(discord)
library(BGmisc)
library(OpenMx)
library(conflicted) # to handle conflicts
conflicted::conflicts_prefer(OpenMx::vech,dplyr::filter) # Resolve conflicts


data(twinData)

df_long <- twinData %>% select(-age)
```


``` r
# Convert wide data to long form
df_long <- df_long %>%
  pivot_longer(
    cols = matches('1$|2$'), # Select columns ending in '1' or '2'
     cols_vary = "slowest", # Specify that the columns are in the same order for each twin
    names_to = c(".value", "twin"), # Split the column names into variable and twin number
    names_pattern = "(.*)(1|2)" # Capture the variable and twin number
  )
```


## Data Structure
Let's take a look at the structure of the dataset now that it's in long form.


``` r
class(df_long)
```

```
## [1] "tbl_df"     "tbl"        "data.frame"
```

``` r
glimpse(df_long)
```

```
## Rows: 7,616
## Columns: 11
## $ fam      <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18…
## $ zyg      <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
## $ part     <int> 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2, 2…
## $ cohort   <chr> "younger", "younger", "younger", "younger", "younger", "young…
## $ zygosity <fct> MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, MZFF, M…
## $ twin     <chr> "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "1", "…
## $ wt       <int> 58, 54, 55, 66, 50, 60, 65, 40, 60, 76, 48, 70, 51, 53, 58, 4…
## $ ht       <dbl> 1.7000, 1.6299, 1.6499, 1.5698, 1.6099, 1.5999, 1.7500, 1.559…
## $ htwt     <dbl> 20.0692, 20.3244, 20.2020, 26.7759, 19.2894, 23.4375, 21.2245…
## $ bmi      <dbl> 20.9943, 21.0828, 21.0405, 23.0125, 20.7169, 22.0804, 21.3861…
## $ age      <int> 21, 24, 21, 21, 19, 26, 23, 29, 24, 28, 29, 19, 23, 22, 23, 2…
```

The dataset now contains a much larger number of observations, as each twin's data is represented as a separate row. The zygosity variable indicates the zygosity of the twins, while other variables are split into variable and value pairs, reflecting measurements or characteristics of the twins.

## Adding `sex` and `zyg`

To facilitate analyses that depend on sex or zygosity type, we'll add these as new columns derived from zygosity.



``` r
# Add 'sex' and 'zyg' columns based on 'zygosity'
df_long <- df_long %>%
  mutate(sex = case_when(
    zygosity %in% c("MZFF", "DZFF") ~ "F",
    zygosity %in% c("MZMM", "DZMM") ~ "M",
    TRUE ~ "OS"
  ),
  zyg = case_when(
    zygosity %in% c("MZFF", "MZMM") ~ "MZ",
    zygosity %in% c("DZFF", "DZMM", "DZOS") ~ "DZ",
    TRUE ~ NA_character_
  ))
```

Unfortunately, the data do not contain the information for the gender for each twin, so we will just have to settle for noting that the data is missing.

## Summary Statistics (Long Form)

Once again, let's calculate summary statistics for numeric variables across the full sample. This will provide a quick overview of central tendencies and variability in the dataset. When working with long form data, it is often helpful to start with summarizing by the data structure you already have. In this case, we will calculate summary statistics by specific measurement across all twins.


Data Structure and Summary Statistics
Examine the transformed data and calculate summary statistics similar to those performed in the wide form.


``` r
summary_stats_long <- df_long %>%
  summarise(across(where(is.numeric), list(
    mean = ~mean(., na.rm = TRUE),
    sd = ~sd(., na.rm = TRUE),
    median = ~median(., na.rm = TRUE),
    min = ~min(., na.rm = TRUE),
    max = ~max(., na.rm = TRUE),
    IQR = ~IQR(., na.rm = TRUE)
  ), .names = "{col}_{fn}")) %>%
  pivot_longer(
    cols = everything(),
    names_to = c("variable", "statistic"),
    names_sep = "_"
  ) %>%
  pivot_wider(
    names_from = statistic,
    values_from = value
  )

summary_stats_long %>% 
  print(n = 15) # to see more rows
```

```
## # A tibble: 7 × 7
##   variable    mean        sd  median   min     max      IQR
##   <chr>      <dbl>     <dbl>   <dbl> <dbl>   <dbl>    <dbl>
## 1 fam      1904.   1099.     1904.    1    3808    1904.   
## 2 part        1.93    0.265     2     0       2       0    
## 3 wt         63.9    11.7      62    34     127      16    
## 4 ht          1.68    0.0958    1.68  1.34    1.99    0.150
## 5 htwt       22.6     3.18     22.2  13.3    46.2     3.83 
## 6 bmi        21.8     0.941    21.7  18.1    26.8     1.20 
## 7 age        34.5    14.2      30    17      88      19
```


Generate frequency tables for sex and zyg, paralleling the wide form analysis.
# Frequency Tables

Paralleling the wide form analysis, let us create frequency tables for categorical variables like zygosity and sex. These tables should provide a clear picture of the distribution of these categories within the dataset. In some ways, these calculations are simpler in long form data because each row is already an individual observation. 


``` r
# Counting 'zygosity' and calculating percentages
zygosity_summary_long <- df_long %>%
  count(zyg, name = "count") %>%
  mutate(percentage = count / sum(count) * 100) %>%
  rename(category = zyg) %>%  # Renaming the column for clarity
  mutate(variable = "zygosity")  # Adding a descriptor column for the variable

# Counting 'sex' and calculating percentages
sex_summary_long <- df_long %>%
  count(sex, name = "count") %>%
  mutate(percentage = count / sum(count) * 100) %>%
  rename(category = sex) %>%  # Renaming the column for clarity
  mutate(variable = "sex")  # Adding a descriptor column for the variable

# Combining both summaries into a single dataframe
combined_summary_long <- bind_rows(zygosity_summary_long, sex_summary_long) %>%
  select(variable, category, everything())  # Reordering columns for clarity

combined_summary_long
```

```
## # A tibble: 5 × 4
##   variable category count percentage
##   <chr>    <chr>    <int>      <dbl>
## 1 zygosity DZ        4018       52.8
## 2 zygosity MZ        3598       47.2
## 3 sex      F         3966       52.1
## 4 sex      M         1838       24.1
## 5 sex      OS        1812       23.8
```

As you can see, the long form data structure allows for a straightforward calculation of frequency tables for categorical variables. The resulting tables provide a clear picture of the distribution, and it does not differ  from the wide form analysis, as long as one remembers to that we're now looking at individual twins rather than pairs.


<!--chapter:end:04_long.Rmd-->

# Long Form Data Plots



<!--chapter:end:05_descriptiveplots.Rmd-->

# Path Diagrams


<!--chapter:end:06_pathdiagrams.Rmd-->

# Tables


<!--chapter:end:07_tables.Rmd-->

# Final Words
<!-- I leaned into the cheesiness -->
Throughout this document, we have embarked on an exploration of the evolving landscape of data visualization in the field of behavior genetics. By revisiting historical methodologies and embracing modern techniques, we have uncovered a rich tapestry of visual tools that enhance our understanding and communication of genetic data. The atlas of `ggplot2` visualizations presented here not only serves as a practical guide but also as an inspiration for researchers to think creatively about how data can be visualized more effectively.

<!--chapter:end:08_summary.Rmd-->


# References {-}


<!--chapter:end:09_references.Rmd-->


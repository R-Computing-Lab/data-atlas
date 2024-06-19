--- 
title: "Data Atlas"
author: 
- S. Mason Garrison
date: "2024-06-19"
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

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
##  date     2024-06-23
##  pandoc   3.1.11 @ C:/Program Files/RStudio/resources/app/bin/quarto/bin/tools/ (via rmarkdown)
```

Along with these packages:


```{=html}
<div class="datatables html-widget html-fill-item" id="htmlwidget-16c0c9cbc5dfad49fe85" style="width:100%;height:auto;"></div>
<script type="application/json" data-for="htmlwidget-16c0c9cbc5dfad49fe85">{"x":{"filter":"top","vertical":false,"filterHTML":"<tr>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n  <td data-type=\"character\" style=\"vertical-align: top;\">\n    <div class=\"form-group has-feedback\" style=\"margin-bottom: auto;\">\n      <input type=\"search\" placeholder=\"All\" class=\"form-control\" style=\"width: 100%;\" disabled=\"\"/>\n      <span class=\"glyphicon glyphicon-remove-circle form-control-feedback\"><\/span>\n    <\/div>\n  <\/td>\n<\/tr>","data":[["base64enc","bookdown","bslib","cachem","cli","digest","evaluate","fastmap","fontawesome","fs","glue","highr","htmltools","jquerylib","jsonlite","knitr","lifecycle","memoise","mime","R6","rappdirs","rlang","rmarkdown","sass","tinytex","xfun","yaml"],[null,"0.39","0.7.0","1.1.0","3.6.2","0.6.35","0.23","1.2.0",null,"1.6.4","1.7.0",null,"0.5.8.1","0.1.4","1.8.8","1.46","1.0.4","2.0.1","0.12","2.5.1",null,"1.1.3","2.27","0.4.9",null,"0.44","2.3.8"],["2015-07-28","2024-04-15","2024-03-29","2024-05-16","2023-12-11","2024-03-11","2023-11-01","2024-05-15","2023-08-19","2024-04-25","2024-01-09","2024-05-26","2024-04-04","2021-04-26","2023-12-04","2024-04-06","2023-11-07","2021-11-26","2021-09-28","2021-08-19","2021-01-31","2024-01-10","2024-05-17","2024-03-15","2024-05-06","2024-05-15","2023-12-11"],["CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)","CRAN (R 4.4.0)"]],"container":"<table class=\"cell-border stripe\">\n  <thead>\n    <tr>\n      <th>package<\/th>\n      <th>loadedversion<\/th>\n      <th>date<\/th>\n      <th>source<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":27,"autoWidth":true,"bInfo":false,"paging":false,"columnDefs":[{"name":"package","targets":0},{"name":"loadedversion","targets":1},{"name":"date","targets":2},{"name":"source","targets":3}],"order":[],"orderClasses":false,"orderCellsTop":true,"lengthMenu":[10,25,27,50,100]},"selection":{"mode":"multiple","selected":null,"target":"row","selectable":null}},"evals":[],"jsHooks":[]}</script>
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

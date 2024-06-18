# Welcome to ggplot

This chapter serves as an in-depth guide for visualizing twin study data using `ggplot2`, a component of the R `tidyverse` package. By leveraging the flexibility and power of `ggplot2`, researchers can effectively illustrate the intricate patterns often present in twin study data.


## math example

$p$ is unknown but expected to be around 1/3. Standard error will be approximated

$$
SE = \sqrt(\frac{p(1-p)}{n}) \approx \sqrt{\frac{1/3 (1 - 1/3)} {300}} = 0.027
$$

You can also use math in footnotes like this^[where we mention $p = \frac{a}{b}$].

We will approximate standard error to 0.027[^longnote]

[^longnote]: $p$ is unknown but expected to be around 1/3. Standard error will be approximated

    $$
    SE = \sqrt(\frac{p(1-p)}{n}) \approx \sqrt{\frac{1/3 (1 - 1/3)} {300}} = 0.027
    $$

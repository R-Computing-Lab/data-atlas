# (PART\*) Generating Tables {-}

# Generating Tables in APA Style

When presenting data in scientific papers, it's important to follow the guidelines provided by the American Psychological Association (APA) to ensure clarity and consistency. In this section, we'll demonstrate how to generate tables in APA style using the `kableExtra` package in R.

## Summary Statistics

First, let's calculate summary statistics for the twin data and present them in an APA-style table.


``` r
# Load necessary libraries
library(tidyverse)
```

```
## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
## ✔ dplyr     1.1.4     ✔ readr     2.1.5
## ✔ forcats   1.0.0     ✔ stringr   1.5.1
## ✔ ggplot2   3.5.1     ✔ tibble    3.2.1
## ✔ lubridate 1.9.3     ✔ tidyr     1.3.1
## ✔ purrr     1.0.2     
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```

``` r
library(kableExtra)
```

```
## 
## Attaching package: 'kableExtra'
## 
## The following object is masked from 'package:dplyr':
## 
##     group_rows
```

``` r
library(tidyverse)
library(NlsyLinks)
library(discord)
library(BGmisc)
library(OpenMx)
```

```
## 
## Attaching package: 'OpenMx'
## 
## The following object is masked from 'package:BGmisc':
## 
##     vech
```

``` r
library(conflicted) # to handle conflicts
conflicted::conflicts_prefer(OpenMx::vech,dplyr::filter) # Resolve conflicts
```

```
## [conflicted] Will prefer OpenMx::vech over any other package.
## [conflicted] Will prefer dplyr::filter over any other package.
```

``` r
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

``` r
# Calculate summary statistics
summary_stats_long <- df_long %>%
  summarise(across(where(is.numeric), list(
    Mean = ~mean(., na.rm = TRUE),
    SD = ~sd(., na.rm = TRUE),
    Median = ~median(., na.rm = TRUE),
    Min = ~min(., na.rm = TRUE),
    Max = ~max(., na.rm = TRUE),
    IQR = ~IQR(., na.rm = TRUE)
  ), .names = "{col}_{fn}")) %>%
  pivot_longer(
    cols = everything(),
    names_to = c("Variable", "Statistic"),
    names_sep = "_"
  ) %>%
  pivot_wider(
    names_from = Statistic,
    values_from = value
  )
```

Now, let's create an APA-style table for these summary statistics.


``` r
# Generate APA-style table
summary_stats_long %>%
  kable(caption = "Summary Statistics for Twin Data",
        col.names = c("Variable", "Mean", "SD", "Median", "Min", "Max", "IQR"),
        format = "html") %>%
  kable_styling(bootstrap_options = c("striped", "hover", "condensed", "responsive"),
                full_width = FALSE,
                position = "left") %>%
  add_header_above(c(" " = 1, "Summary Statistics" = 6)) %>%
  footnote(general = "Note. This table presents the summary statistics for the variables in the twin dataset.",
           general_title = " ",
           footnote_as_chunk = TRUE)
```

<table class="table table-striped table-hover table-condensed table-responsive" style="width: auto !important; border-bottom: 0;">
<caption>(\#tab:unnamed-chunk-4)Summary Statistics for Twin Data</caption>
 <thead>
<tr>
<th style="empty-cells: hide;border-bottom:hidden;" colspan="1"></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; " colspan="6"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">Summary Statistics</div></th>
</tr>
  <tr>
   <th style="text-align:left;"> Variable </th>
   <th style="text-align:right;"> Mean </th>
   <th style="text-align:right;"> SD </th>
   <th style="text-align:right;"> Median </th>
   <th style="text-align:right;"> Min </th>
   <th style="text-align:right;"> Max </th>
   <th style="text-align:right;"> IQR </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> fam </td>
   <td style="text-align:right;"> 1904.500000 </td>
   <td style="text-align:right;"> 1099.3470505 </td>
   <td style="text-align:right;"> 1904.5000 </td>
   <td style="text-align:right;"> 1.0000 </td>
   <td style="text-align:right;"> 3808.0000 </td>
   <td style="text-align:right;"> 1903.5000 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> part </td>
   <td style="text-align:right;"> 1.933298 </td>
   <td style="text-align:right;"> 0.2648394 </td>
   <td style="text-align:right;"> 2.0000 </td>
   <td style="text-align:right;"> 0.0000 </td>
   <td style="text-align:right;"> 2.0000 </td>
   <td style="text-align:right;"> 0.0000 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> wt </td>
   <td style="text-align:right;"> 63.881744 </td>
   <td style="text-align:right;"> 11.7100387 </td>
   <td style="text-align:right;"> 62.0000 </td>
   <td style="text-align:right;"> 34.0000 </td>
   <td style="text-align:right;"> 127.0000 </td>
   <td style="text-align:right;"> 16.0000 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> ht </td>
   <td style="text-align:right;"> 1.677868 </td>
   <td style="text-align:right;"> 0.0958175 </td>
   <td style="text-align:right;"> 1.6799 </td>
   <td style="text-align:right;"> 1.3398 </td>
   <td style="text-align:right;"> 1.9900 </td>
   <td style="text-align:right;"> 0.1501 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> htwt </td>
   <td style="text-align:right;"> 22.612309 </td>
   <td style="text-align:right;"> 3.1794125 </td>
   <td style="text-align:right;"> 22.2041 </td>
   <td style="text-align:right;"> 13.2964 </td>
   <td style="text-align:right;"> 46.2493 </td>
   <td style="text-align:right;"> 3.8303 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> bmi </td>
   <td style="text-align:right;"> 21.764600 </td>
   <td style="text-align:right;"> 0.9408264 </td>
   <td style="text-align:right;"> 21.7019 </td>
   <td style="text-align:right;"> 18.1125 </td>
   <td style="text-align:right;"> 26.8383 </td>
   <td style="text-align:right;"> 1.2029 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> age </td>
   <td style="text-align:right;"> 34.453494 </td>
   <td style="text-align:right;"> 14.1704368 </td>
   <td style="text-align:right;"> 30.0000 </td>
   <td style="text-align:right;"> 17.0000 </td>
   <td style="text-align:right;"> 88.0000 </td>
   <td style="text-align:right;"> 19.0000 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<span style="font-style: italic;"> </span> <sup></sup> Note. This table presents the summary statistics for the variables in the twin dataset.</td></tr></tfoot>
</table>

The table above presents the summary statistics for the variables in the twin dataset, including the mean, standard deviation, median, minimum, maximum, and interquartile range.


## Frequency Tables
Next, we'll create frequency tables for categorical variables such as zygosity and sex, and format them in APA style.


``` r
# Calculate frequency tables
frequency_tables <- df_long %>%
  select(zyg, sex) %>%
  pivot_longer(cols = everything(), names_to = "Variable", values_to = "Category") %>%
  group_by(Variable, Category) %>%
  summarise(Count = n()) %>%
  mutate(Percentage = round((Count / sum(Count)) * 100, 2)) %>%
  ungroup()
```

```
## `summarise()` has grouped output by 'Variable'. You can override using the
## `.groups` argument.
```
Let's create an APA-style table for these frequency tables.

# Generate APA-style table for frequency tables



``` r
frequency_tables %>%
  kable(caption = "Frequency Tables for Categorical Variables",
        col.names = c("Variable", "Category", "Count", "Percentage"),
        format = "html") %>%
  kable_styling(bootstrap_options = c("striped", "hover", "condensed", "responsive"),
                full_width = FALSE,
                position = "left") %>%
  add_header_above(c(" " = 2, "Frequency Table" = 2)) %>%
  footnote(general = "Note. This table presents the frequency and percentage of categories for zygosity and sex in the twin dataset.",
           general_title = " ",
           footnote_as_chunk = TRUE)
```

<table class="table table-striped table-hover table-condensed table-responsive" style="width: auto !important; border-bottom: 0;">
<caption>(\#tab:unnamed-chunk-6)Frequency Tables for Categorical Variables</caption>
 <thead>
<tr>
<th style="empty-cells: hide;border-bottom:hidden;" colspan="2"></th>
<th style="border-bottom:hidden;padding-bottom:0; padding-left:3px;padding-right:3px;text-align: center; " colspan="2"><div style="border-bottom: 1px solid #ddd; padding-bottom: 5px; ">Frequency Table</div></th>
</tr>
  <tr>
   <th style="text-align:left;"> Variable </th>
   <th style="text-align:left;"> Category </th>
   <th style="text-align:right;"> Count </th>
   <th style="text-align:right;"> Percentage </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> sex </td>
   <td style="text-align:left;"> F </td>
   <td style="text-align:right;"> 3966 </td>
   <td style="text-align:right;"> 52.07 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> sex </td>
   <td style="text-align:left;"> M </td>
   <td style="text-align:right;"> 1838 </td>
   <td style="text-align:right;"> 24.13 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> sex </td>
   <td style="text-align:left;"> OS </td>
   <td style="text-align:right;"> 1812 </td>
   <td style="text-align:right;"> 23.79 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> zyg </td>
   <td style="text-align:left;"> DZ </td>
   <td style="text-align:right;"> 4018 </td>
   <td style="text-align:right;"> 52.76 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> zyg </td>
   <td style="text-align:left;"> MZ </td>
   <td style="text-align:right;"> 3598 </td>
   <td style="text-align:right;"> 47.24 </td>
  </tr>
</tbody>
<tfoot><tr><td style="padding: 0; " colspan="100%">
<span style="font-style: italic;"> </span> <sup></sup> Note. This table presents the frequency and percentage of categories for zygosity and sex in the twin dataset.</td></tr></tfoot>
</table>

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


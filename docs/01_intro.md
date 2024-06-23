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


---
title: Tidyverse Tidyr Package
author: Sikai Huang
date: '2022-05-09'
slug: tidyverse-tidyr-package
categories:
  - R
tags:
  - RStudio
output:
  html_document:
    toc: yes
    theme: united
---

<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<link href="{{< blogdown/postref >}}index_files/datatables-css/datatables-crosstalk.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/datatables-binding/datatables.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery-3.6.0.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.min.css" rel="stylesheet" />
<link href="{{< blogdown/postref >}}index_files/dt-core/css/jquery.dataTables.extra.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/dt-core/js/jquery.dataTables.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/crosstalk/css/crosstalk.min.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/crosstalk/js/crosstalk.min.js"></script>

How to process messy data at hand? What does tidy data looks like? ![TidyData](images/tidy_data.png) Tidy data includes three key points:

-   each row includes each observation
-   each column stands for each variable
-   each cell contains each value

let’s look at an example of messy data: Although the following data satisfies three kep points we mentioned before, we could change our perspectives to better understand it.

<div id="htmlwidget-1" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40","41","42","43","44","45","46","47","48","49","50","51","52","53","54","55","56","57","58","59","60","61","62","63","64","65","66","67","68","69","70","71","72","73","74","75","76","77","78","79","80","81","82","83","84","85","86","87","88","89","90","91","92","93","94","95","96","97","98","99","100","101","102","103","104"],["01","01","02","02","04","04","05","05","06","06","08","08","09","09","10","10","11","11","12","12","13","13","15","15","16","16","17","17","18","18","19","19","20","20","21","21","22","22","23","23","24","24","25","25","26","26","27","27","28","28","29","29","30","30","31","31","32","32","33","33","34","34","35","35","36","36","37","37","38","38","39","39","40","40","41","41","42","42","44","44","45","45","46","46","47","47","48","48","49","49","50","50","51","51","53","53","54","54","55","55","56","56","72","72"],["Alabama","Alabama","Alaska","Alaska","Arizona","Arizona","Arkansas","Arkansas","California","California","Colorado","Colorado","Connecticut","Connecticut","Delaware","Delaware","District of Columbia","District of Columbia","Florida","Florida","Georgia","Georgia","Hawaii","Hawaii","Idaho","Idaho","Illinois","Illinois","Indiana","Indiana","Iowa","Iowa","Kansas","Kansas","Kentucky","Kentucky","Louisiana","Louisiana","Maine","Maine","Maryland","Maryland","Massachusetts","Massachusetts","Michigan","Michigan","Minnesota","Minnesota","Mississippi","Mississippi","Missouri","Missouri","Montana","Montana","Nebraska","Nebraska","Nevada","Nevada","New Hampshire","New Hampshire","New Jersey","New Jersey","New Mexico","New Mexico","New York","New York","North Carolina","North Carolina","North Dakota","North Dakota","Ohio","Ohio","Oklahoma","Oklahoma","Oregon","Oregon","Pennsylvania","Pennsylvania","Rhode Island","Rhode Island","South Carolina","South Carolina","South Dakota","South Dakota","Tennessee","Tennessee","Texas","Texas","Utah","Utah","Vermont","Vermont","Virginia","Virginia","Washington","Washington","West Virginia","West Virginia","Wisconsin","Wisconsin","Wyoming","Wyoming","Puerto Rico","Puerto Rico"],["income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent"],[24476,747,32940,1200,27517,972,23789,709,29454,1358,32401,1125,35326,1123,31560,1076,43198,1424,25952,1077,27024,927,32453,1507,25298,792,30684,952,27247,782,30002,740,29126,801,24702,713,25086,825,26841,808,37147,1311,34498,1173,26987,824,32734,906,22766,740,26999,784,26249,751,30020,773,29019,1017,33172,1052,35075,1249,24457,809,31057,1194,26482,844,32336,775,27435,764,26207,766,27389,988,28923,885,30210,957,25454,836,28821,696,25453,808,28063,952,27928,948,29351,945,32545,1166,32318,1120,23707,681,29868,813,30854,828,null,464],[136,3,508,13,148,4,165,5,109,3,109,5,195,5,247,10,681,17,70,3,106,3,218,18,208,7,83,3,117,3,143,4,208,5,159,4,155,4,187,7,152,5,199,5,82,3,189,4,194,5,113,4,206,9,146,4,213,6,387,9,148,4,214,6,69,3,111,3,245,9,94,2,101,3,146,4,119,3,259,6,123,4,276,7,102,4,110,2,239,6,361,11,202,5,113,4,203,6,135,3,342,11,null,6]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>GEOID<\/th>\n      <th>NAME<\/th>\n      <th>variable<\/th>\n      <th>estimate<\/th>\n      <th>moe<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"columnDefs":[{"className":"dt-right","targets":[4,5]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

------------------------------------------------------------------------

# Pivot

Among all definitions of pivot, I preferred that one given by [Merriam-Webster](https://www.merriam-webster.com/dictionary/pivot).

> ***To adapt or improve by adjusting or modifying something (such as a product, service, or strategy)***

The pivot here is an action of **improve** whatever you turn left or right. That’s why we’ve got **data pivoting**. Data pivoting enables you to rearrange the columns and rows in a data so you can view it from different perspectives to get a better sense of it.

## Pivot data from long to wide

``` r
us_rent_income
```

    ## # A tibble: 104 × 5
    ##    GEOID NAME       variable estimate   moe
    ##    <chr> <chr>      <chr>       <dbl> <dbl>
    ##  1 01    Alabama    income      24476   136
    ##  2 01    Alabama    rent          747     3
    ##  3 02    Alaska     income      32940   508
    ##  4 02    Alaska     rent         1200    13
    ##  5 04    Arizona    income      27517   148
    ##  6 04    Arizona    rent          972     4
    ##  7 05    Arkansas   income      23789   165
    ##  8 05    Arkansas   rent          709     5
    ##  9 06    California income      29454   109
    ## 10 06    California rent         1358     3
    ## # … with 94 more rows

``` r
us_rent_income %>%
  pivot_wider(
    names_from = variable,
    values_from = c(estimate, moe)
  )
```

    ## # A tibble: 52 × 6
    ##    GEOID NAME                 estimate_income estimate_rent moe_income moe_rent
    ##    <chr> <chr>                          <dbl>         <dbl>      <dbl>    <dbl>
    ##  1 01    Alabama                        24476           747        136        3
    ##  2 02    Alaska                         32940          1200        508       13
    ##  3 04    Arizona                        27517           972        148        4
    ##  4 05    Arkansas                       23789           709        165        5
    ##  5 06    California                     29454          1358        109        3
    ##  6 08    Colorado                       32401          1125        109        5
    ##  7 09    Connecticut                    35326          1123        195        5
    ##  8 10    Delaware                       31560          1076        247       10
    ##  9 11    District of Columbia           43198          1424        681       17
    ## 10 12    Florida                        25952          1077         70        3
    ## # … with 42 more rows

## Pivot data from wide to long

``` r
head(relig_income)
```

    ## # A tibble: 6 × 11
    ##   religion  `<$10k` `$10-20k` `$20-30k` `$30-40k` `$40-50k` `$50-75k` `$75-100k`
    ##   <chr>       <dbl>     <dbl>     <dbl>     <dbl>     <dbl>     <dbl>      <dbl>
    ## 1 Agnostic       27        34        60        81        76       137        122
    ## 2 Atheist        12        27        37        52        35        70         73
    ## 3 Buddhist       27        21        30        34        33        58         62
    ## 4 Catholic      418       617       732       670       638      1116        949
    ## 5 Don’t kn…      15        14        15        11        10        35         21
    ## 6 Evangeli…     575       869      1064       982       881      1486        949
    ## # … with 3 more variables: $100-150k <dbl>, >150k <dbl>,
    ## #   Don't know/refused <dbl>

``` r
relig_income %>%
  pivot_longer(!religion, names_to = "income", values_to = "count")
```

    ## # A tibble: 180 × 3
    ##    religion income             count
    ##    <chr>    <chr>              <dbl>
    ##  1 Agnostic <$10k                 27
    ##  2 Agnostic $10-20k               34
    ##  3 Agnostic $20-30k               60
    ##  4 Agnostic $30-40k               81
    ##  5 Agnostic $40-50k               76
    ##  6 Agnostic $50-75k              137
    ##  7 Agnostic $75-100k             122
    ##  8 Agnostic $100-150k            109
    ##  9 Agnostic >150k                 84
    ## 10 Agnostic Don't know/refused    96
    ## # … with 170 more rows

``` r
billboard %>%
  pivot_longer(
    cols = starts_with("wk"), # or wk1:wkN
    names_to = "week",
    names_prefix = "wk", # A regular expression used to remove matching text from the start of each variable name
    names_transform = list(week = as.integer),  # convert a character variable called week to an integer
    values_to = "rank",
    values_drop_na = TRUE
  )
```

    ## # A tibble: 5,307 × 5
    ##    artist  track                   date.entered  week  rank
    ##    <chr>   <chr>                   <date>       <int> <dbl>
    ##  1 2 Pac   Baby Don't Cry (Keep... 2000-02-26       1    87
    ##  2 2 Pac   Baby Don't Cry (Keep... 2000-02-26       2    82
    ##  3 2 Pac   Baby Don't Cry (Keep... 2000-02-26       3    72
    ##  4 2 Pac   Baby Don't Cry (Keep... 2000-02-26       4    77
    ##  5 2 Pac   Baby Don't Cry (Keep... 2000-02-26       5    87
    ##  6 2 Pac   Baby Don't Cry (Keep... 2000-02-26       6    94
    ##  7 2 Pac   Baby Don't Cry (Keep... 2000-02-26       7    99
    ##  8 2Ge+her The Hardest Part Of ... 2000-09-02       1    91
    ##  9 2Ge+her The Hardest Part Of ... 2000-09-02       2    87
    ## 10 2Ge+her The Hardest Part Of ... 2000-09-02       3    92
    ## # … with 5,297 more rows

## Uncount a data frame

Uncount the data so that per x, each character gets a row and an ID.

``` r
df <- tibble(star = c("Jason", "Murphy"), boxoffice = c(1, 2))
df
```

    ## # A tibble: 2 × 2
    ##   star   boxoffice
    ##   <chr>      <dbl>
    ## 1 Jason          1
    ## 2 Murphy         2

``` r
uncount(df, boxoffice)
```

    ## # A tibble: 3 × 1
    ##   star  
    ##   <chr> 
    ## 1 Jason 
    ## 2 Murphy
    ## 3 Murphy

``` r
uncount(df, boxoffice, .id = "ID") # The ID should go in the id column
```

    ## # A tibble: 3 × 2
    ##   star      ID
    ##   <chr>  <int>
    ## 1 Jason      1
    ## 2 Murphy     1
    ## 3 Murphy     2

# Separate, Unite, and Fill

## Separate a character column into multiple columns

df contains strings with both a name and sort of drinks. We will tidy this dataset so that each variable gets its own column.

``` r
library(tidyr)
df <- data.frame(x = c("Joy:Milk", "Monica:Coffee", "Chandler:Tea", "Rachel:Juice", NA))
df %>% separate(x, into = c("name","drink"), sep = ":", convert = TRUE) 
```

    ##       name  drink
    ## 1      Joy   Milk
    ## 2   Monica Coffee
    ## 3 Chandler    Tea
    ## 4   Rachel  Juice
    ## 5     <NA>   <NA>

## Unite multiple columns into one by pasting strings together

``` r
df <- data.frame(name = c("Joy", "Monica", NA), drink = c("Milk", "Coffee", NA))
df
```

    ##     name  drink
    ## 1    Joy   Milk
    ## 2 Monica Coffee
    ## 3   <NA>   <NA>

``` r
df %>% unite("Love", name, drink, sep =" loves ", remove = FALSE)
```

    ##                  Love   name  drink
    ## 1      Joy loves Milk    Joy   Milk
    ## 2 Monica loves Coffee Monica Coffee
    ## 3         NA loves NA   <NA>   <NA>

``` r
df %>% unite("Love", name, drink, sep =" loves ", na.rm = TRUE, remove = FALSE) # To remove missing values:
```

    ##                  Love   name  drink
    ## 1      Joy loves Milk    Joy   Milk
    ## 2 Monica loves Coffee Monica Coffee
    ## 3                       <NA>   <NA>

## Separate a collapsed column into multiple rows

``` r
df <- data.frame(
  name = c("Joy", "Monica/Chandler", "Rachel/Ross"),
  drink = c("Milk", "Coffee/Tea", "Juice/Water")
  )
df %>% 
  separate_rows(name, drink, sep = "/", convert = TRUE)
```

    ## # A tibble: 5 × 2
    ##   name     drink 
    ##   <chr>    <chr> 
    ## 1 Joy      Milk  
    ## 2 Monica   Coffee
    ## 3 Chandler Tea   
    ## 4 Rachel   Juice 
    ## 5 Ross     Water

## Fill in missing values with previous or next value

``` r
sales <- tibble::tribble(
  ~quarter, ~year, ~sales,
  "Q1",    2000,    66013,
  "Q2",      NA,    69182,
  "Q3",      NA,    53175,
  "Q4",      NA,    21001,
  "Q1",    2001,    46036,
  "Q2",      NA,    58842,
  "Q3",      NA,    44568,
  "Q4",      NA,    50197,
  "Q1",    2002,    39113,
  "Q2",      NA,    41668,
  "Q3",      NA,    30144,
  "Q4",      NA,    52897,
  "Q1",    2004,    32129,
  "Q2",      NA,    67686,
  "Q3",      NA,    31768,
  "Q4",      NA,    49094
)
# `fill()` defaults to replacing missing data from top to bottom
sales_df <- sales %>% fill(year, .direction = "down")
sales_df
```

    ## # A tibble: 16 × 3
    ##    quarter  year sales
    ##    <chr>   <dbl> <dbl>
    ##  1 Q1       2000 66013
    ##  2 Q2       2000 69182
    ##  3 Q3       2000 53175
    ##  4 Q4       2000 21001
    ##  5 Q1       2001 46036
    ##  6 Q2       2001 58842
    ##  7 Q3       2001 44568
    ##  8 Q4       2001 50197
    ##  9 Q1       2002 39113
    ## 10 Q2       2002 41668
    ## 11 Q3       2002 30144
    ## 12 Q4       2002 52897
    ## 13 Q1       2004 32129
    ## 14 Q2       2004 67686
    ## 15 Q3       2004 31768
    ## 16 Q4       2004 49094

Create a line plot with sales per quarter colored by year

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-10-1.png" width="672" />

## Create a tibble from all combinations of inputs

``` r
expand_grid(x = 1:3, y = 1:2)
```

    ## # A tibble: 6 × 2
    ##       x     y
    ##   <int> <int>
    ## 1     1     1
    ## 2     1     2
    ## 3     2     1
    ## 4     2     2
    ## 5     3     1
    ## 6     3     2

``` r
expand_grid(l1 = letters, l2 = LETTERS)
```

    ## # A tibble: 676 × 2
    ##    l1    l2   
    ##    <chr> <chr>
    ##  1 a     A    
    ##  2 a     B    
    ##  3 a     C    
    ##  4 a     D    
    ##  5 a     E    
    ##  6 a     F    
    ##  7 a     G    
    ##  8 a     H    
    ##  9 a     I    
    ## 10 a     J    
    ## # … with 666 more rows

``` r
expand_grid(x1 = matrix(1:4, nrow = 2), x2 = matrix(5:8, nrow = 2))
```

    ## # A tibble: 4 × 2
    ##   x1[,1]  [,2] x2[,1]  [,2]
    ##    <int> <int>  <int> <int>
    ## 1      1     3      5     7
    ## 2      1     3      6     8
    ## 3      2     4      5     7
    ## 4      2     4      6     8

## Complete a data frame with missing combinations of data

``` r
df <- tibble(
  group = c(1:2, 1, 2),
  item_id = c(1:2, 2, 3),
  item_name = c("a", "a", "b", "b"),
  value1 = c(1, NA, 3, 4),
  value2 = 4:7
)
df
```

    ## # A tibble: 4 × 5
    ##   group item_id item_name value1 value2
    ##   <dbl>   <dbl> <chr>      <dbl>  <int>
    ## 1     1       1 a              1      4
    ## 2     2       2 a             NA      5
    ## 3     1       2 b              3      6
    ## 4     2       3 b              4      7

``` r
# Generate all possible combinations of `group`, `item_id`, and `item_name`
# (whether or not they appear in the data)
complete(df, group, item_id, item_name)
```

    ## # A tibble: 12 × 5
    ##    group item_id item_name value1 value2
    ##    <dbl>   <dbl> <chr>      <dbl>  <int>
    ##  1     1       1 a              1      4
    ##  2     1       1 b             NA     NA
    ##  3     1       2 a             NA     NA
    ##  4     1       2 b              3      6
    ##  5     1       3 a             NA     NA
    ##  6     1       3 b             NA     NA
    ##  7     2       1 a             NA     NA
    ##  8     2       1 b             NA     NA
    ##  9     2       2 a             NA      5
    ## 10     2       2 b             NA     NA
    ## 11     2       3 a             NA     NA
    ## 12     2       3 b              4      7

``` r
# # Cross all possible `group` values with the unique pairs of
# `(item_id, item_name)` that already exist in the data
complete(df, group, nesting(item_id, item_name))
```

    ## # A tibble: 8 × 5
    ##   group item_id item_name value1 value2
    ##   <dbl>   <dbl> <chr>      <dbl>  <int>
    ## 1     1       1 a              1      4
    ## 2     1       2 a             NA     NA
    ## 3     1       2 b              3      6
    ## 4     1       3 b             NA     NA
    ## 5     2       1 a             NA     NA
    ## 6     2       2 a             NA      5
    ## 7     2       2 b             NA     NA
    ## 8     2       3 b              4      7

## Create the full sequence of values in a vector

``` r
outer_dates <- c(as.Date("1980-01-01"), as.Date("1980-12-31"))

# Generate the dates for all days in 1980
head(full_seq(outer_dates, period = 1))
```

    ## [1] "1980-01-01" "1980-01-02" "1980-01-03" "1980-01-04" "1980-01-05"
    ## [6] "1980-01-06"

# Rectangling data

## Rectangle a nested list into a tidy tibble

hoist(), unnest_longer(), and unnest_wider() provide tools for rectangling, collapsing deeply nested lists into regular columns.

Named lists of **fixed length** = unnest_wider(), unnamed lists of **varying length** = unnest_longer().

``` r
df <- tibble(
  character = c("Toothless", "Dory"),
  metadata = list(
    list(
      species = "dragon",
      color = "black",
      films = c(
        "How to Train Your Dragon",
        "How to Train Your Dragon 2",
        "How to Train Your Dragon: The Hidden World"
       )
    ),
    list(
      species = "blue tang",
      color = "blue",
      films = c("Finding Nemo", "Finding Dory")
    )
  )
)
df
```

    ## # A tibble: 2 × 2
    ##   character metadata        
    ##   <chr>     <list>          
    ## 1 Toothless <named list [3]>
    ## 2 Dory      <named list [3]>

``` r
# Turn all components of metadata into columns
df %>% unnest_wider(metadata)
```

    ## # A tibble: 2 × 4
    ##   character species   color films    
    ##   <chr>     <chr>     <chr> <list>   
    ## 1 Toothless dragon    black <chr [3]>
    ## 2 Dory      blue tang blue  <chr [2]>

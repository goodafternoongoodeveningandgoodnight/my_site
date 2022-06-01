---
title: Tidyverse Tidyr Package (Updating)
author: Sikai Huang
date: '2022-05-09'
slug: tidyverse-tidyr-package
categories:
  - R
tags:
  - RStudio
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

How to do with messy data at hand? What does tidy data looks like?
![TidyData](images/tidy_data.png)
Tidy data includes three key points:
- each row includes each observation
- each column stands for each variable
- each cell contains each value

let’s look at an example of messy data:

<div id="htmlwidget-1" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"filter":"none","vertical":false,"data":[["1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","34","35","36","37","38","39","40","41","42","43","44","45","46","47","48","49","50","51","52","53","54","55","56","57","58","59","60","61","62","63","64","65","66","67","68","69","70","71","72","73","74","75","76","77","78","79","80","81","82","83","84","85","86","87","88","89","90","91","92","93","94","95","96","97","98","99","100","101","102","103","104"],["01","01","02","02","04","04","05","05","06","06","08","08","09","09","10","10","11","11","12","12","13","13","15","15","16","16","17","17","18","18","19","19","20","20","21","21","22","22","23","23","24","24","25","25","26","26","27","27","28","28","29","29","30","30","31","31","32","32","33","33","34","34","35","35","36","36","37","37","38","38","39","39","40","40","41","41","42","42","44","44","45","45","46","46","47","47","48","48","49","49","50","50","51","51","53","53","54","54","55","55","56","56","72","72"],["Alabama","Alabama","Alaska","Alaska","Arizona","Arizona","Arkansas","Arkansas","California","California","Colorado","Colorado","Connecticut","Connecticut","Delaware","Delaware","District of Columbia","District of Columbia","Florida","Florida","Georgia","Georgia","Hawaii","Hawaii","Idaho","Idaho","Illinois","Illinois","Indiana","Indiana","Iowa","Iowa","Kansas","Kansas","Kentucky","Kentucky","Louisiana","Louisiana","Maine","Maine","Maryland","Maryland","Massachusetts","Massachusetts","Michigan","Michigan","Minnesota","Minnesota","Mississippi","Mississippi","Missouri","Missouri","Montana","Montana","Nebraska","Nebraska","Nevada","Nevada","New Hampshire","New Hampshire","New Jersey","New Jersey","New Mexico","New Mexico","New York","New York","North Carolina","North Carolina","North Dakota","North Dakota","Ohio","Ohio","Oklahoma","Oklahoma","Oregon","Oregon","Pennsylvania","Pennsylvania","Rhode Island","Rhode Island","South Carolina","South Carolina","South Dakota","South Dakota","Tennessee","Tennessee","Texas","Texas","Utah","Utah","Vermont","Vermont","Virginia","Virginia","Washington","Washington","West Virginia","West Virginia","Wisconsin","Wisconsin","Wyoming","Wyoming","Puerto Rico","Puerto Rico"],["income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent","income","rent"],[24476,747,32940,1200,27517,972,23789,709,29454,1358,32401,1125,35326,1123,31560,1076,43198,1424,25952,1077,27024,927,32453,1507,25298,792,30684,952,27247,782,30002,740,29126,801,24702,713,25086,825,26841,808,37147,1311,34498,1173,26987,824,32734,906,22766,740,26999,784,26249,751,30020,773,29019,1017,33172,1052,35075,1249,24457,809,31057,1194,26482,844,32336,775,27435,764,26207,766,27389,988,28923,885,30210,957,25454,836,28821,696,25453,808,28063,952,27928,948,29351,945,32545,1166,32318,1120,23707,681,29868,813,30854,828,null,464],[136,3,508,13,148,4,165,5,109,3,109,5,195,5,247,10,681,17,70,3,106,3,218,18,208,7,83,3,117,3,143,4,208,5,159,4,155,4,187,7,152,5,199,5,82,3,189,4,194,5,113,4,206,9,146,4,213,6,387,9,148,4,214,6,69,3,111,3,245,9,94,2,101,3,146,4,119,3,259,6,123,4,276,7,102,4,110,2,239,6,361,11,202,5,113,4,203,6,135,3,342,11,null,6]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>GEOID<\/th>\n      <th>NAME<\/th>\n      <th>variable<\/th>\n      <th>estimate<\/th>\n      <th>moe<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"pageLength":5,"columnDefs":[{"className":"dt-right","targets":[4,5]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"lengthMenu":[5,10,25,50,100]}},"evals":[],"jsHooks":[]}</script>

## Separate\_a character column into multiple columns

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

## Unite\_Multiple columns into one by pasting strings together

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

## 

---
title: Tidyverse Stringr Package
author: Sikai Huang
date: '2022-05-27'
slug: stringr-in-r
categories:
  - R
tags:
  - RStudio
---

The [**stringr**](https://stringr.tidyverse.org/index.html) package encompasses a series of verbs designed to make data manipulation work with strings as easy as possible, particular useful to wrangle the **survey data** (including string values).

## Essential packages


```r
library(stringr)
```

## Measure a string length


```r
fruits <- c(
  "apples and oranges and pears and bananas",
  "pineapples and mangos and guavas")
str_length(fruits) # Results include the whitespace
```

```
## [1] 40 32
```

## Combine multiple strings into a string


```r
str_c(fruits, collapse = " and ")
```

```
## [1] "apples and oranges and pears and bananas and pineapples and mangos and guavas"
```

## Extract and replace substrings from a character vector

If a vector contains multiple strings, it will return the subset of each string


```r
str_sub(fruits, 1, 6) 
```

```
## [1] "apples" "pineap"
```

## **Keep strings matching a pattern, or find positions**


```r
str_subset(fruits, "mangos")
```

```
## [1] "pineapples and mangos and guavas"
```

## **Detect the presence or absence of a pattern**


```r
str_detect(fruits, "pears")
```

```
## [1]  TRUE FALSE
```

```r
str_detect(fruits, "^apples") # "^" refers to the string that starts with pattern
```

```
## [1]  TRUE FALSE
```

```r
str_detect(fruits, "guavas$") # "$" refers to the string that ends with pattern
```

```
## [1] FALSE  TRUE
```

## Counts the number of patterns


```r
str_count(fruits, "and")
```

```
## [1] 3 2
```

## **Locate the position of patterns**


```r
str_locate(fruits, "banana")
```

```
##      start end
## [1,]    34  39
## [2,]    NA  NA
```

## **Extract matching patterns from a string**


```r
str_extract(fruits, "bananas")
```

```
## [1] "bananas" NA
```

## Replaces the matches with new text


```r
str_replace(fruits, "s", "") # replace the first matched pattern
```

```
## [1] "apple and oranges and pears and bananas"
## [2] "pineapple and mangos and guavas"
```

```r
str_replace_all(fruits, "s", "") # replace all matached components with new text in a string
```

```
## [1] "apple and orange and pear and banana"
## [2] "pineapple and mango and guava"
```

## Split up a string into pieces


```r
fruits <- c(
  "apples and oranges and pears and bananas",
  "pineapples and mangos and guavas")
str_split(fruits, " and ") # return a list
```

```
## [[1]]
## [1] "apples"  "oranges" "pears"   "bananas"
## 
## [[2]]
## [1] "pineapples" "mangos"     "guavas"
```

Using **unlist()** or **unnest()** to convert a list to a vector


```r
unlist(strsplit(fruits, " and "))
```

```
## [1] "apples"     "oranges"    "pears"      "bananas"    "pineapples"
## [6] "mangos"     "guavas"
```

## Cheat Sheet

[![](images/stringr.png)](https://stringr.tidyverse.org/index.html)

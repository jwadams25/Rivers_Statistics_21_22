KEY - Tutorial 1: Introduction to R and RStudio
================
Mr. Adams

-   [Welcome to R and RStudio!](#welcome-to-r-and-rstudio)
-   [By the end of this tutorial I should be able
    to…](#by-the-end-of-this-tutorial-i-should-be-able-to)
    -   [1: Describe what a package is and know when to run a
        library.](#1-describe-what-a-package-is-and-know-when-to-run-a-library)
        -   [1.1: Tasks and Questions](#11-tasks-and-questions)
    -   [2: Use R as a calculator](#2-use-r-as-a-calculator)
        -   [2.1: Tasks and Questions](#21-tasks-and-questions)
    -   [3: Name functions](#3-name-functions)
        -   [3.1: Tasks and Questions](#31-tasks-and-questions)
    -   [4: Create a vector](#4-create-a-vector)
        -   [4.1: Tasks and Questions](#41-tasks-and-questions)
    -   [5: Create a data frame](#5-create-a-data-frame)
        -   [5.1: Tasks and Questions](#51-tasks-and-questions)
        -   [5.2: Tasks and Questions](#52-tasks-and-questions)

# Welcome to R and RStudio!

Congratulations! You are taking the first step toward becoming a data
scientist. R is a powerful statistical programming language and RStudio,
the IDE (integrated development area), is the place where we will do our
work with R.

This tutorial is the first in a series of tutorials that will help you
begin to learn how to to explore data using R.

# By the end of this tutorial I should be able to…

## 1: Describe what a package is and know when to run a library.

If you were to build something, you would need to get some tools and
organize those tools in various toolboxes. To build a house you’d need a
variety of toolboxes because there are many different types of things
you need to get done. For example, building the frame would require
different set of tools than painting all of the rooms.

When working with R you can think of packages as your toolboxes. They
are made up of various functions that make certain tasks easier.
However, before using them, you need to go buy them and then pick them
up off the shelf. Running the line library(package\_name) is equivalent
to grabbing your toolbox off the shelf before you start to work. If you
don’t grab the toolbox off of the shelf or, in other words, run the
libraries, your code will not run.

Long story short…run the libraries code first!

Tidyverse is a very robust package that we will use all of the time.

knitr is a package that will allow you to turn your rmarkdown file
(where you are working right now) into a format that is a bit easier to
read like a pdf, html, or github file.

### 1.1: Tasks and Questions

1.  ***Run the following code by clicking the green play button.***

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✓ ggplot2 3.3.5     ✓ purrr   0.3.4
    ## ✓ tibble  3.1.5     ✓ dplyr   1.0.7
    ## ✓ tidyr   1.1.4     ✓ stringr 1.4.0
    ## ✓ readr   2.0.2     ✓ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(knitr)
```

## 2: Use R as a calculator

At its most basic level, R can be used as a calculator. Keep your phone
in your pocket and stay on task if you need to perform a calculation.

### 2.1: Tasks and Questions

1.  ***Below is an example of a calculation. In the gray space below,
    write your own calculation and then hit the play button.***

2.  ***Write another calculation that requires you to add two numbers
    together and then divide that sum by 3.***

``` r
#Example
3+2
```

    ## [1] 5

``` r
#1 - Type your calculation below
2+5
```

    ## [1] 7

``` r
#2 - Type your calculation below
(2+13)/3
```

    ## [1] 5

## 3: Name functions

As you start to explore data, you will have many lines of code that
create many statistics and visualizations. Staying organized is
important. One way to do that is naming certain chunks of code. When you
want to run that code again, you run the name of the code instead of the
whole long chunk.

name &lt;- thing you want to name

(Note: That little arrow is made by typing the greater than sign and
minus sign on keyboard)

Naming tips:

-   use \_ instead of spaces. Example john\_adams
-   keep it short yet something that will help you remember what it
    represents. Ex. grades\_hist could be used to name a histogram
    showing the distributions of grades.

### 3.1: Tasks and Questions

1.  ***Copy one of the calculations you did in 2.1 Tasks and Questions
    and paste it into the gray section below.***

2.  ***Give your calculations a name and add the arrow.***

3.  ***Type the name of your calculation on the line below what you did
    for question 2 and then run the code.***

4.  ***Create and name 2 more calculations.***

5.  ***Use the names to multiply all of your equations together.***

``` r
adams_calcs <- (2+13)/3
adams_calcs
```

    ## [1] 5

``` r
second_calc <- 3*4
third_calc <- 6/2

adams_calcs*second_calc*third_calc
```

    ## [1] 180

## 4: Create a vector

A vector is a sequence of either numbers or characters. Here are some
examples.

#### Here is an example of a numeric vector

In this example, we create a vector of numeric values and then give it a
name. rivers\_numeric\_vector is written on a line of its own so we can
see a printout of the vector.

``` r
rivers_numeric_vector <- c(1915,333,6,12)

rivers_numeric_vector
```

    ## [1] 1915  333    6   12

**In this example, we create a vector of characters and then give it a
name.**

Remember, run the name of the vector by itself to see it.

``` r
rivers_character_vector <- c("red", "white", "black", "gray")

rivers_character_vector
```

    ## [1] "red"   "white" "black" "gray"

### 4.1: Tasks and Questions

In the gray space below…

1.  ***Create and name a numeric vector.***

2.  ***Create and name a character vector.***

Bonus: Name the significance of each number in the vector created above
titled, rivers\_numeric\_vector.

1915 = The year Rivers was founded

333 = Rivers is located at 333 Winter St. 

6 = 6th Grade. The start of your Rivers journey

12 = 12th Grade. The end of your Rivers journey.

``` r
# 1. Create and name our numeric vector in the line below. 
adams_num <- c(1,2,3,4)

# 2. Create and name your character vector in the line below.

adams_char <- c("stats", "is", "the", "best")
```

## 5: Create a data frame

As you’ve learned before, we will want our data frames organized as tidy
datasets. When data is organized in such a way, each column is a
variable and the rows are for each observational unit or case.

Most often, we will load in data to Rstudio or use data included within
various packages. For this exercise, we will build a data frame.

Here is an example of a data frame. Use it to answer the tasks and
questions section below.

``` r
rivers_data <- data.frame(
                    important_numbers = c(1915,333,6,12),
                    riv_colors = c("red", "white", "black", "gray")
                    )
rivers_data
```

    ##   important_numbers riv_colors
    ## 1              1915        red
    ## 2               333      white
    ## 3                 6      black
    ## 4                12       gray

### 5.1: Tasks and Questions

1.  ***What is the name of this data frame? Type it EXACTLY how it
    appears in the code above.*** rivers\_data

2.  ***How many variables are in this data frame and what are their
    names? Type the names EXACTLY how they appear in the code above.***
    2 variables important\_numbers riv\_colors

3.  ***What types of variables are they?*** important\_numbers =
    numerical riv\_colors = categorical

4.  ***How many observations are in this data frame?***

4

### 5.2: Tasks and Questions

1.  ***In the gray space below, create and name a data frame that
    includes two variables and 4 observations.***

``` r
# 1: Create and name your data frame in the lines below.

adams_data <- data.frame(
                adams_num = c(1,2,3,4),
                adams_char = c("stats", "is", "the", "best")
                )

adams_data
```

    ##   adams_num adams_char
    ## 1         1      stats
    ## 2         2         is
    ## 3         3        the
    ## 4         4       best

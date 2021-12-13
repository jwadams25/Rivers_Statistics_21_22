KEY_5\_Least_Squares_Regression
================
Mr. Adams

-   [Overview](#overview)
-   [Goals](#goals)
-   [Libraries](#libraries)
-   [1: Structured Walk-Through](#1-structured-walk-through)
    -   [1.1: The Data](#11-the-data)
        -   [1.1: Tasks and Questions](#11-tasks-and-questions)
    -   [1.2: The Plot](#12-the-plot)
        -   [1.2: Tasks and Questions](#12-tasks-and-questions)
    -   [1.3: The Model](#13-the-model)
        -   [1.3: Tasks and Questions](#13-tasks-and-questions)
    -   [1.4: Interpreting the Model](#14-interpreting-the-model)
        -   [1.4: Tasks and Questions](#14-tasks-and-questions)
-   [2: Build Your Own Scatter Plot and
    Model](#2-build-your-own-scatter-plot-and-model)
    -   [2.1: Learn about the Data](#21-learn-about-the-data)
    -   [2.2: Build the scatter plot with the linear model
        included](#22-build-the-scatter-plot-with-the-linear-model-included)
    -   [2.3: Generate the equation of the least squares regression
        line.](#23-generate-the-equation-of-the-least-squares-regression-line)
    -   [2.4: Generate the correlation
        coefficient](#24-generate-the-correlation-coefficient)
    -   [2.5: Using what you just calculated, describe the relationship
        between prices of textbooks on Amazon and the UCLA book store.
        In your answer you should reference the slope and the
        correlation.](#25-using-what-you-just-calculated-describe-the-relationship-between-prices-of-textbooks-on-amazon-and-the-ucla-book-store-in-your-answer-you-should-reference-the-slope-and-the-correlation)
    -   [Sources:](#sources)

# Overview

Now that you’ve built a baseline understanding of least squares
regressions, you will learn to build scatter plots and generate linear
models here in RStudio.

# Goals

***By the end of this tutorial you should be able to…***

1.  Build a scatter plot that has a linear model.

2.  Generate the equation of the linear model.

3.  Interpret the linear regression model.

4.  Add design elements to the scatter plot to improve the labels,
    colors, and alpha.

# Libraries

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
library(openintro)
```

    ## Loading required package: airports

    ## Loading required package: cherryblossom

    ## Loading required package: usdata

``` r
library(knitr)
```

# 1: Structured Walk-Through

## 1.1: The Data

We had a great discussion in class about the relationship between gift
aid and family income for freshman at Elmhurst College after reading
chapter 7 in Introduction to Modern Statistics. Therefore, let’s start
by recreating the scatter plot and the linear model you saw in the
reading.

### 1.1: Tasks and Questions

``` r
?elmhurst
glimpse(elmhurst)
```

    ## Rows: 50
    ## Columns: 3
    ## $ family_income <dbl> 92.922, 0.250, 53.092, 50.200, 137.613, 47.957, 113.534,…
    ## $ gift_aid      <dbl> 21.720, 27.470, 27.750, 27.220, 18.000, 18.520, 13.000, …
    ## $ price_paid    <dbl> 14.280, 8.530, 14.250, 8.780, 24.000, 23.480, 23.000, 29…

#### a. What are the observational units and how many are there?

The observations are 50 random students gift aid from Elmhurst College.

#### b. What are the names of the two variables we will explore when answering the question, “Is there an association between family income and the amount of gift aid received?”

family_income gift_aid

#### c. What is the predictor variable?

family_income

#### d. What is the outcome variable?

gift_aid

## 1.2: The Plot

You will see in the code below the structure matches the code we used to
make other data visualizations. You ask the computer to reference a
dataset, make a plot with certain aesthetics, make a certain type of
plot, and add labels.

### 1.2: Tasks and Questions

#### a. Replace NAME_OF_DATASET with the name of the dataset.

#### b. Replace PREDICTOR and OUTCOME.

#### c. Change the labels for the x and y axes. Be sure to list the units.

``` r
elmhurst %>%
  ggplot(aes(x = family_income, y = gift_aid)) +
  geom_point() +
  labs(
    x = "Family Income of the Student ($1000s)", 
    y = "Gift Aid ($1000s)")
```

![](Key_5_Least_Squares_Regression_files/figure-gfm/build%20a%20scatter%20plot-1.png)<!-- -->

## 1.3: The Model

As you know, adding a least squares regression line to the plot and
generating an equation allows you to better quantify the association
between the two numerical values. You will now do both of those things
in the following sections of this tutorial.

### 1.3: Tasks and Questions

#### a. Add the line representing the linear model to scatter plot you just created. To do this, type “lm” after where you see method = in the code chunk below.

geom_smooth is the function that adds the line and the lm code you added
stands for linear model. When you progress to higher levels of
statistics and data science, you will add in different types of models
while also using geom_smooth.

``` r
elmhurst %>%
  ggplot(aes(x = family_income, y = gift_aid)) +
  geom_point() +
  geom_smooth(method = "lm", se = FALSE) +
  labs(
    x = "Family Income of the Student ($1000s)", 
    y = "Gift Aid ($1000s)")
```

    ## `geom_smooth()` using formula 'y ~ x'

![](Key_5_Least_Squares_Regression_files/figure-gfm/add%20the%20model-1.png)<!-- -->

#### b. Generate the intercept and slope of the model by replacing NAME_OF_DATASET, PREDICTOR, and OUTCOME in the code chunk below.

#### c. Write the equation.

gift_aid = 24.32 - 0.04307(family_income)

``` r
lm(data = elmhurst, formula = gift_aid~family_income)
```

    ## 
    ## Call:
    ## lm(formula = gift_aid ~ family_income, data = elmhurst)
    ## 
    ## Coefficients:
    ##   (Intercept)  family_income  
    ##      24.31933       -0.04307

#### d. Using what you learned during the correlation tutorial, find the mean and standard deviation of each variable along with the correlation coefficient.

``` r
elmhurst %>%
  summarise(
    mean_income = mean(family_income), 
    sd_income = sd(family_income), 
    mean_aid = mean(gift_aid), 
    sd_aid = sd(gift_aid),
    r = cor(gift_aid,family_income)
  )
```

    ## # A tibble: 1 × 5
    ##   mean_income sd_income mean_aid sd_aid      r
    ##         <dbl>     <dbl>    <dbl>  <dbl>  <dbl>
    ## 1        102.      63.2     19.9   5.46 -0.499

## 1.4: Interpreting the Model

Getting the numbers is only part of the battle. Interpreting the model
properly and then clearly communicating that to others is essential. You
will now practice doing just that.

### 1.4: Tasks and Questions

#### a. Use the slope coefficient to describe the direction of the association.

This model tell us that for every additional $1000 dollars in a
student’s family income, they could expect to receive on average 43.07
fewer dollars in gift aid.

#### b. Use the correlation coefficient to describe the strength of the association.

Family income and gift aid have a fairly strong correlation given the
correlation coefficient of -0.4986. More specifically, roughly 24.86% of
the variation in gift aid can be explained a student’s family income.

#### c. If a family income of an incoming freshman student was $125,000, how much gift aid would the model predict they’d receive. USE THE EQUATION to find this. DO NOT JUST LOOK AT THE SCATTER PLOT!! Remember r can be used as calculator.

This model predicts that a student at Elmhurst College who’s family
earns and income of $125,000, can expect to receive 18,935.58. However,
it is worth noting that given the fact that the there isn’t perfect
correlation and the data was for just 50 freshman students in one year,
the prediction we got should only be used as an estimate.

``` r
# find slope in thousands
-0.04307*1000
```

    ## [1] -43.07

``` r
# find r-squared
-0.4985561^2
```

    ## [1] -0.2485582

``` r
# Make prediction
(24.31933-0.04307*(125))*1000
```

    ## [1] 18935.58

# 2: Build Your Own Scatter Plot and Model

The Question you will explore is: “Are textbooks at UCLA’s bookstore
overpriced in relation to the same ones sold on Amazon?” This section is
modeled after a tutorial developed in Introduction to Modern Statistics.

## 2.1: Learn about the Data

``` r
?textbooks
```

## 2.2: Build the scatter plot with the linear model included

Before you dive into the coding, you may want to draw a quick sketch of
the plot you want to create so you know which variables go on which
axis. You Can do this on paper, your iPad, or the board. Tip: Amazon_new
will be the predictor variable.

``` r
textbooks %>%
  ggplot(aes(x = amaz_new, y = ucla_new)) +
  geom_point() +
  geom_smooth(method = "lm", se = FALSE) +
  labs(
    x = "Price of Textbook on Amazon.com", 
    y = "Price of Textbook at the UCLA Bookstore"
  )
```

    ## `geom_smooth()` using formula 'y ~ x'

![](Key_5_Least_Squares_Regression_files/figure-gfm/textbook%20viz-1.png)<!-- -->

## 2.3: Generate the equation of the least squares regression line.

``` r
lm(data = textbooks, formula = ucla_new ~ amaz_new)
```

    ## 
    ## Call:
    ## lm(formula = ucla_new ~ amaz_new, data = textbooks)
    ## 
    ## Coefficients:
    ## (Intercept)     amaz_new  
    ##       0.929        1.199

## 2.4: Generate the correlation coefficient

``` r
textbooks %>%
  summarise(
    r = cor(ucla_new, amaz_new)
  )
```

    ## # A tibble: 1 × 1
    ##       r
    ##   <dbl>
    ## 1 0.985

## 2.5: Using what you just calculated, describe the relationship between prices of textbooks on Amazon and the UCLA book store. In your answer you should reference the slope and the correlation.

The correlation coefficient of 0.9846 is a very strong relationship
between the price of textbooks on Amazon and at the UCLA bookstore.
However, given the slope is 1.20, we can expect that for every
additional dollar a textbook is on Amazon, a book at the book store will
go up by $1.20 on average. This tells us that books at the book store
tend to be 20% more expensive than their counterpart on Amazon.

## Sources:

<https://openintro-ims.netlify.app/model-slr.html>
<https://openintro.shinyapps.io/ims-03-model-04/#section-data-set-up>

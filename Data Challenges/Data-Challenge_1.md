Data Challenge 1
================

-   [Overview](#overview)
-   [What you will do](#what-you-will-do)
-   [Logistics](#logistics)
-   [Libraries you will need.](#libraries-you-will-need)
-   [The Data](#the-data)
-   [Explore your questions](#explore-your-questions)
-   [Choose the two main questions you want to
    answer](#choose-the-two-main-questions-you-want-to-answer)
-   [Answering your first question](#answering-your-first-question)
-   [Answering your second question](#answering-your-second-question)

# Overview

You now understand how to utilize many tools that will allow you to
explore data and begin to uncover stories hidden within data. This
challenge will allow you to put those tools to work!

# What you will do

1.  Gain an understanding of the dataset and generate questions you
    could explore with it.

2.  Explore the data and the questions you asked by generating
    visualizations and the supporting summary statistics.

3.  Produce at least two data visualizations that include the design
    elements we discussed, summary statistics to support them, and a
    written description of each.

# Logistics

Time Frame: 1 Week

Group Work: You can work with those in your assigned group, but you must
produce your own rMarkdown file. All of your work will be done in this
rMarkdown file. Your work includes the code and descriptions you write.

# Libraries you will need.

``` r
library(tidyverse)
library(openintro)
library(skimr)
library(knitr)
library(kableExtra)
library(gridExtra)
library(ggridges)
```

# The Data

In the next unit, you will dive into linear regression models to learn
how to make predictions and assess whether variables have a
relationship. The authors of our textbook Introduction to Modern
Statistics, Mine Çetinkaya-Rundel and Jo Hardin, will reference a
dataset called, possum, which consists of data on…you guessed it -
possums, as they walk through linear regression models. Before getting
to that reading, you can utilize your newly formed EDA skills to build
an understanding of the possum dataset.

This data challenge is where you will explore the possum dataset!

``` r
?possum
view(possum)
glimpse(possum)
```

    ## Rows: 104
    ## Columns: 8
    ## $ site    <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1,…
    ## $ pop     <fct> Vic, Vic, Vic, Vic, Vic, Vic, Vic, Vic, Vic, Vic, Vic, Vic, Vi…
    ## $ sex     <fct> m, f, f, f, f, f, m, f, f, f, f, f, m, m, m, m, f, m, f, f, f,…
    ## $ age     <int> 8, 6, 6, 6, 2, 1, 2, 6, 9, 6, 9, 5, 5, 3, 5, 4, 1, 2, 5, 4, 3,…
    ## $ head_l  <dbl> 94.1, 92.5, 94.0, 93.2, 91.5, 93.1, 95.3, 94.8, 93.4, 91.8, 93…
    ## $ skull_w <dbl> 60.4, 57.6, 60.0, 57.1, 56.3, 54.8, 58.2, 57.6, 56.3, 58.0, 57…
    ## $ total_l <dbl> 89.0, 91.5, 95.5, 92.0, 85.5, 90.5, 89.5, 91.0, 91.5, 89.5, 89…
    ## $ tail_l  <dbl> 36.0, 36.5, 39.0, 38.0, 36.0, 35.5, 36.0, 37.0, 37.0, 37.5, 39…

***1. Write a description of the data.***

Be sure you’ve run both the run the code above and looked through each
of their respective outputs so you can be specific when describing the
data.

***2. Write down 4 questions you could explore with these data?***

1.  
2.  
3.  
4.  

# Explore your questions

***1. Now that you understand the variables and have a few questions,
start to use your R skills to explore the data.***

As you do this task, do not go crazy with styling. Just get the base
data visualizations and statistics generated so you can start to see
learn about these possums.

Think of this as the drawing board. You may even want to draw rough
sketches of the visualizations you could create on the board or on your
iPad. After you go through this task, you will be able to say, “Ok team,
we’ve made a bunch of visualizations and should clean up these two
visualizations to use in our final report.”

# Choose the two main questions you want to answer

Now that you have a better sense of your data and have explored your
questions, you will choose two questions and answer them by producing
data visualizations utilizing data viz best practices and the necessary
statistics to support them. In addition, you will have to describe the
distributions or bar graphs you create. USE NUMBERS! USE COURSE
VOCABULARY! Bring context to the numbers and vocab.

Write each question below.

***Question 1***

***Question 2***

# Answering your first question

In this section, you will clean up your visualizations and generate the
necessary summary statistics or tables to support those visualizations.
You are now in the phase where you want to foucs on clear and effective
communication - organized code, data visualizations include some data
viz best practices, and descriptions give context to the numbers and
visualizations you’ve generated.

***1. Code for first data visualization and supporting summary
statistics.***

***2. Description to help answer your first question.***

# Answering your second question

***1. Code for second data visualization and supporting summary
statistics.***

***2. Description to help answer your second question.***

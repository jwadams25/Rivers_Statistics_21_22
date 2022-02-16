KEY 7 Confidence Intervals with Bootstrapping, Part 2
================
John Adams

-   [Overview](#overview)
-   [Goals](#goals)
-   [1: Get Ready to Go](#1-get-ready-to-go)
    -   [1.1: Packages](#11-packages)
        -   [1.1: Tasks and Questions](#11-tasks-and-questions)
    -   [1.2: Set Seed](#12-set-seed)
        -   [1.2: Tasks and Questions](#12-tasks-and-questions)
-   [2: Recreate the Marble Activity](#2-recreate-the-marble-activity)
    -   [2.1: Create your sample.](#21-create-your-sample)
        -   [2.1: Tasks and Questions](#21-tasks-and-questions)
-   [3: Generate Bootstrapped Samples](#3-generate-bootstrapped-samples)
    -   [3.1: Tasks and Questions](#31-tasks-and-questions)
    -   [3.2: Tasks and Questions](#32-tasks-and-questions)
-   [4: THE CHALLENGE](#4-the-challenge)
    -   [4.1: Youtube - Tasks and
        Questions](#41-youtube---tasks-and-questions)
    -   [4.1: Illness - Tasks and
        Questions](#41-illness---tasks-and-questions)
    -   [4.1: Twitter - Tasks and
        Questions](#41-twitter---tasks-and-questions)

# Overview

This activity builds on the one you did with the marbles. As you saw in
that activity, generating a lot of bootstrapped portions takes a long
time! Let’s let the computer do the work! This activity will walk you
through how you can generate thousands of bootstrapped proportions and
construct a confidence interval. What you learn in this activity will
allow you to make your statistical research more sophisticated.

***Start by changing YOUR NAME to your name. This can be found at the
top of this document next to author.***

# Goals

***By the end of this tutorial you should be able to…***

1.  Ask a statistical question that would lead one to generate a
    confidence interval.

2.  Write code to generate a histogram of the bootstrapped distribution.

3.  Write code to generate a confidence interval with bootstrapping.

4.  Interpret the confidence interval you generate.

# 1: Get Ready to Go

## 1.1: Packages

As always, you want to grab the necessary “toolboxes” to complete the
work you are about to do. You’ll use the same packages used in part one:
tidyverse, openintro, and infer.

### 1.1: Tasks and Questions

#### a. Run the following code chunk.

``` r
library(tidyverse)
library(openintro)
library(infer)
```

## 1.2: Set Seed

Some of the code you will run later will involve randomness. Therefore,
you’ll want to set the seed first.

### 1.2: Tasks and Questions

#### a. Double click on PUT_ANY_NUMBER_HERE, hit delete, and enter any number.

``` r
set.seed(1935)
```

# 2: Recreate the Marble Activity

## 2.1: Create your sample.

The first thing you did in the marble activity was select a sample of 20
marbles. When researching, that will be the step you take after
generating your research question. When you collect a random sample from
a population, you will collect data and organize it into a tidy data
set. To recreate our marble activity, you need to create the sample you
selected. That is what you will do in this section.

### 2.1: Tasks and Questions

#### a. You need to give your data frame a name. Therefore, change NAME_OF_DATA_FRAME to marble_data.

#### b. Tibble is the function that will create the data frame. In that data frame, you will have one variable called marble_color. Find the portion of the code where the name of the variable should go. Then, replace that code with marble_color.

#### c. Change MARBLE_COLOR_1 and MARBLE_COLOR_2 to blue and green respectively.

#### d. Change NUMBER_OF_MARBLE_1 to the number of blue marbles in your sample of marbles you selected in tutorial 7 part 1. ie How many blue marbles did you physically select when you originally did the activity in class?

#### e. Change NUMBER_OF_MARBLE_2 to the number of green marbles in your sample of marbles you selected in tutorial 7 part 1. ie How many green marbles did you physically select when you originally did the activity in class?

#### f. Run the code chunk and look over the data frame you created.

``` r
marble_data <- tibble(marble_color = c(rep("blue", 13), rep("green", 7)))

marble_data
```

    ## # A tibble: 20 × 1
    ##    marble_color
    ##    <chr>       
    ##  1 blue        
    ##  2 blue        
    ##  3 blue        
    ##  4 blue        
    ##  5 blue        
    ##  6 blue        
    ##  7 blue        
    ##  8 blue        
    ##  9 blue        
    ## 10 blue        
    ## 11 blue        
    ## 12 blue        
    ## 13 blue        
    ## 14 green       
    ## 15 green       
    ## 16 green       
    ## 17 green       
    ## 18 green       
    ## 19 green       
    ## 20 green

# 3: Generate Bootstrapped Samples

Now that we have our sample, you can simulate the bootstrapping process.
Or, in other words, we can sample 20 marbles, with replacement, from our
sample, calculate a proportion, and then repeat that process many, many
times. In this activity, we will repeat that process 1,000 times. Let’s
GO!

### 3.1: Tasks and Questions

#### a. Change NAME_OF_VARIABLE, COLOR, and NUMBER_OF_REPS in the code below so that the computer looks at the marble_color variable, counts blue as a success as it generates bootstrapped samples and calculates the proportion.

#### b. Why does your new data frame have 1000 rows?

We resampled 20 marbles (with replacement) from the sample data recorded
a proportion and then repeated that process 999 more times. As a result,
we now have a data frame that includes the 1000 proportions calculated
in that process and the trial number.

#### c. What does the each number listed under the variable stat in the new data frame represent?

Each number represents the bootstrapped proportion. Or in other words,
it is the proportion of blue marlbes in the 20 marbles we selected when
resampling 20 marbles from the sample.

``` r
bootstrapped_proportions <- marble_data %>%
                              specify(response = marble_color, success = "blue") %>%
                              generate(reps = 1000, type = "bootstrap") %>%
                              calculate(stat = "prop") 

bootstrapped_proportions
```

    ## Response: marble_color (factor)
    ## # A tibble: 1,000 × 2
    ##    replicate  stat
    ##        <int> <dbl>
    ##  1         1  0.6 
    ##  2         2  0.65
    ##  3         3  0.65
    ##  4         4  0.8 
    ##  5         5  0.7 
    ##  6         6  0.6 
    ##  7         7  0.7 
    ##  8         8  0.8 
    ##  9         9  0.65
    ## 10        10  0.75
    ## # … with 990 more rows

### 3.2: Tasks and Questions

#### a. Edit the code below to create a histogram showing the distribution of bootstrapped proportions. Be sure to add in a title and lables for the x and y axes.

Hint: Look closely at the code above to be sure you know what the name
of the data frame is and the name of the variable is that represents the
bootstrapped proportions.

#### b. Using the visualization, estimate a 95% confidence interval for the proportion of blue marbles in the population.

Lower bound \~0.45 Upper bound \~.85

How I got these numbers. 25 is 2.5% of 1000. When you have a 95%
confidence interval, you want to exclude the lowest 2.5% and the highest
2.5% so you are left with the middle 95% of the data. In this case, I
first counted the bar heights on the left until I got to 25 and ended up
at 0.45. As a result, 0.45 was my lower bound. I then counted the bar
heights from the far right, working my way to the left until, I got to a
combined bar height of 25. This left me at 0.85 as my upper bound.

#### c. Interpret the confidence interval you found in part b.

We can be 95% confident that between 45% and 85% of the marbles in the
population are blue.

``` r
  bootstrapped_proportions    %>%
  ggplot(aes(x = stat)) +
  geom_histogram() +
  labs(
    title = "1,000 Bootstrapped Proportions",
    x = "Bootstrapped Proportion of Blue Marbles",
    y = "Count",
  )
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Key_7_Confidence_Intervals_with_Bootstrapping_pt_2_files/figure-gfm/visualize%20bootstrapped%20props-1.png)<!-- -->
### 3.3: Generate the Confidence Inteval

In the last section, you estimated the confidence interval. In this
part, you will adjust the code to generate the a 95% Confidence
Interval.

#### 3.3: Tasks and Questions

#### a. Adjust the code below to construct a 95% confidence interval.

***Tips: You are going to use the data frame that contains the 1000
bootstrapped proportions.***

#### b. How accurate was your estimate of the confidence interval in 3.2 part b in relation to what you got from running the code below.

It was the same thing.

``` r
bootstrapped_proportions %>%
  select(stat) %>%
  get_confidence_interval(level = 0.95) 
```

    ## # A tibble: 1 × 2
    ##   lower_ci upper_ci
    ##      <dbl>    <dbl>
    ## 1     0.45     0.85

# 4: THE CHALLENGE

On the homework problems in chapter 12 of Introduction to Modern
Statistics, you were asked to analyze distributions of bootstrapped
proportions. The challenge you have now is to recreate one of those
histograms and construct a confidence interval using the tools you
learned above. This is a very challenging task!

Think - Ask Questions - Review and use the code above - Collaborate -
Edit - Stay Patient - Fierce Positivity!

### 4.1: Youtube - Tasks and Questions

#### a. Choose one of the following questions from the chapter 12 exercises: 1, 2, or 3.

1

#### b. Create a data frame that represents the sample data described in the question.

``` r
youtube_sample_data <- tibble(video_location = c(rep("outside", 37), rep("inside", 91)))

youtube_sample_data
```

    ## # A tibble: 128 × 1
    ##    video_location
    ##    <chr>         
    ##  1 outside       
    ##  2 outside       
    ##  3 outside       
    ##  4 outside       
    ##  5 outside       
    ##  6 outside       
    ##  7 outside       
    ##  8 outside       
    ##  9 outside       
    ## 10 outside       
    ## # … with 118 more rows

#### c. Create 1000 boostrapped sample proportions.

``` r
youtube_bootstrapped_proportions <- youtube_sample_data %>%
                              specify(response = video_location, success = "outside") %>%
                              generate(reps = 1000, type = "bootstrap") %>%
                              calculate(stat = "prop") 

youtube_bootstrapped_proportions
```

    ## Response: video_location (factor)
    ## # A tibble: 1,000 × 2
    ##    replicate  stat
    ##        <int> <dbl>
    ##  1         1 0.258
    ##  2         2 0.336
    ##  3         3 0.164
    ##  4         4 0.328
    ##  5         5 0.297
    ##  6         6 0.273
    ##  7         7 0.305
    ##  8         8 0.344
    ##  9         9 0.352
    ## 10        10 0.328
    ## # … with 990 more rows

#### d. Create a histogram showing the distribution of those 1000 bootstrapped proportions.

``` r
youtube_bootstrapped_proportions %>%
  ggplot(aes(x = stat)) +
  geom_histogram(color = "white", fill = "navy") +
  labs(
    title = "1,000 Bootstrapped Proportions",
    x = "Bootstrapped Proportion of Outdoor Videos",
    y = "Count",
  )
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Key_7_Confidence_Intervals_with_Bootstrapping_pt_2_files/figure-gfm/boot%20hist%20youtube-1.png)<!-- -->

#### e. Generate a 95% confidence interval and interpret it.

We can be 95% confident that between 21.88% and 36.72% of Youtube videos
take place outdoors.

``` r
youtube_bootstrapped_proportions %>%
  select(stat) %>%
  get_confidence_interval(level = 0.95) 
```

    ## # A tibble: 1 × 2
    ##   lower_ci upper_ci
    ##      <dbl>    <dbl>
    ## 1    0.219    0.367

### 4.1: Illness - Tasks and Questions

#### a. Choose one of the following questions from the chapter 12 exercises: 1, 2, or 3.

2

#### b. Create a data frame that represents the sample data described in the question.

``` r
illness_sample_data <- tibble(chronic = c(rep("yes", 1658), rep("no", 1356)))

illness_sample_data
```

    ## # A tibble: 3,014 × 1
    ##    chronic
    ##    <chr>  
    ##  1 yes    
    ##  2 yes    
    ##  3 yes    
    ##  4 yes    
    ##  5 yes    
    ##  6 yes    
    ##  7 yes    
    ##  8 yes    
    ##  9 yes    
    ## 10 yes    
    ## # … with 3,004 more rows

#### c. Create 1000 boostrapped sample proportions.

``` r
illness_bootstrapped_proportions <- illness_sample_data %>%
                              specify(response = chronic, success = "yes") %>%
                              generate(reps = 1000, type = "bootstrap") %>%
                              calculate(stat = "prop") 

illness_bootstrapped_proportions
```

    ## Response: chronic (factor)
    ## # A tibble: 1,000 × 2
    ##    replicate  stat
    ##        <int> <dbl>
    ##  1         1 0.554
    ##  2         2 0.544
    ##  3         3 0.561
    ##  4         4 0.551
    ##  5         5 0.563
    ##  6         6 0.560
    ##  7         7 0.545
    ##  8         8 0.538
    ##  9         9 0.552
    ## 10        10 0.551
    ## # … with 990 more rows

#### d. Create a histogram showing the distribution of those 1000 bootstrapped proportions.

``` r
illness_bootstrapped_proportions %>%
  ggplot(aes(x = stat)) +
  geom_histogram(color = "white", fill = "navy") +
  labs(
    title = "1,000 Bootstrapped Proportions",
    x = "Bootstrapped Proportion of Those with Chronic Illness",
    y = "Count",
  )
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Key_7_Confidence_Intervals_with_Bootstrapping_pt_2_files/figure-gfm/boot%20hist%20illness-1.png)<!-- -->

#### e. Generate a 95% confidence interval and interpret it.

We can be 95% confident that between 53.28% and 56.93% of US adults live
with one or more chronic conditions.

``` r
illness_bootstrapped_proportions %>%
  select(stat) %>%
  get_confidence_interval(level = 0.95)
```

    ## # A tibble: 1 × 2
    ##   lower_ci upper_ci
    ##      <dbl>    <dbl>
    ## 1    0.532    0.568

### 4.1: Twitter - Tasks and Questions

#### a. Choose one of the following questions from the chapter 12 exercises: 1, 2, or 3.

3

#### b. Create a data frame that represents the sample data described in the question.

``` r
twitter_sample_data <- tibble(twitter_news = c(rep("no", 353), rep("yes", 383)))

twitter_sample_data
```

    ## # A tibble: 736 × 1
    ##    twitter_news
    ##    <chr>       
    ##  1 no          
    ##  2 no          
    ##  3 no          
    ##  4 no          
    ##  5 no          
    ##  6 no          
    ##  7 no          
    ##  8 no          
    ##  9 no          
    ## 10 no          
    ## # … with 726 more rows

#### c. Create 1000 boostrapped sample proportions.

``` r
twitter_bootstrapped_proportions <- twitter_sample_data %>%
                              specify(response = twitter_news, success = "yes") %>%
                              generate(reps = 1000, type = "bootstrap") %>%
                              calculate(stat = "prop") 

twitter_bootstrapped_proportions
```

    ## Response: twitter_news (factor)
    ## # A tibble: 1,000 × 2
    ##    replicate  stat
    ##        <int> <dbl>
    ##  1         1 0.522
    ##  2         2 0.510
    ##  3         3 0.504
    ##  4         4 0.533
    ##  5         5 0.492
    ##  6         6 0.542
    ##  7         7 0.527
    ##  8         8 0.523
    ##  9         9 0.510
    ## 10        10 0.507
    ## # … with 990 more rows

#### d. Create a histogram showing the distribution of those 1000 bootstrapped proportions.

``` r
twitter_bootstrapped_proportions %>%
  ggplot(aes(x = stat)) +
  geom_histogram(color = "white", fill = "navy") +
  labs(
    title = "1,000 Bootstrapped Proportions",
    x = "Bootstrapped Proportion of those\nwho get their news from Twitter",
    y = "Count",
  )
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Key_7_Confidence_Intervals_with_Bootstrapping_pt_2_files/figure-gfm/boot%20hist%20Twitter-1.png)<!-- -->

#### e. Generate a 95% confidence interval and interpret it.

We can be 95% confident that the true propotion of US adult Twitter
users in 2013 got at least some of their news from Twitter.

``` r
twitter_bootstrapped_proportions %>%
  select(stat) %>%
  get_confidence_interval(level = 0.95)
```

    ## # A tibble: 1 × 2
    ##   lower_ci upper_ci
    ##      <dbl>    <dbl>
    ## 1    0.485    0.557

Sources:
<https://openintro-ims.netlify.app/foundations-bootstrapping.html#chp12-exercises>
<https://github.com/OpenIntroStat/ims/blob/main/exercises/12-ex-foundations-bootstrapping.Rmd>

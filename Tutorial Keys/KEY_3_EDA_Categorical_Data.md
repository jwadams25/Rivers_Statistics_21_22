KEY\_3\_EDA\_Categorical\_Data
================
Mr. Adams

-   [EDA with Categorical Data](#eda-with-categorical-data)
-   [Libraries](#libraries)
-   [1: Exploring One Categorical
    Variable](#1-exploring-one-categorical-variable)
    -   [1.1 Data for Part One](#11-data-for-part-one)
        -   [1.1: Tasks and Questions](#11-tasks-and-questions)
    -   [1.2 Build a table](#12-build-a-table)
        -   [1.2 Tasks and Questions](#12-tasks-and-questions)
    -   [1.3 Table with Proportions and
        Counts](#13-table-with-proportions-and-counts)
        -   [1.3 Tasks and Questions](#13-tasks-and-questions)
    -   [1.4 Arranging the table](#14-arranging-the-table)
        -   [1.4 Tasks and Questions](#14-tasks-and-questions)
    -   [1.5: Build a Bar Graph](#15-build-a-bar-graph)
        -   [1.5 Tasks and Questions](#15-tasks-and-questions)
    -   [1.6: Adjust bar graph to implement some data visualizations
        best
        practices.](#16-adjust-bar-graph-to-implement-some-data-visualizations-best-practices)
        -   [1.6a: Horizontal Bars and
            Labels](#16a-horizontal-bars-and-labels)
            -   [1.6a: Tasks and Questions](#16a-tasks-and-questions)
            -   [1.6b: Tasks and Questions](#16b-tasks-and-questions)
-   [2: Exploring Two Categorical
    Variables](#2-exploring-two-categorical-variables)
    -   [2.1: Contingency Table with
        Counts](#21-contingency-table-with-counts)
        -   [2.1: Tasks and Questions](#21-tasks-and-questions)
    -   [2.2: Contingency Table with
        Proportions.](#22-contingency-table-with-proportions)
        -   [2.2: Tasks and Questions](#22-tasks-and-questions)
    -   [2.3: Visualize Two Categorical Variables with a Filled Bar
        Plot](#23-visualize-two-categorical-variables-with-a-filled-bar-plot)
        -   [2.3a: Create a Filled Bar
            Graph](#23a-create-a-filled-bar-graph)
            -   [2.3a: Tasks and Questions](#23a-tasks-and-questions)
        -   [2.3b Adjust filled bar graph to include some data
            visualization best
            practices](#23b-adjust-filled-bar-graph-to-include-some-data-visualization-best-practices)
            -   [2.3b Tasks and Questions](#23b-tasks-and-questions)

# EDA with Categorical Data

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
library(janitor)
```

    ## 
    ## Attaching package: 'janitor'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     chisq.test, fisher.test

``` r
library(knitr)
library(kableExtra)
```

    ## 
    ## Attaching package: 'kableExtra'

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     group_rows

``` r
library(gridExtra)
```

    ## 
    ## Attaching package: 'gridExtra'

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     combine

``` r
library(readr)
library(openintro)
```

    ## Loading required package: airports

    ## Loading required package: cherryblossom

    ## Loading required package: usdata

# 1: Exploring One Categorical Variable

## 1.1 Data for Part One

To learn how you can explore one categorical variable using R, you will
use the data in the openintro packaged called immigration.

Copy and paste the link below to read a description of the dataset -
<http://openintrostat.github.io/openintro/reference/immigration.html>

### 1.1: Tasks and Questions

1.  Without running the code below, read the code and write down what
    the name of the data frame will be. (Be sure to type the name
    EXACTLY as it appears in the code)

immigration

2.  What are the observational units?

Registered voters in Tampa, FL who responded to this survey.

3.  How many observations are there? (You can now run the code to help
    answer this question.)

4.  List the two variables included in this data frame. Be sure to list
    the name of the variable exactly as it appears and label the type of
    each variable.

``` r
glimpse(immigration)
```

    ## Rows: 910
    ## Columns: 2
    ## $ response  <fct> Apply for citizenship, Apply for citizenship, Apply for citi…
    ## $ political <fct> conservative, conservative, conservative, conservative, cons…

## 1.2 Build a table

Now that you have an understanding of the data, let’s start exploring.

To begin, we will ask a question:

How many of the survey respondents described themselves as having a
political ideology of either conservative, liberal, or moderate?

Obviously we are not going to look at the data and get our answer by
counting by hand! What a waste of time! One thing we could do is tell
the computer to build a table for us! The structure of the code required
to make a table will read like this:

Look at this data called immigration AND THEN count the number of items
for each level in this categorical variable.

### 1.2 Tasks and Questions

1.  Based on the description above that details the structure of the
    code, erase the \_\_\_\_\_\_ sections in the code chunk below and
    replace them with either the name of the data set or the name of the
    variable needed to answer our question.

2.  Which political ideology had the most respondents?

Conservative

``` r
immigration %>%
  count(political)
```

    ## # A tibble: 3 × 2
    ##   political        n
    ##   <fct>        <int>
    ## 1 conservative   372
    ## 2 liberal        175
    ## 3 moderate       363

## 1.3 Table with Proportions and Counts

Knowing the total in each group is helpful. Knowing what proportion of
respondents fell into each level can also be helpful. To get that
information you have to add one line of code to what you wrote in part
1.2.

That line of code is what you see in the gray space below. The mutate
function in that line is creating a new variable called proportion that
takes the number of respondents in each level and divides each of those
by the total number of respondents.

### 1.3 Tasks and Questions

1.  Copy the code you wrote in part 1.2 into the line above the code you
    see below.

2.  Add the pipe symbol, %&gt;%, at the end of the line that has count.

3.  Run the code.

4.  What proportion of the respondents were moderate?

0.3989

``` r
immigration %>%
  count(political) %>%
  mutate(proportion = n / sum(n)) 
```

    ## # A tibble: 3 × 3
    ##   political        n proportion
    ##   <fct>        <int>      <dbl>
    ## 1 conservative   372      0.409
    ## 2 liberal        175      0.192
    ## 3 moderate       363      0.399

## 1.4 Arranging the table

We’ve talked a lot about clear and effective communication. One way to
do that when making a table is by ordering the table in a meaningful
way. The political ideology variable is not ordinal so we can order the
table from least to greatest or greatest to least. Again, one additional
line of code to what we’ve already created will do just that.

### 1.4 Tasks and Questions

1.  Copy the code from part 1.3 and paste it into the gray space below.

2.  Add a pipe symbol, %&gt;%, after the row that includes mutate.

3.  In the next line of code add: arrange(desc(proportion))

4.  Run the entire code chunk.

5.  What do you think desc, which is in the line of code your wrote,
    stands for?

desc tells the computer to put the proportion column in descending
order.

``` r
immigration %>%
  count(political) %>%
  mutate(proportion = n / sum(n)) %>%
  arrange(desc(proportion))
```

    ## # A tibble: 3 × 3
    ##   political        n proportion
    ##   <fct>        <int>      <dbl>
    ## 1 conservative   372      0.409
    ## 2 moderate       363      0.399
    ## 3 liberal        175      0.192

## 1.5: Build a Bar Graph

After building the table, you now have a better understanding of the
respondents to the survey. The table could be used as a visualization.
However, often times people can more easily and quickly see the major
takeaways from a bar graph. The table would then provide you with the
numbers to support what is displayed in the bar graph.

We will now build a bar graph that shows what is in the table you just
created. The structure of the code to do this will look very similar to
the code you wrote to make histograms and density curves in the previous
tutorial.

To answer this question… I need this data frame I specifically need this
variable and need to put it on the blank axis and I want to make this
visualization.

### 1.5 Tasks and Questions

1.  Change NAME\_OF\_DATA\_FRAME and CATEGORICAL\_VARIABLE so you create
    a bar graph that visualizes the same information you created in 1.2.

2.  Run the code.

3.  What are three design changes you’d like to make to this
    visualization to make it easier for someone to read?

-   Order the bars from largest to smallest
-   Add better labels. ie Title, subtitle, axes titles.
-   Add meaningful color

``` r
immigration %>%
  ggplot(aes(x = political)) +
  geom_bar()
```

![](KEY_3_EDA_Categorical_Data_files/figure-gfm/bar%20graph-1.png)<!-- -->

## 1.6: Adjust bar graph to implement some data visualizations best practices.

Making a bar graph without adjusting any design elements should be your
first step when exploring data. Keep it simple and keep your process
short as you start learning about the data. Only after that can you
begin to say things like, "Oh, given what it shows, I should change the
title to \_\_\_, the scales on the axes need adjusting, and flip it
horizontally."

This next section of this tutorial will guide you through adding or
adjusting layers of code to produce a more polished bar graph. These are
the steps you are taking as you prepare to put your visualizations into
a paper or presentation.

### 1.6a: Horizontal Bars and Labels

Let’s begin by making the bars lay horizontally and adding in a few of
the design layers you learned in the second tutorial.

#### 1.6a: Tasks and Questions

1.  The code chunk below will cause the bars to lay horizontally. It
    looks VERY similar to the code written in 1.5. What was changed in
    the code from 1.5 to make the bars lay horizontally?

x = was changed to y =

2.  Add in appropriate labels in between each "".

``` r
immigration %>%
  ggplot(aes(y = political)) +
  geom_bar() +
  labs(x = "Number of Respondents", 
       y = "", 
       title = "The Political Ideology of Registered Votes in Tampa Florida", 
       subtitle = "Based on a random sample of 910 registred voters in Tampa, Florida") 
```

![](KEY_3_EDA_Categorical_Data_files/figure-gfm/horizontal%20and%20labels-1.png)<!-- -->
\#\#\# 1.6b: Arranging the bars and changing colors

You will also want to help an observer of your visualization by ordering
the bars from greatest to least, filling the bars in with meaningful
colors, and removing some clutter.

The changes to what comes after y = in the code below change the order
of the bars from least to greatest.

Putting political after fill = is a necessary step given how you will
adjust the color of the bars.

#### 1.6b: Tasks and Questions

1.  Given the context of what we are visualizing, what colors would best
    fit each bar? Again, feel free to reference this site for the names
    of the colors you want.
    <http://www.stat.columbia.edu/~tzheng/files/Rcolor.pdf>

2.  Change CONSERVATIVE\_COLOR, LIBERAL\_COLOR, and MODERATE\_COLOR in
    the code below to the names of the colors you selected in
    question 1. Keep the quotes around each color name.

3.  Run the code and pat yourself on the back!

``` r
immigration %>%  
  ggplot(aes(y = fct_rev(fct_infreq(political)), fill = political)) +
  geom_bar() +
  labs(x = "Number of Respondents", 
       y = "", 
       title = "The Political Ideology of Registered Votes in Tampa, Florida", 
       subtitle = "Based on a random sample of 910 registred voters in Tampa, Florida") +
  scale_fill_manual(values = c("red","navy", "lightgray"), guide = FALSE) +
  theme_minimal()
```

    ## Warning: It is deprecated to specify `guide = FALSE` to remove a guide. Please
    ## use `guide = "none"` instead.

![](KEY_3_EDA_Categorical_Data_files/figure-gfm/complete%20bar-1.png)<!-- -->

# 2: Exploring Two Categorical Variables

The question you answered on one of your homework assignments was, “Do
political ideology and views on immigration appear to be associated?”

Answering that question requires you to explore two categorical
variables. This part of the tutorial will walk you through building
contingency tables and filled bar plots.

## 2.1: Contingency Table with Counts

Let’s start by recreating the table you saw on this homework problem. To
get a refresher, visit question 2 after going to this link -
<https://openintro-ims.netlify.app/explore-categorical.html>

### 2.1: Tasks and Questions

1.  Change NAME\_OF\_DATA\_FRAME and SECOND\_VARIABLE so you can create
    the two way table with the right information.

2.  Given the results in the table and bar graph you produced in part 1
    of this tutorial, why might we not want to compare the NUMBER of
    people within each political ideology that responded for each level
    of immigration?

The number of people that reported hav

``` r
immigration %>%
  count(political, response) %>%
  pivot_wider(names_from = political, values_from = n) %>%
  adorn_totals(where = c("row", "col"))
```

    ##               response conservative liberal moderate Total
    ##  Apply for citizenship           57     101      120   278
    ##           Guest worker          121      28      113   262
    ##      Leave the country          179      45      126   350
    ##               Not sure           15       1        4    20
    ##                  Total          372     175      363   910

## 2.2: Contingency Table with Proportions.

In the code below, you will create a contingency with column
proportions.

In other words, you want to have a table that can help answer questions
like, “What proportion OF THOSE who are conservative responded by saying
they support applying for citizenship?”

### 2.2: Tasks and Questions

1.  Change NAME\_OF\_DATA\_FRAME, FIRST\_VARIABLE, and SECOND\_VARIABLE
    in the code below to create the contingency table described above.

``` r
 immigration%>%
  count(political, response) %>% 
  group_by(political) %>%
  mutate(proportion = n / sum(n)) %>% 
  select(-n) %>%
  pivot_wider(names_from = political, values_from = proportion)
```

    ## # A tibble: 4 × 4
    ##   response              conservative liberal moderate
    ##   <fct>                        <dbl>   <dbl>    <dbl>
    ## 1 Apply for citizenship       0.153  0.577     0.331 
    ## 2 Guest worker                0.325  0.16      0.311 
    ## 3 Leave the country           0.481  0.257     0.347 
    ## 4 Not sure                    0.0403 0.00571   0.0110

## 2.3: Visualize Two Categorical Variables with a Filled Bar Plot

As we did in part one, we want to create a data visualization in
addition to a table. Because there was a big difference between the
number of people who responded from each political ideology, we will
make a filled bar plot.

### 2.3a: Create a Filled Bar Graph

#### 2.3a: Tasks and Questions

1.  Before we dive into the code, take out either a piece of paper or
    your iPad and draw a rough sketch of the filled bar plot that will
    support the table you created in part 2.2. We are going to make the
    bars lay horizontally. You do not have to draw it to exact scale.
    Instead be sure you can identify what variable will be on the
    y-axis, what variable you will fill the bars, and what labels will
    you want to include.

Call Mr. Adams over before going to the next step.

2.  Change NAME\_OF\_DATA\_FRAME, FIRST\_VARIABLE, and SECOND\_VARIABLE
    in the code below to create the filled bar graph you made in
    question 1.

3.  Add in a title, labels for each axis, and a label for the key.

4.  Run the code and pat yourself on the back!

``` r
immigration %>%
  ggplot(aes(y = political, fill = response)) +
  geom_bar(position = "fill", color = "white") +
  labs(
    title = "What should workers who have entered the country \nillegally be allowed to or have to do?",
    subtitle = "Based on a random sample of 910 registred voters in Tampa, Florida",
    x = "Proportion",
    y = "Political Ideology",
    fill = ""
  )
```

![](KEY_3_EDA_Categorical_Data_files/figure-gfm/standardized%20bar-1.png)<!-- -->

### 2.3b Adjust filled bar graph to include some data visualization best practices

Like before, we want the main takeaway to pop out to the viewer of this
visualization. In this case we will highlight the filled spaces
representing proportion supporting Apply for Citizenship and order the
bars from least to greatest proportion that support Apply for
Citizenship.

#### 2.3b Tasks and Questions

1.  In the row that starts with scale\_fill\_manual, change the APPLY’s
    color to any color you’d like. Change all the other colors to
    lightgray (NO SPACES in lightgray)

2.  Run the code and pat yourself on the back!

3.  Now that you’ve seen the visualization, add in a subtitle that will
    highlight the major takeaway from this visualization.

4.  Run the code again. Stand up. Put your hands in the air and yell,
    “LET’S GOOOOO!!!”

5.  After your brief celebration, write answer the question we started
    with in this part of the tutorial: “Do political ideology and views
    on immigration appear to be associated?”

Yes, it does appear that there is an association between political
ideology and views on immigration. One way in which this is evident is
that the proportion of liberal respondents who favored allowing workers
who entered the country illegally to apply for citizenship was roughly
58% while it was about 15% amongst conservatives.

``` r
immigration %>%
  ggplot(aes(y = fct_rev(fct_infreq(political)), fill = response)) +
  geom_bar(position = "fill", color = "white") +
  labs(
    title = "What should workers who have entered the country \nillegally be allowed to or have to do?",
    subtitle = "Based on a random sample of 910 registred voters in Tampa, Florida",
    x = "Proportion",
    y = "Political Ideology",
    fill = ""
  ) +
  scale_fill_manual(values = c("red", "lightgray", "lightgray","lightgray")) +
  theme_minimal()
```

![](KEY_3_EDA_Categorical_Data_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

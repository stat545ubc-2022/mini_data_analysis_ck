Mini Data-Analysis 1
================

# Welcome to your (maybe) first-ever data analysis project!

And hopefully the first of many. Let’s get started:

1.  Install the [`datateachr`](https://github.com/UBC-MDS/datateachr)
    package by typing the following into your **R terminal**:

<!-- -->

    install.packages("devtools")
    devtools::install_github("UBC-MDS/datateachr")

2.  Load the packages below.

``` r
suppressPackageStartupMessages(library(datateachr))
suppressPackageStartupMessages(library(tidyverse))
```

3.  Make a repository in the <https://github.com/stat545ubc-2022>
    Organization. You will be working with this repository for the
    entire data analysis project. You can either make it public, or make
    it private and add the TA’s and Lucy as collaborators. A link to
    help you create a private repository is available on the
    \#collaborative-project Slack channel.

# Instructions

## For Both Milestones

-   Each milestone is worth 45 points. The number of points allocated to
    each task will be annotated within each deliverable. Tasks that are
    more challenging will often be allocated more points.

-   10 points will be allocated to the reproducibility, cleanliness, and
    coherence of the overall analysis. While the two milestones will be
    submitted as independent deliverables, the analysis itself is a
    continuum - think of it as two chapters to a story. Each chapter, or
    in this case, portion of your analysis, should be easily followed
    through by someone unfamiliar with the content.
    [Here](https://swcarpentry.github.io/r-novice-inflammation/06-best-practices-R/)
    is a good resource for what constitutes “good code”. Learning good
    coding practices early in your career will save you hassle later on!

## For Milestone 1

**To complete this milestone**, edit [this very `.Rmd`
file](https://raw.githubusercontent.com/UBC-STAT/stat545.stat.ubc.ca/master/content/mini-project/mini-project-1.Rmd)
directly. Fill in the sections that are tagged with
`<!--- start your work below --->`.

**To submit this milestone**, make sure to knit this `.Rmd` file to an
`.md` file by changing the YAML output settings from
`output: html_document` to `output: github_document`. Commit and push
all of your work to the mini-analysis GitHub repository you made
earlier, and tag a release on GitHub. Then, submit a link to your tagged
release on canvas.

**Points**: This milestone is worth 45 points: 43 for your analysis, 1
point for having your Milestone 1 document knit error-free, and 1 point
for tagging your release on Github.

# Learning Objectives

By the end of this milestone, you should:

-   Become familiar with your dataset of choosing
-   Select 4 questions that you would like to answer with your data
-   Generate a reproducible and clear report using R Markdown
-   Become familiar with manipulating and summarizing your data in
    tibbles using `dplyr`, with a research question in mind.

# Task 1: Choose your favorite dataset (10 points)

The `datateachr` package by Hayley Boyce and Jordan Bourak currently
composed of 7 semi-tidy datasets for educational purposes. Here is a
brief description of each dataset:

-   *apt_buildings*: Acquired courtesy of The City of Toronto’s Open
    Data Portal. It currently has 3455 rows and 37 columns.

-   *building_permits*: Acquired courtesy of The City of Vancouver’s
    Open Data Portal. It currently has 20680 rows and 14 columns.

-   *cancer_sample*: Acquired courtesy of UCI Machine Learning
    Repository. It currently has 569 rows and 32 columns.

-   *flow_sample*: Acquired courtesy of The Government of Canada’s
    Historical Hydrometric Database. It currently has 218 rows and 7
    columns.

-   *parking_meters*: Acquired courtesy of The City of Vancouver’s Open
    Data Portal. It currently has 10032 rows and 22 columns.

-   *steam_games*: Acquired courtesy of Kaggle. It currently has 40833
    rows and 21 columns.

-   *vancouver_trees*: Acquired courtesy of The City of Vancouver’s Open
    Data Portal. It currently has 146611 rows and 20 columns.

**Things to keep in mind**

-   We hope that this project will serve as practice for carrying our
    your own *independent* data analysis. Remember to comment your code,
    be explicit about what you are doing, and write notes in this
    markdown document when you feel that context is required. As you
    advance in the project, prompts and hints to do this will be
    diminished - it’ll be up to you!

-   Before choosing a dataset, you should always keep in mind **your
    goal**, or in other ways, *what you wish to achieve with this data*.
    This mini data-analysis project focuses on *data wrangling*,
    *tidying*, and *visualization*. In short, it’s a way for you to get
    your feet wet with exploring data on your own.

And that is exactly the first thing that you will do!

1.1 Out of the 7 datasets available in the `datateachr` package, choose
**4** that appeal to you based on their description. Write your choices
below:

**Note**: We encourage you to use the ones in the `datateachr` package,
but if you have a dataset that you’d really like to use, you can include
it here. But, please check with a member of the teaching team to see
whether the dataset is of appropriate complexity. Also, include a
**brief** description of the dataset here to help the teaching team
understand your data.

<!-------------------------- Start your work below ---------------------------->

#### Initial Choices

1: cancer_sample  
2: vancouver_trees  
3: apt_buildings  
4: parking_meters

<!----------------------------------------------------------------------------->

1.2 One way to narrowing down your selection is to *explore* the
datasets. Use your knowledge of dplyr to find out at least *3*
attributes about each of these datasets (an attribute is something such
as number of rows, variables, class type…). The goal here is to have an
idea of *what the data looks like*.

*Hint:* This is one of those times when you should think about the
cleanliness of your analysis. I added a single code chunk for you below,
but do you want to use more than one? Would you like to write more
comments outside of the code chunk?

<!-------------------------- Start your work below ---------------------------->

#### Cancer Sample

``` r
glimpse(cancer_sample)
```

    ## Rows: 569
    ## Columns: 32
    ## $ ID                      <dbl> 842302, 842517, 84300903, 84348301, 84358402, …
    ## $ diagnosis               <chr> "M", "M", "M", "M", "M", "M", "M", "M", "M", "…
    ## $ radius_mean             <dbl> 17.990, 20.570, 19.690, 11.420, 20.290, 12.450…
    ## $ texture_mean            <dbl> 10.38, 17.77, 21.25, 20.38, 14.34, 15.70, 19.9…
    ## $ perimeter_mean          <dbl> 122.80, 132.90, 130.00, 77.58, 135.10, 82.57, …
    ## $ area_mean               <dbl> 1001.0, 1326.0, 1203.0, 386.1, 1297.0, 477.1, …
    ## $ smoothness_mean         <dbl> 0.11840, 0.08474, 0.10960, 0.14250, 0.10030, 0…
    ## $ compactness_mean        <dbl> 0.27760, 0.07864, 0.15990, 0.28390, 0.13280, 0…
    ## $ concavity_mean          <dbl> 0.30010, 0.08690, 0.19740, 0.24140, 0.19800, 0…
    ## $ concave_points_mean     <dbl> 0.14710, 0.07017, 0.12790, 0.10520, 0.10430, 0…
    ## $ symmetry_mean           <dbl> 0.2419, 0.1812, 0.2069, 0.2597, 0.1809, 0.2087…
    ## $ fractal_dimension_mean  <dbl> 0.07871, 0.05667, 0.05999, 0.09744, 0.05883, 0…
    ## $ radius_se               <dbl> 1.0950, 0.5435, 0.7456, 0.4956, 0.7572, 0.3345…
    ## $ texture_se              <dbl> 0.9053, 0.7339, 0.7869, 1.1560, 0.7813, 0.8902…
    ## $ perimeter_se            <dbl> 8.589, 3.398, 4.585, 3.445, 5.438, 2.217, 3.18…
    ## $ area_se                 <dbl> 153.40, 74.08, 94.03, 27.23, 94.44, 27.19, 53.…
    ## $ smoothness_se           <dbl> 0.006399, 0.005225, 0.006150, 0.009110, 0.0114…
    ## $ compactness_se          <dbl> 0.049040, 0.013080, 0.040060, 0.074580, 0.0246…
    ## $ concavity_se            <dbl> 0.05373, 0.01860, 0.03832, 0.05661, 0.05688, 0…
    ## $ concave_points_se       <dbl> 0.015870, 0.013400, 0.020580, 0.018670, 0.0188…
    ## $ symmetry_se             <dbl> 0.03003, 0.01389, 0.02250, 0.05963, 0.01756, 0…
    ## $ fractal_dimension_se    <dbl> 0.006193, 0.003532, 0.004571, 0.009208, 0.0051…
    ## $ radius_worst            <dbl> 25.38, 24.99, 23.57, 14.91, 22.54, 15.47, 22.8…
    ## $ texture_worst           <dbl> 17.33, 23.41, 25.53, 26.50, 16.67, 23.75, 27.6…
    ## $ perimeter_worst         <dbl> 184.60, 158.80, 152.50, 98.87, 152.20, 103.40,…
    ## $ area_worst              <dbl> 2019.0, 1956.0, 1709.0, 567.7, 1575.0, 741.6, …
    ## $ smoothness_worst        <dbl> 0.1622, 0.1238, 0.1444, 0.2098, 0.1374, 0.1791…
    ## $ compactness_worst       <dbl> 0.6656, 0.1866, 0.4245, 0.8663, 0.2050, 0.5249…
    ## $ concavity_worst         <dbl> 0.71190, 0.24160, 0.45040, 0.68690, 0.40000, 0…
    ## $ concave_points_worst    <dbl> 0.26540, 0.18600, 0.24300, 0.25750, 0.16250, 0…
    ## $ symmetry_worst          <dbl> 0.4601, 0.2750, 0.3613, 0.6638, 0.2364, 0.3985…
    ## $ fractal_dimension_worst <dbl> 0.11890, 0.08902, 0.08758, 0.17300, 0.07678, 0…

``` r
sum(is.na(cancer_sample)) #in addition to dataset attributes, this looks at the total number of na's
```

    ## [1] 0

Cancer sample contains:  
- 569 rows, 32 columns  
- 0 NA’s, mostly numeric data

#### Vancouver Tree’s Dataset

``` r
glimpse(vancouver_trees)
```

    ## Rows: 146,611
    ## Columns: 20
    ## $ tree_id            <dbl> 149556, 149563, 149579, 149590, 149604, 149616, 149…
    ## $ civic_number       <dbl> 494, 450, 4994, 858, 5032, 585, 4909, 4925, 4969, 7…
    ## $ std_street         <chr> "W 58TH AV", "W 58TH AV", "WINDSOR ST", "E 39TH AV"…
    ## $ genus_name         <chr> "ULMUS", "ZELKOVA", "STYRAX", "FRAXINUS", "ACER", "…
    ## $ species_name       <chr> "AMERICANA", "SERRATA", "JAPONICA", "AMERICANA", "C…
    ## $ cultivar_name      <chr> "BRANDON", NA, NA, "AUTUMN APPLAUSE", NA, "CHANTICL…
    ## $ common_name        <chr> "BRANDON ELM", "JAPANESE ZELKOVA", "JAPANESE SNOWBE…
    ## $ assigned           <chr> "N", "N", "N", "Y", "N", "N", "N", "N", "N", "N", "…
    ## $ root_barrier       <chr> "N", "N", "N", "N", "N", "N", "N", "N", "N", "N", "…
    ## $ plant_area         <chr> "N", "N", "4", "4", "4", "B", "6", "6", "3", "3", "…
    ## $ on_street_block    <dbl> 400, 400, 4900, 800, 5000, 500, 4900, 4900, 4900, 7…
    ## $ on_street          <chr> "W 58TH AV", "W 58TH AV", "WINDSOR ST", "E 39TH AV"…
    ## $ neighbourhood_name <chr> "MARPOLE", "MARPOLE", "KENSINGTON-CEDAR COTTAGE", "…
    ## $ street_side_name   <chr> "EVEN", "EVEN", "EVEN", "EVEN", "EVEN", "ODD", "ODD…
    ## $ height_range_id    <dbl> 2, 4, 3, 4, 2, 2, 3, 3, 2, 2, 2, 5, 3, 2, 2, 2, 2, …
    ## $ diameter           <dbl> 10.00, 10.00, 4.00, 18.00, 9.00, 5.00, 15.00, 14.00…
    ## $ curb               <chr> "N", "N", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "Y", "…
    ## $ date_planted       <date> 1999-01-13, 1996-05-31, 1993-11-22, 1996-04-29, 19…
    ## $ longitude          <dbl> -123.1161, -123.1147, -123.0846, -123.0870, -123.08…
    ## $ latitude           <dbl> 49.21776, 49.21776, 49.23938, 49.23469, 49.23894, 4…

``` r
sum(is.na(vancouver_trees))
```

    ## [1] 191135

This dataset contains:  
- 146,611 rows, 20 columns  
- 191135 NA’s, mostly character variables

#### Apartment Buildings Dataset

``` r
glimpse(apt_buildings)
```

    ## Rows: 3,455
    ## Columns: 37
    ## $ id                               <dbl> 10359, 10360, 10361, 10362, 10363, 10…
    ## $ air_conditioning                 <chr> "NONE", "NONE", "NONE", "NONE", "NONE…
    ## $ amenities                        <chr> "Outdoor rec facilities", "Outdoor po…
    ## $ balconies                        <chr> "YES", "YES", "YES", "YES", "NO", "NO…
    ## $ barrier_free_accessibilty_entr   <chr> "YES", "NO", "NO", "YES", "NO", "NO",…
    ## $ bike_parking                     <chr> "0 indoor parking spots and 10 outdoo…
    ## $ exterior_fire_escape             <chr> "NO", "NO", "NO", "YES", "NO", NA, "N…
    ## $ fire_alarm                       <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ garbage_chutes                   <chr> "YES", "YES", "NO", "NO", "NO", "NO",…
    ## $ heating_type                     <chr> "HOT WATER", "HOT WATER", "HOT WATER"…
    ## $ intercom                         <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ laundry_room                     <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ locker_or_storage_room           <chr> "NO", "YES", "YES", "YES", "NO", "YES…
    ## $ no_of_elevators                  <dbl> 3, 3, 0, 1, 0, 0, 0, 2, 4, 2, 0, 2, 2…
    ## $ parking_type                     <chr> "Underground Garage , Garage accessib…
    ## $ pets_allowed                     <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ prop_management_company_name     <chr> NA, "SCHICKEDANZ BROS. PROPERTIES", N…
    ## $ property_type                    <chr> "PRIVATE", "PRIVATE", "PRIVATE", "PRI…
    ## $ rsn                              <dbl> 4154812, 4154815, 4155295, 4155309, 4…
    ## $ separate_gas_meters              <chr> "NO", "NO", "NO", "NO", "NO", "NO", "…
    ## $ separate_hydro_meters            <chr> "YES", "YES", "YES", "YES", "YES", "Y…
    ## $ separate_water_meters            <chr> "NO", "NO", "NO", "NO", "NO", "NO", "…
    ## $ site_address                     <chr> "65  FOREST MANOR RD", "70  CLIPPER R…
    ## $ sprinkler_system                 <chr> "YES", "YES", "NO", "YES", "NO", "NO"…
    ## $ visitor_parking                  <chr> "PAID", "FREE", "UNAVAILABLE", "UNAVA…
    ## $ ward                             <chr> "17", "17", "03", "03", "02", "02", "…
    ## $ window_type                      <chr> "DOUBLE PANE", "DOUBLE PANE", "DOUBLE…
    ## $ year_built                       <dbl> 1967, 1970, 1927, 1959, 1943, 1952, 1…
    ## $ year_registered                  <dbl> 2017, 2017, 2017, 2017, 2017, NA, 201…
    ## $ no_of_storeys                    <dbl> 17, 14, 4, 5, 4, 4, 4, 7, 32, 4, 4, 7…
    ## $ emergency_power                  <chr> "NO", "YES", "NO", "NO", "NO", "NO", …
    ## $ `non-smoking_building`           <chr> "YES", "NO", "YES", "YES", "YES", "NO…
    ## $ no_of_units                      <dbl> 218, 206, 34, 42, 25, 34, 14, 105, 57…
    ## $ no_of_accessible_parking_spaces  <dbl> 8, 10, 20, 42, 12, 0, 5, 1, 1, 6, 12,…
    ## $ facilities_available             <chr> "Recycling bins", "Green Bin / Organi…
    ## $ cooling_room                     <chr> "NO", "NO", "NO", "NO", "NO", "NO", "…
    ## $ no_barrier_free_accessible_units <dbl> 2, 0, 0, 42, 0, NA, 14, 0, 0, 1, 25, …

``` r
sum(is.na(apt_buildings))
```

    ## [1] 6286

This dataset contains:  
- 3,455 rows, 37 columns  
- 6286 NA’s, a number of dichotomous variables

#### Parking Meters Dataset

``` r
glimpse(parking_meters)
```

    ## Rows: 10,032
    ## Columns: 22
    ## $ meter_head     <chr> "Twin", "Pay Station", "Twin", "Single", "Twin", "Twin"…
    ## $ r_mf_9a_6p     <chr> "$2.00", "$1.00", "$1.00", "$1.00", "$2.00", "$2.00", "…
    ## $ r_mf_6p_10     <chr> "$4.00", "$1.00", "$1.00", "$1.00", "$1.00", "$1.00", "…
    ## $ r_sa_9a_6p     <chr> "$2.00", "$1.00", "$1.00", "$1.00", "$2.00", "$2.00", "…
    ## $ r_sa_6p_10     <chr> "$4.00", "$1.00", "$1.00", "$1.00", "$1.00", "$1.00", "…
    ## $ r_su_9a_6p     <chr> "$2.00", "$1.00", "$1.00", "$1.00", "$2.00", "$2.00", "…
    ## $ r_su_6p_10     <chr> "$4.00", "$1.00", "$1.00", "$1.00", "$1.00", "$1.00", "…
    ## $ rate_misc      <chr> NA, "$ .50", NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
    ## $ time_in_effect <chr> "METER IN EFFECT: 9:00 AM TO 10:00 PM", "METER IN EFFEC…
    ## $ t_mf_9a_6p     <chr> "2 Hr", "10 Hrs", "2 Hr", "2 Hr", "2 Hr", "3 Hr", "2 Hr…
    ## $ t_mf_6p_10     <chr> "4 Hr", "10 Hrs", "4 Hr", "4 Hr", "4 Hr", "4 Hr", "4 Hr…
    ## $ t_sa_9a_6p     <chr> "2 Hr", "10 Hrs", "2 Hr", "2 Hr", "2 Hr", "3 Hr", "2 Hr…
    ## $ t_sa_6p_10     <chr> "4 Hr", "10 Hrs", "4 Hr", "4 Hr", "4 Hr", "4 Hr", "4 Hr…
    ## $ t_su_9a_6p     <chr> "2 Hr", "10 Hrs", "2 Hr", "2 Hr", "2 Hr", "3 Hr", "2 Hr…
    ## $ t_su_6p_10     <chr> "4 Hr", "10 Hrs", "4 Hr", "4 Hr", "4 Hr", "4 Hr", "4 Hr…
    ## $ time_misc      <chr> NA, "No Time Limit", NA, NA, NA, NA, NA, NA, NA, NA, NA…
    ## $ credit_card    <chr> "No", "Yes", "No", "No", "No", "No", "No", "No", "No", …
    ## $ pay_phone      <chr> "66890", "59916", "57042", "57159", "51104", "60868", "…
    ## $ longitude      <dbl> -123.1289, -123.0982, -123.1013, -123.1862, -123.1278, …
    ## $ latitude       <dbl> 49.28690, 49.27215, 49.25468, 49.26341, 49.26354, 49.27…
    ## $ geo_local_area <chr> "West End", "Strathcona", "Riley Park", "West Point Gre…
    ## $ meter_id       <chr> "670805", "471405", "C80145", "D03704", "301023", "5913…

``` r
sum(is.na(parking_meters))
```

    ## [1] 19096

This dataset contains:  
- 10,032 rows, 2 columns  
- 19096 NA’s, multiple variables with nonsense names

<!----------------------------------------------------------------------------->

1.3 Now that you’ve explored the 4 datasets that you were initially most
interested in, let’s narrow it down to 2. What lead you to choose these
2? Briefly explain your choices below, and feel free to include any code
in your explanation.

<!-------------------------- Start your work below ---------------------------->

**Final 2 choices:**  
- Cancer sample  
- Apartment Buildings  
*This was mostly predicated on the number of NA’s in each dataset but
the parking meter dataset had a number of unclear variable names as well
as observations that might have required separating out a lot of
strings.*

<!----------------------------------------------------------------------------->

1.4 Time for the final decision! Going back to the beginning, it’s
important to have an *end goal* in mind. For example, if I had chosen
the `titanic` dataset for my project, I might’ve wanted to explore the
relationship between survival and other variables. Try to think of 1
research question that you would want to answer with each dataset. Note
them down below, and make your final choice based on what seems more
interesting to you!

<!-------------------------- Start your work below ---------------------------->

1.  *Cancer Sample*

-   What’s the relationship of texture and symmetry to diagnosis?

2.  *Vancouver Trees*

-   Are there more of a particular tree genus in particular
    neighbourhoods?

3.  *Apartment Buildings*

-   Are buildings that have elevators more likely to allow pets?

4.  *Parking Meters*

-   Do meters that use credit cards appear in particular areas?
    <!----------------------------------------------------------------------------->

# Important note

Read Tasks 2 and 3 *fully* before starting to complete either of them.
Probably also a good point to grab a coffee to get ready for the fun
part!

This project is semi-guided, but meant to be *independent*. For this
reason, you will complete tasks 2 and 3 below (under the **START HERE**
mark) as if you were writing your own exploratory data analysis report,
and this guidance never existed! Feel free to add a brief introduction
section to your project, format the document with markdown syntax as you
deem appropriate, and structure the analysis as you deem appropriate.
Remember, marks will be awarded for completion of the 4 tasks, but 10
points of the whole project are allocated to a reproducible and clean
analysis. If you feel lost, you can find a sample data analysis
[here](https://www.kaggle.com/headsortails/tidy-titarnic) to have a
better idea. However, bear in mind that it is **just an example** and
you will not be required to have that level of complexity in your
project.

# Task 2: Exploring your dataset (15 points)

If we rewind and go back to the learning objectives, you’ll see that by
the end of this deliverable, you should have formulated *4* research
questions about your data that you may want to answer during your
project. However, it may be handy to do some more exploration on your
dataset of choice before creating these questions - by looking at the
data, you may get more ideas. **Before you start this task, read all
instructions carefully until you reach START HERE under Task 3**.

2.1 Complete *4 out of the following 8 exercises* to dive deeper into
your data. All datasets are different and therefore, not all of these
tasks may make sense for your data - which is why you should only answer
*4*. Use *dplyr* and *ggplot*.

1.  Plot the distribution of a numeric variable.
2.  Create a new variable based on other variables in your data (only if
    it makes sense)
3.  Investigate how many missing values there are per variable. Can you
    find a way to plot this?
4.  Explore the relationship between 2 variables in a plot.
5.  Filter observations in your data according to your own criteria.
    Think of what you’d like to explore - again, if this was the
    `titanic` dataset, I may want to narrow my search down to passengers
    born in a particular year…
6.  Use a boxplot to look at the frequency of different observations
    within a single variable. You can do this for more than one variable
    if you wish!
7.  Make a new tibble with a subset of your data, with variables and
    observations that you are interested in exploring.
8.  Use a density plot to explore any of your variables (that are
    suitable for this type of plot).

2.2 For each of the 4 exercises that you complete, provide a *brief
explanation* of why you chose that exercise in relation to your data (in
other words, why does it make sense to do that?), and sufficient
comments for a reader to understand your reasoning and code.

<!-------------------------- Start your work below ---------------------------->

### 2.1 - Data Exploration

#### 1.Distribution of the smoothness variable

This plot gives a sense of what this variable looks like as the dataset
has many, many rows. We can easily see if the distribution is unimodal
or multimodal and formulate questions around that.

``` r
smoothness_dist<- cancer_sample %>%
  ggplot(aes(x=smoothness_mean)) +
  geom_histogram(aes(y=..density..), bins = 30, colour = "black", fill = "white") +
  geom_density(alpha=.2, colour = "red") +
  scale_x_continuous(breaks = scales::breaks_width(0.0125)) +
  labs(y="Density", x="Smoothness")
smoothness_dist
```

![](mini_data_analysis_1_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

#### 2. Relationship between radius and smoothness

This quick scatterplot gives an indication of the relationship between
two of the variables to see if there’s a question to be asked about
either (or both) of them.

``` r
smooth_v_rad<- cancer_sample %>%
  ggplot(aes(x=smoothness_mean, y=radius_mean)) +
  geom_point() +
  geom_smooth(method = "lm") +
  labs(y="Radius", x="Smoothness")
smooth_v_rad
```

    ## `geom_smooth()` using formula 'y ~ x'

![](mini_data_analysis_1_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

#### 3. Select relevant attributes

This is a large, numeric dataset so selecting out a few of the
attributes helps narrow down the questions and focus the analysis.

``` r
cancer_compact<- cancer_sample %>%
  select(starts_with(c("ID", "diagnosis", "radius", "texture", "smoothness"))) %>%
  rename(radius=radius_mean, texture=texture_mean, smoothness=smoothness_mean)
head(cancer_compact)
```

    ## # A tibble: 6 × 11
    ##        ID diagn…¹ radius radiu…² radiu…³ texture textu…⁴ textu…⁵ smoot…⁶ smoot…⁷
    ##     <dbl> <chr>    <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>   <dbl>
    ## 1  8.42e5 M         18.0   1.10     25.4    10.4   0.905    17.3  0.118  0.00640
    ## 2  8.43e5 M         20.6   0.544    25.0    17.8   0.734    23.4  0.0847 0.00522
    ## 3  8.43e7 M         19.7   0.746    23.6    21.2   0.787    25.5  0.110  0.00615
    ## 4  8.43e7 M         11.4   0.496    14.9    20.4   1.16     26.5  0.142  0.00911
    ## 5  8.44e7 M         20.3   0.757    22.5    14.3   0.781    16.7  0.100  0.0115 
    ## 6  8.44e5 M         12.4   0.334    15.5    15.7   0.890    23.8  0.128  0.00751
    ## # … with 1 more variable: smoothness_worst <dbl>, and abbreviated variable
    ## #   names ¹​diagnosis, ²​radius_se, ³​radius_worst, ⁴​texture_se, ⁵​texture_worst,
    ## #   ⁶​smoothness, ⁷​smoothness_se

#### 4. Radius density plot

Like \#1, this just shows the distribution of another potential variable
with the mean and median included so we can see the influence of any
outliers.

``` r
texture_density<- cancer_compact %>%
  ggplot(aes(x=texture, y=..density..)) +
  geom_density() +
  geom_vline(aes(xintercept=mean(texture)),
            color="red", linetype="dashed", size=0.8, alpha=0.5) +
  geom_vline(aes(xintercept=median(texture)),
            color="blue", linetype="dashed", size=0.8, alpha=0.5) +
  labs(y="Texture", x="Radius", caption = "Red dashed line indicates variable mean, blue indiciates the median")
texture_density
```

![](mini_data_analysis_1_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

<!----------------------------------------------------------------------------->

# Task 3: Write your research questions (5 points)

So far, you have chosen a dataset and gotten familiar with it through
exploring the data. Now it’s time to figure out 4 research questions
that you would like to answer with your data! Write the 4 questions and
any additional comments at the end of this deliverable. These questions
are not necessarily set in stone - TAs will review them and give you
feedback; therefore, you may choose to pursue them as they are for the
rest of the project, or make modifications!

<!--- *****START HERE***** --->

### Cell attributes and diagnosis

These 3 questions will explore the relationship between physical
attributes and diagnosis.

**1. Is radius, texture, or smoothness a better predictor of a malignant
diagnosis?**

**2. What is the relationship between cancer cell size (smoothness and
radius) and diagnosis?**

**3. What is the relationship between cell texture and diagnosis?**

### Relationships between cell attributes

This question is a general question about how the attributes are
related.

**4. How are the 3 attributes related to each other?**

# Task 4: Process and summarize your data (13 points)

From Task 2, you should have an idea of the basic structure of your
dataset (e.g. number of rows and columns, class types, etc.). Here, we
will start investigating your data more in-depth using various data
manipulation functions.

### 1.1 (10 points)

Now, for each of your four research questions, choose one task from
options 1-4 (summarizing), and one other task from 4-8 (graphing). You
should have 2 tasks done for each research question (8 total). Make sure
it makes sense to do them! (e.g. don’t use a numerical variables for a
task that needs a categorical variable.). Comment on why each task helps
(or doesn’t!) answer the corresponding research question.

Ensure that the output of each operation is printed!

**Summarizing:**

1.  Compute the *range*, *mean*, and *two other summary statistics* of
    **one numerical variable** across the groups of **one categorical
    variable** from your data.
2.  Compute the number of observations for at least one of your
    categorical variables. Do not use the function `table()`!
3.  Create a categorical variable with 3 or more groups from an existing
    numerical variable. You can use this new variable in the other
    tasks! *An example: age in years into “child, teen, adult, senior”.*
4.  Based on two categorical variables, calculate two summary statistics
    of your choosing.

**Graphing:**

5.  Create a graph out of summarized variables that has at least two
    geom layers.
6.  Create a graph of your choosing, make one of the axes logarithmic,
    and format the axes labels so that they are “pretty” or easier to
    read.
7.  Make a graph where it makes sense to customize the alpha
    transparency.
8.  Create 3 histograms out of summarized variables, with each histogram
    having different sized bins. Pick the “best” one and explain why it
    is the best.

Make sure it’s clear what research question you are doing each operation
for!

<!------------------------- Start your work below ----------------------------->

#### 1. Is radius, texture, or smoothness a better predictor of a malignant diagnosis?

**Summarize option 3:** *3 numeric variables were transformed into a
categorical variable with 3 groups to make plotting easier.*

``` r
vars_long<- cancer_compact %>%
  pivot_longer(cols = c("radius", "texture", "smoothness"), 
               names_to = "attribute", values_to = "average") %>%
  select(c("ID", "diagnosis", "attribute", "average"))
vars_long
```

    ## # A tibble: 1,707 × 4
    ##          ID diagnosis attribute  average
    ##       <dbl> <chr>     <chr>        <dbl>
    ##  1   842302 M         radius     18.0   
    ##  2   842302 M         texture    10.4   
    ##  3   842302 M         smoothness  0.118 
    ##  4   842517 M         radius     20.6   
    ##  5   842517 M         texture    17.8   
    ##  6   842517 M         smoothness  0.0847
    ##  7 84300903 M         radius     19.7   
    ##  8 84300903 M         texture    21.2   
    ##  9 84300903 M         smoothness  0.110 
    ## 10 84348301 M         radius     11.4   
    ## # … with 1,697 more rows

**Graphing option 5:** *A simple bar plot with the each datapoint
overlaid for a quick visual on how each attribute contributes to
diagnosis.*

``` r
vars_plot<- vars_long %>%
  ggplot(aes(attribute, average, fill=diagnosis)) +
  geom_bar(fun="mean", stat="summary", position="dodge") +
  geom_point(position=position_jitterdodge(dodge.width=0.9), alpha=0.2)
vars_plot
```

![](mini_data_analysis_1_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

#### 2. What is the relationship between cancer cell size (smoothness and radius) and diagnosis?

**Summarize option 1:** *One of the ‘size’ attributes is summarized
across diagnosis for a quick visual numeric comparison, to provide a
dataframe for future stats, and to provide a dataframe for the following
plot.*

``` r
#head(cancer_compact)
rad_sum<- cancer_compact %>%
  group_by(diagnosis) %>%
  summarize(mean=mean(radius), median=median(radius), 
            sd=sd(radius), min=min(radius), max=max(radius))
rad_sum
```

    ## # A tibble: 2 × 6
    ##   diagnosis  mean median    sd   min   max
    ##   <chr>     <dbl>  <dbl> <dbl> <dbl> <dbl>
    ## 1 B          12.1   12.2  1.78  6.98  17.8
    ## 2 M          17.5   17.3  3.20 11.0   28.1

**Graphing option 5:** *A simple bar graph is used for easy visual
comparison of radius means per diagnosis.*

``` r
rad_diagnosis_plot<- rad_sum %>%
  ggplot(aes(diagnosis, mean)) +
  geom_bar(stat="identity", width=0.5) +
  geom_errorbar(aes(ymin=mean-sd, ymax=mean+sd), width=.2) +
  scale_y_continuous(expand = c(0, 0), limits = c(0, 25)) +
  labs(y = "Radius", x = "Diagnosis") + 
  scale_x_discrete(labels = c("Benign", "Malignant")) +
  theme(axis.title = element_text(size = 12, face = "bold")) +
  theme(axis.text = element_text(face = "bold")) +
  theme(panel.background = element_blank()) + 
  theme(panel.grid.major = element_blank(), 
        panel.grid.minor = element_blank()) +
  theme(axis.line = element_line(colour = "black", size = 0.5))
rad_diagnosis_plot
```

![](mini_data_analysis_1_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

#### 3. What is the relationship between cell texture and diagnosis?

**Summarize option 1:** *Again, the first option was the most useful
option here but the mean of the other attributes were kept in the
dataframe to keep texture within the context of the other variables.*

``` r
radsmooth<- vars_long %>%
  group_by(diagnosis, attribute) %>%
  summarise(mean=mean(average), sd=sd(average), median=median(average)) %>%
  arrange(attribute)
```

    ## `summarise()` has grouped output by 'diagnosis'. You can override using the
    ## `.groups` argument.

``` r
radsmooth
```

    ## # A tibble: 6 × 5
    ## # Groups:   diagnosis [2]
    ##   diagnosis attribute     mean     sd  median
    ##   <chr>     <chr>        <dbl>  <dbl>   <dbl>
    ## 1 B         radius     12.1    1.78   12.2   
    ## 2 M         radius     17.5    3.20   17.3   
    ## 3 B         smoothness  0.0925 0.0134  0.0908
    ## 4 M         smoothness  0.103  0.0126  0.102 
    ## 5 B         texture    17.9    4.00   17.4   
    ## 6 M         texture    21.6    3.78   21.5

**Graphing option 6:** *A boxplot with datapoints was used instead of a
bar graph to maintain a comparison between diagnoses but to also
visualize the distribution of datapoints. A logarithmic y scale was
used, mostly to diversify the graphing options used in the assignment.*

``` r
text_boxplot<- cancer_compact %>%
  ggplot(aes(diagnosis, texture)) +
  geom_boxplot(width=0.5, outlier.shape=NA) +
  geom_jitter(alpha=0.3, width=0.1) +
  scale_y_log10() +
  labs(y = "Texture", x = "Diagnosis") + 
  scale_x_discrete(labels = c("Benign", "Malignant")) +
  theme(axis.title = element_text(size = 12, face = "bold")) +
  theme(axis.text = element_text(face = "bold")) +
  theme(axis.line = element_line(colour = "black", size = 0.5))
text_boxplot
```

![](mini_data_analysis_1_files/figure-gfm/unnamed-chunk-15-1.png)<!-- -->

#### 4. How are the 3 attributes related to each other?

**Summarize option 5:** *All 3 attributes were collapsed across
diagnoses and summarized which provides a starting dataframe for stats
on the total value of each characteristic irrespective of diagnosis.*

``` r
smoothxtext<- vars_long %>% 
  group_by(attribute) %>%
  summarize(mean=mean(average), median=median(average), 
            sd=sd(average), min=min(average), max=max(average))
smoothxtext
```

    ## # A tibble: 3 × 6
    ##   attribute     mean  median     sd    min    max
    ##   <chr>        <dbl>   <dbl>  <dbl>  <dbl>  <dbl>
    ## 1 radius     14.1    13.4    3.52   6.98   28.1  
    ## 2 smoothness  0.0964  0.0959 0.0141 0.0526  0.163
    ## 3 texture    19.3    18.8    4.30   9.71   39.3

**Graphing option 7:** *A simple scatterplot with a line of best fit
shows the direction of the relationship between 2 of the 3 variables.
Alpha was adjusted based on the heavy clustering of datapoints in the
middle.*

``` r
smooth_text_plot<- cancer_compact %>%
  ggplot(aes(texture, smoothness)) +
  geom_point(alpha=0.4) +
  geom_smooth(method="lm")
smooth_text_plot
```

    ## `geom_smooth()` using formula 'y ~ x'

![](mini_data_analysis_1_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

<!----------------------------------------------------------------------------->

### 1.2 (3 points)

Based on the operations that you’ve completed, how much closer are you
to answering your research questions? Think about what aspects of your
research questions remain unclear. Can your research questions be
refined, now that you’ve investigated your data a bit more? Which
research questions are yielding interesting results?

<!-------------------------- Start your work below ---------------------------->

-   Question 1 requires a multivariate model to fully answer the
    question but the bar graph offers a quick comparison that suggests
    smoothness has no relation to diagnosis but both texture and radius
    can affect diagnosis.  
-   Question 2 and 3 explore the results of question 1 at a more
    granular level, both the summary and graph suggest a direction for
    radius/texture on diagnosis but confirmatory analyses are required
    next.  
-   Question 4 gives an indication of the relationship between 2 of the
    3 variables but this is perfunctory and how each affects the others
    still remains to be uncovered.  
-   Question 1, 2, and 3 are likely to be the most interesting but *how*
    the attributes are related to each other may also be of use if this
    analysis were trying to improve diagnostic tools in cancer research.

<!----------------------------------------------------------------------------->

### Attribution

Thanks to Icíar Fernández Boyano for mostly putting this together, and
Vincenzo Coia for launching.

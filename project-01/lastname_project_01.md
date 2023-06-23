---
title: "Mini-Project 01"
output: 
  html_document:
    keep_md: true
    toc: true
    toc_float: true
---

# Data Visualization Project 01


```r
library(ggplot2)
library(tidyverse)
```

```
## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
## ✔ dplyr     1.1.1     ✔ readr     2.1.4
## ✔ forcats   1.0.0     ✔ stringr   1.5.0
## ✔ lubridate 1.9.2     ✔ tibble    3.2.1
## ✔ purrr     1.0.1     ✔ tidyr     1.3.0
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors
```


```r
WC_data <- read_csv("https://raw.githubusercontent.com/reisanar/datasets/master/WorldCupMatches.csv")
```

```
## Rows: 4572 Columns: 20
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (12): Datetime, Stage, Stadium, City, Home Team Name, Away Team Name, Wi...
## dbl  (8): Year, Home Team Goals, Away Team Goals, Attendance, Half-time Home...
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```


```r
WC_data_goals_long <- WC_data %>% 
  filter(Year == 2014) %>% 
  summarize(
    Home_Team_Goals = sum(`Home Team Goals`),
    Away_Team_Goals = sum(`Away Team Goals`)
  )%>% 
  pivot_longer(cols = everything(), names_to = "category", values_to = "value")
```



# Motivation and changes

For Mini Project 1 the main goal is to work on the critique I received. First, I implement an README.md file that gives an executive summary for the reader. Moreover, the report will be adjusted. Implementing my most interesting plots will help to convey the message and make the data story more exciting. The third and final step is to improve my data visualizations. Using themes and change labels are tools to make my plots easier readable.

# What story could you tell with your plots?

"Soccer has the largest average home advantage across leagues." ("https://www.chicagobooth.edu/review/home-field-advantage-facts-and-fiction#:~:text=Soccer%20has%20the%20largest%20average,are%20won%20by%20home%20teams.") To investigate this quote, I looked at home and away goals. 

<img src="https://raw.githubusercontent.com/Tommnn/dataviz_final_project3/main/figures/attendance_brazil.png" width="60%" height="60%">

We can see, that home teams score more goals on average (see Figure below). Besides that, there is no real advantage of being a home team in a World Cup. All games are played on "neutral ground". The only team that had an home advantage was the Brazilian Team.

<img src="https://raw.githubusercontent.com/Tommnn/dataviz_final_project3/main/figures/attendance_brazil.png" width="60%" height="60%">

The attendees of a football game create a unique environment that can have a big impact on the game. On average a Bundesliga Stadium has 43,000 viewers every game. The highest number of attendees ever were counted in Glasgow. 1937 almost 150,000 people watched the Game Scotland against England. In our bar chart, the Estadio de Maracana is the one with most attendees. The capacity of the stadium is 76,935.

It can also be beneficial to play in the same stadium for more than one time. This is due to travel effort or existing routines. If we take a look at the map of all stadiums, the travel effort can be very high going from stadium to stadium. This can influence the regenaration and practice schedules of teams.

<img src="https://raw.githubusercontent.com/Tommnn/dataviz_final_project3/main/figures/map_brazil.png" width="60%" height="60%">



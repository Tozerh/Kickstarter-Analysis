# Kickstarting with Excel

## Overview of Project

  

### 
  The purpose of this project is to provide our customer, Louise, with an analysis of Kickstarter campaign data relevant to her areas of interest: campaign outcomes by launch date and campaign outcomes by funding goals. Because Louise's theater campaign for her own play, *Fever*, is very close to its funding goal, she has become interested in learning more about how her campaign is fairing compared to historical campaigns. 

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

  In order to isolate theater campaign outcomes by launch date, I initially filtered the data in my main sheet, 'Kickstarter', using "theater" on the column "Parent Category." Once I applied this filter, I copied and pasted this information into a new sheet "Theater Outcomes by Date" (more on this in the "Challenges and Difficulties..." section below). Once I was able to isolate the "theater" parent category, I inserted a PivotTable based on this data subset and adjusted the labels and filters as required for this project. Once I was satisfied that this pivot table was providing the right data, I created a line chart based on this table, which can be seen here: 
  
  ![Outcomes versus Launch Date](https://github.com/Tozerh/Kickstarter-Analysis/blob/main/Resources/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals
  The analysis for this particular deliverable for Louise required collecting a subset of data not with a column filter but with the Excel function "COUNTIFS," which required particular ranges and range criteria to be entered manually for each of the 12 ranges for the "Goal" column. Once I read up on the COUNTIFS function, I came up with the following formula to test output for the number of successful campaigns with a goal of less than 1,000 dollars: 
  
  `=COUNTIFS(Kickstarter!$D:$D,"<1000",Kickstarter!$F:$F,"successful",Kickstarter!$R:$R,"plays")`
  
  Checking this output against the raw dataset, I was confident that I understood the COUNTIFS function well enough to continue with the other ranges. Most of the Kickstarter goal ranges, however, required at least four arguments, and I ended up with the following formula template (after some testing, more on this below...) to adjust as needed: 

  `=COUNTIFS(Kickstarter!$D:$D,"<5000",Kickstarter!$D:$D,">=1000",Kickstarter!$F:$F,"failed",Kickstarter!$R:$R,"plays")` 

  Having confirmed the COUNTIFS formulae in my data table, I also prepared the "Total Projects," "Percentage Successful," "Percentage Failed," and "Percentage Canceled" columns. Once the formulae were all ready to go, I moved on to preparing the line graph to visualize these data, which required some adjustment to the "Series" (y-axis) and "Categories" (x-axis) data. 
  
  Initially, creating a line graph from the data table pulled in all of the data sources in the data table, including columns that I was not interested in displaying. I was able to adjust the data sources to isolate for only "successful," "failed," and "canceled" campaigns by right clicking on the plot area for this graph to adjust the data sources. Ultimately, I ended up with the following visual representation of the data for outcomes versus launch date: 

   ![Outcomes versus Goal](https://github.com/Tozerh/Kickstarter-Analysis/blob/main/Resources/Outcomes_versus_Goals.png) 

### Challenges and Difficulties Encountered

1) **Creating a sheet that was not necessary**:
  For the outcomes based on launch date analysis, I started by creating a new sheet that was a copy/paste of the subset of data present after filtering. This was not necessary, however, and I could have just created a pivot table from the master data sheet and then narrowed my scope using filters in the pivot table. The data output from this new sheet was ultimately the same for my graph, but I could have been a bit more efficient had I not created a new sheet. 

2) **Formula Consistency**: 
  Doing a quality check of my formulae for the outcomes based on goals, I found intially that the total number of projects in my data table was not matching the total projects in the raw data. I was able to identify the culprit: inconsistent ranges for my COUNTIFS criteria. 
  
  E.g.: 
  
  For the range of goals $1000 - $4999, I intially had this formula: 
  
  `=COUNTIFS(Kickstarter!$D:$D,"<5000",Kickstarter!$D:$D,">1000",Kickstarter!$F:$F,"failed",Kickstarter!$R:$R,"plays")`, 
  
  which was not capturing the correct range, not including goals that were both greater than _and equal to_ 1,000. In order to correct this, I needed to adjust my formula to include the ">=" operator, ending up with the formula: 
  
  `=COUNTIFS(Kickstarter!$D:$D,"<5000",Kickstarter!$D:$D,">=1000",Kickstarter!$F:$F,"failed",Kickstarter!$R:$R,"plays")`, 
   
  which achieved the desired result.

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

1) The mean for the percentage of successful campaigns in a given month is 60.56%, and May and June provide a 66.87% and 65.36% success rate, respectively. It will be important to have a campaign ready to launch by May 1st in order to take full advantage of this opportunity. 

2) If, for some reason,the campaign is only going to be ready to begin in December, then the launch should be delayed until at least January (if not February) in order to guarantee the best chance of success on the most convenient timetable. Postponing the launch of the campaign from December to January yields an 18% increase in success rate. 

- What can you conclude about the Outcomes based on Goals?
  Success rates are overall higher than failure rates in these two funding goal ranges:  $0 to $14,999 and $35,000 to $44,999. That higher funding goal range contains only a small number of campaigns (only 9 total projects), so I would not recommend any action in that range given this small sample size. The sweet spot for funding goal range is from $0 to $4,999, where we see an average success rate of %74.5. We would definitely want to counsel our client to keep their campaign in this lower range, if possible. 
  

- What are some limitations of this dataset?

1) This dataset does not provide data on when each individual donation to a particular campaign was made, only when a campaign was launched and when it ended. A dataset that includes information on the timing of each individual donation to each campaign would allow for more in-depth funding analysis. For example, knowing which months are most conducive to eliciting donations for a given subcategory would facilitate budgeting out a communications strategy for the life of a given campaign. 

2) This dataset is only current through 2017, making it more difficult to identify changes in trends in the last four years. Finding a similar dataset that is more current would allow us to make better recommendations for a campaign launching this year. 

3) This dataset is limited to one crowd-funding platform, Kickstarter. Finding parallel datasets from different crowd-funding platforms would allow for richer comparison and would give a better view of the crowd-funding landscape, allowing us to make stronger recommendations. 

- What are some other possible tables and/or graphs that we could create?

I think that a percentages table could be helpful in interpreting the graph that we created for the outcomes by launch date deliverable. Additionally, adding in a few descriptive statistics below this table might help us think about this piece of the project a little more clearly. Here is an example of this possible table, for reference: 

![Percentages Table and Descriptive Stats](https://github.com/Tozerh/Kickstarter-Analysis/blob/main/Percentages.PNG)

In conjunction with the graph that we produced for outcomes by launch date, this table shows that there is less variance than one might assume by looking at our graph, which has dramatic peaks and valleys. 

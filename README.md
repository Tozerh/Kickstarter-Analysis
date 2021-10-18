# Kickstarting with Excel

## Overview of Project

  

### 
The purpose of this project is to provide our customer, Louise, with an analysis of Kickstarter campaign data relevant to her areas of interest: campaign outcomes by launch date and campaign outcomes by funding goals. Because Louise's theater campaign for her own play, *Fever*, is very close to its funding goal, she is very interested in learning more about how her campaign is fairing compared to historical campaigns. 

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

  In order to isolate theater campaign outcomes by launch date, I initially filtered the data in my main sheet, 'Kickstarter', using "theater" on the column "Parent Category." Once I applied this filter, I copied and pasted this information into a new sheet "Theater Outcomes by Date" (more on this in the "Challenges and Difficulties..." section below). Once I was able to isolate the "theater" parent category, I inserted a PivotTable based on this data subset and adjusted the labels and filters as required for this project. Once I was satisfied that this pivot table was providing the right data, I created a line chart based on this table, which can be seen here: 
  
  ![Outcomes versus Launch Date](https://github.com/Tozerh/Kickstarter-Analysis/blob/main/Resources/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals
  The analysis for this particular deliverable for Louise required collecting a subset of data not with a column filter but with the Excel function "COUNTIFS," which required particular ranges and range criteria to be entered manually for each of the 12 ranges for the "Goal" column. Once I read up on the COUNTIFS function, I came up with the following formula to test output for the number of successful campaigns with a goal of less than 1,000 dollars: 
  
  `=COUNTIFS(Kickstarter!$D:$D,"<1000",Kickstarter!$F:$F,"successful",Kickstarter!$R:$R,"plays")`
  
  Checking this output against the raw dataset, I was confident that I understood the COUNTIFS function well enough to continue with the other ranges. Most of the Kickstarter goal ranges, however, required at least four arguments, and I ended up with the following formula template (after some testing, more on this below...) to adjust as needed: 

`=COUNTIFS(Kickstarter!$D:$D,"<5000",Kickstarter!$D:$D,">=1000",Kickstarter!$F:$F,"failed",Kickstarter!$R:$R,"plays")` 

  Having confirmed the formulae in this data table, I moved on to preparing the line graph to visualize this data, which required some adjustment to the "Series" (y-axis) and "Categories" (x-axis) data. Initially, creating a line graph pulled in all of the data sources in the data table, and I was able to adjust the data source with a quick right click on the plot area for this graph. Ultimately, I ended up with the following visual representation of the data for outcomes versus launch date: 

   ![Outcomes versus Goal](https://github.com/Tozerh/Kickstarter-Analysis/blob/main/Resources/Outcomes_versus_Goals.png) 

### Challenges and Difficulties Encountered

**Formatted file headers created an odd text sizing issue -- decided to resolve with a line break after the header hashes in line 7.** 

**Creating a sheet that was not necessary**

**Formula < and <= and >, etc. **
Sheet

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create?

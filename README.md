# Kickstarter-analysis
### Analyzing Kickstarter data to help Louise source funding for her theater production.

### Overview
For this project, my task was to help Louise determine which actions she should take to maximize the likelihood of having a successful crowdfunding campaign and bringing her play to the stage. From Kickstarter, I had access to a large number of campaigns that included information about the countries in which they were hosted, the funding goals and amounts pledged, different categories for each campaign, and numerous other attributes. My goal, then, was to use this data from Kickstarter to find common trends among the successfu theater campaigns to make recommendations for what she should do, as well as actions to avoid based on unsuccessful campaigns.

Analysis and Challenges: Explain how you performed your analysis using images and links to code, as well as any challenges you encountered and how you overcame them. If you had no challenges, describe any possible challenges or difficulties that could be encountered.

#### Preparation: outcomes based on launch date
Since many industries have busy seasons and slow seasons, I thought it would be worthwhile to investigate first whether there is a best time of year to launch a funding campaign. However, before I could dive into the data, I had to convert it to a format that would be understandable and easy to use. The original data for campaign launch dates and deadlines came in Unix timestamps, so I converted them to a normal month/day/year format by using Excel's "Date" data type. Unix timestamps indicate the number of seconds that have elapsed since January 1st, 1970, I simply divided the values given by 60 to yield minutes, then again divided by 60 to yield hours, then 24 to give days. To this, I added the value provided by Excel's DATE() function for January 1st, 1970. Finally, the "Date" data type applied to the relevant columns provided the dates in a standard month/day/year format, which is now easy to read. 

![Date Conversion Screenshot](https://github.com/veachk90/Kickstarter-analysis/blob/main/DateConversions.png)

#### Analysis: outcomes based on launch date
Once the dates had been converted, I could then look for trends in the data. With Excel, it was relatively easy to create a pivot table with outcomes based on launch date, filtered by Parent Category and Years, and with a count of each outcome as a dependent variable. From this table, I created a line graph that showed the count of each outcome throughout 2014, 2015, and 2016. This graph clearly showed that most successful theater campaigns began in May, with a sharp decline in the number of successful campaigns by September. Since the data showed such a spike in May, it is likely that Louise would benefit from launching her own production around that time.

![Theater Outcomes and Launch Dates](https://github.com/veachk90/Kickstarter-analysis/blob/main/Theater_Outcomes_vs_Launch.png)

The challenges with any pivot table is determining which factors are relavent and what filters to apply. From there, it is a matter of implementing a graph or chart that best communicates the intended meaning of the analysis. In this case, plays are theater productions, so we wanted to be sure to filter to only theater productions. Including data from other categories, such as games, would inhibit clarity, and could have resulted in Louise not launching her campaign at the historically optimum time. Then, we wanted to construct the pivot table to reflect how campaign outcomes respond to launch dates, so we set them to be the dependent variable, with launch dates as the independent variable. 

#### Preparation: outcomes based on goals
Next, it was important to consider the amount of funding Louise should source for her production. In order to do this effectively, I wanted to see how a campgain's goal affected its outcome. Again, I wanted to produce a visual aid that would quickly and easily communicate the results. A graph that included each individual data point would have been cluttered and unhelpful, so the first step was to create a table that organized the data into buckets. The buckets were set to $5,000 increments, from less than $1,000 to over $50,000. This allowed me to see a general trend for successful plays based on goals without being overly specific in my recommendations. To create the table, I wanted to count the number of plays that were successful, failed, or canceled in each goal bucket. From there, I could calculate the percentage of each outcome in each bucket. Thus, I implemented Excel's COUNTIFS() function to count the number of campaigns of each outocme in each bucket. Initially, I struggled to produce accurate counts because I attempted to reference filtered data. However, I learned that it is more effective to not bother with filtering the data, and instead to be more precise with the COUNTIFS() function by including better criteria. Apparently, COUNTIFS() considers raw data, and ignores filters on the data.

#### Analysis: outcomes based on goals
Once I had the count of each outcome in each bucket, it was a straightforward process to calculate the percentages of each outcome in each bucket. Percentages are commonly-understood metrics, and would serve as a great way to present my findings to Louise. From the table, I generated another line chart that showed how each outcome varied as the campaign goals increased. 

![Outcomes of Plays Based on Goals](https://github.com/veachk90/Kickstarter-analysis/blob/main/Outcomes_vs_Goals.png.png)

The graph made it clear that the bucket with the highest percentage of successful funding goals were lowest in the dollar amounts. Near 75% of successful campaigns had funding goals of less than $5,000. From there, the percentage of successful campaigns definitely declined as goal amounts increased. However, there was a second peak between $35,000 and $44,999, where 67% of campaigns with those funding goals were successful. As it turns out, there were no play campaigns that were canceled in any of the buckets, and we did not want to consider live campaigns in this analysis, so successful and failed campaign percentages were exact inverses of each other. 

**What are two conclusions you can draw about the Theater Outcomes by Launch Date?**
One conclusion for this analysis is that Louise can maximize her campaign's success by launching it in May. Generally, launching in the Summer is better than launching in the Winter. October had the highest number of failed campaigns, and while not containing the lowest number of successful campaigns, it still appeared to not be a good month for launching.

**What can you conclude about the Outcomes based on Goals?**
Louise should seek to minimize the cost of her campaign. The campaigns with funding goals of less than $5,000 were much more likely to be successful than those of higher amounts. However, if she truly wants to allow her amition to rule her campaign, she should strive to raise between $35,000 and $44,999, or about $40,000. 

**What are some limitations of this dataset?**
The data required a fair amount of processing and conversion in order to be useful. It would be helpful if the data were produced in such a way that it were easy to read at a glance, particularly any of the dates entries. Some data categories were clearly more relevant to Louise's case than others. 

**What are some other possible tables and/or graphs that we could create?**
Since this analysis considered launch dates as a predictor of outcomes, it also would have been fair to consider deadlines. It could have been interested to see how the campaign duration, as a difference between launch date and deadline, would have impacted a campaign's likelihood of success. 

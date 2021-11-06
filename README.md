# An Analysis of Kickstarter Campaigns - Analyzing the Success of Theatre Campaigns
## Overview of Project
After nearly funding her play *Fever* using Kickstarter, Louise's presented us with a problem: How well did her play fair against theater/play campaigns?
## Purpose
We are analyzing two items to provide additional context
  1. How did theater campaigns do dependent on the start date of the fundraising?
  2. How successful were plays based on their fundraising goal?
## Analysis and Challenges
A few items of note when reviewing the provided data:
- In order to find the Theater outcomes by Launch date, we needed to convert unix timestamps to a usable date. Kickstarter's data uses a time stamp measuring the number of secons since midnight of January 1, 1970:
  - Take the cells in Column J and use `<=(((J2/60/60)/24)+DATE(1970,1,1))>` to find the correct start date
  - Remove all sub-date categories out of the *Axis* Pivot Chart Field
  - Remove Live from the Row Labels filter
- To correctly capture all succesful and failed outcomes assigned to playes, make sure to have all factors of your excel function, or the results will be skewed
  - `countifs()` is the best option
  - If you do not use the correct greater than/less than/equals combination, you will not be capturing all items in a range. ex.) All items in a range of 1000 to 4999 Successful plays would code as follows: `=COUNTIFS('Kickstarter -Data'!$F:$F,"successful",'Kickstarter -Data'!$D:$D,">=1000",'Kickstarter -Data'!$D:$D,"<=4999",'Kickstarter -Data'!$R:$R,"plays")`

## Results
*Outcomes for Kickstarter Plays Based On Goals:*

![Image of Theater Outcomes by Date](https://github.com/jraguDataGuy/kickstarter-analysis/blob/main/Theater%20Outcomes%20Based%20on%20Launch%20Date.png)
- May had the highest volume of started campaigns, while also leading the way in successful fundraising.
- Most months had a 60% success rate in comparison to total monthly theater campaigns.
- October had the most failed theater campaigns, about 43.48% of the total theater campaigns that month.
- Given the above chart, Spring time gives folks the most success in fundraising. 

*Outcomes for Kickstarter Plays based on Fundraising Goals:*

![Image of Outcomes by Fundraising Goals](https://github.com/jraguDataGuy/kickstarter-analysis/blob/main/Outcomes%20for%20Plays%20based%20on%20Goals.png)
- Success of fundraising steadily decreased for goals of $1,000 to $30,000. 
- The most successful campaigns have smaller fundraising goals.
- $35,000 to $40,000 fundraising goals had 67% success rate. Beyond those figures, failure becomes very likely.

## Limitations
The visual component to our conclusions does give us confidence in the basic questions asked by Louise. However, there are many factors at play that would need to be considered in order to become confident on our general conclusions:
- For outcomes based on launch date, we would likely want to consider market forces that lead to the larger number of successful outcomes in the spring. Is there correlation to the likely April Tax Refund lots of consumers receive? Are there more plublicized submissions by Kickstart in the spring to help promote traffic on the site?
- For goals data, there is a reaonsable inference to be made that smaller goals are easier to hit. In addition, are the larger fundraising objectives part of projects that more robust in presentation and submission? This could explain the higher success rate seen in the $35,000 to $45,000 fundraising campaigns. 

* This project was practice work using a data set as part of the Data Analytics Bootcamp at Rice University

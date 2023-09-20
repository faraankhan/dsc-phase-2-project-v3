# Identifying Successful Movie Studios

## Project Overview
The purpose of this project was to assess historical movie box office data to recommend a course of strategy for a new entrant in the film industry. We wanted to understand which kinds of movie studios performed best at the box office, and what characteristics these studios embodied, and whether or not seasonality affected box office success. Through our analysis, we identified target studios on which to model creative decisions, including production budget size, inclusion of key genres, recommended runtime, and optimal release date strategy.  

## Business Understanding
We have been hired by a private equity firm to analyze box office data to recommend a course of strategy for the firm to enter the film industry. Guiding questions to inform our analysis included:
1. Which studios perform best at the box office?
2. What characteristics do these studios embody (production size, genre types, ideal runtime)?
3. Is a film's success impacted by release date (ie, what is the optimal release window for a film?)?

Before we opened the data, research showed that movie studios collect between 40% - 60% of box office revenue, and the rest is earned by the distributor (movie theater). This means that successful films would need to generate at least 50% profit to expect to break even on its production budget. Additionally, film studios incur significant print, advertising, and marketing costs that are not included in the production budget that can total up to 50% of the production budget (for large, international blockbusters based on recognizable IP). To account for this variable cost, we set a profit threshold of 75% to act as a cushion, and new that we would be targeting films and studios that generated at least 75% profit to indicate a successful release. 

## Data Understanding and Analysis
We used data from IMDB, Box Office Mojo, TheMovie Database (TMDB) and The Numbers to perform analyses. 

We began by merging movie gross data with movie budget data to create a dataframe called financial movie data that contained 1285 rows and 10 columns. Columns of interest included:
- Release date
- Title
- Production Budget
- Worldwide Gross
- Studio

We then merged this dataframe with the tmdb dataframe and added the columns **Profit Margin** and **Percent Profit**. We then filtered the newly merged dataframe to only include entries with Percent Profit greater than 50%. This filtered dataframe contained 710 rows and 18 columns.

We began by observing the distribution of movie releases per month and noticed a generally upward trend:
`[Screenshot](https://imagizer.imageshack.com/v2/640x480q70/922/xJTsfE.png)`

However, when we plotted percent profitability per month, the trend did not seem to follow that of movies by month. It appeared that the months with the most profitability were June, July, and October:
`[Screenshot](https://imagizer.imageshack.com/v2/640x480q70/924/MjJMNS.png)`

We next observed the correlations between production budget and worldwide gross, and production budget and percent profit. While it appeared there was a strong positive correlation between production budget and worldwide gross, there was no strong visually identifiable relationship between production budget and percent profit:

`[Screenshot](https://imagizer.imageshack.com/v2/640x480q70/923/r1fyrI.png)`

`[Screenshot](https://imagizer.imageshack.com/v2/640x480q70/923/JU97ma.png)`

However, we noticed a concentration of films that were more than 75% profitable with production budgets of less than $100 MM. This guided us to check if there was some sort of inverse relationship between production budget and percent profit, at least below the $100MM budget line. 

We developed a scatter plot of film studios that released films that were more than 50% profitable and distinguied between those that were, on average, less than 75% profitable (red), and those that were more than 75% profitable (green):

`[Screenshot](https://imagizer.imageshack.com/v2/640x480q70/923/x5I17i.png)`

Our intuition proved correct: Of the studios that were, on average, more than 75% profitable, none had average production budgets greater than $60MM. We selected a subset of 7 studios to analyze further that included:
- TWC
- A24
- IFC
- BH Tilt
- Fox S
- RTWC
- WB (NL)

We then broke down these studios by their top 5 most included genres and boxplots of their run times to determine what attributes they possessed that might contribute to their success. Based on these plots, the most frequently featured genres were Drama, Comedy, Horror, Crime, and Romance. The range of their median runtimes was between 91 and 105 minutes: 

`[Screenshot](https://imagizer.imageshack.com/v2/640x480q70/922/Nln10s.png)`

`[Screenshot](https://imagizer.imageshack.com/v2/640x480q70/924/23saEv.png)`

## Recommendation and Next Steps
Based on our analysis, we recommend a low-risk, high-reward approach for our client to model its creative studio on A24, IFC, and BH Tilt. All of these studios exhibited 78% and higher profitability, while producing films for roughly $10MM or less. Since marketing and advertising expenses appear to be a function of production budget, following these studios will allow for low marketing costs, while maintaining a high percent profit for our clients. 

These studios produce films that contain Drama, Comedy, and Horror genres primarily, and their median runtimes ranged from 92 to 98 minutes. We recommend that our client focus on releasing movies in mid summer (June/July) or mid fall (October), with the intution that Drama and Comedy may perform better in the summer and horror better in the fall. To ensure optimal box office returns, we recommend that our client partner with smaller, independent theaters to negotiate better box office deals, and to hire smaller marketing companies that leverage social media and virality to promote their films. 

Moving forward, we would want to incorporate a more robust dataset of film marketing expenses, streaming and television licensing contracts, and retail and merchandise revenue to fully understand total ROI.  

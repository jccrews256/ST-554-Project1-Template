Each group member should provide feedback on the other group members’ work. Be detailed and specific where possible. The quality of this feedback can play a part in your grade.

You can provide feedback to your group members in many different ways (live in a meeting, offline, or however else you devise) but the feedback must be documented here! 

Please replace “Feedback giver #x” with a group member’s name below and add feedback as a bulleted list below. Note: There is a pencil icon on the top right of the README file (when you are viewing the README.md file) that allows you to edit.

- Cass Crews (feedback added 02/20/26)
  + Overall:
    - Your notebook flows well, and the descriptions of the summaries you have created are very good. With a few updates to your plots, you’ll have a strong EDA. 
    - I find it more natural to transition from numeric summaries to graphical summaries. This may be my personal preference, but I also find your numeric summaries to be a great analytical base to build your graphical summary sections on! 
    - Given the size used for your section headings, I find them difficult to spot when scrolling. You might consider second- or third-level headings instead of fourth-level.  
    - Side note: I really appreciated the way you inserted valuable nuggets of information throughout the text. My favorites were the note that benzene is emitted by cars and the note that air’s maximum water vapor capacity declines with temperature. 
  + Introduction:
    - Overall, great introduction. My recommendations for this section are minimal.
    - I recommend further indenting the bullet containing the link to the “On Field Calibration…” paper; the second bullet feels like a child of the first bullet.
    - When you list out the EDA elements you cover in the notebook, ensure this list indicates the sections you have created: Temporal Plots, Non-Temporal plots, Non-Temporal Numeric Summaries, and Temporal Numeric Summaries. You can explicitly map these sections to the task instructions, but I think it’s important to specify the notebook sections in the introduction. 
    - This may be a personal preference: Because you change the variable names in the Clean the Dataset section, I don’t think you need to list the original variable names in the introduction. You can discuss the variables more generally in the introduction and formally define them in the data reading and cleaning sections. 
  + Read in the Data section:
    - You do not need to apply `pd.DataFrame()` to `air_quality.data.features` because `air_quality.data.features` is already a `pandas` data frame.
  + Clean the Dataset secton:
    - When renaming the variables, you might consider indicating the benzene variable is a true concentration and/or indicating the other chemical readings are only sensor readings. As it stands, a reader might forget about the nuanced differences between the benzene variable and the other chemical variables. 
    - Nice use of `.any()` in `df_missing = df_air_quality.loc[df_air_quality.isin([-200]).any(axis=1)]`. Definitely learned a trick when reading that line! 
  + Temporal Plots section:
    - I don’t think the plot “Scatter Plot of Benzene and Weather Measurements” adds any value given that you decide the plot contains too much information and then plot subsets of the same information in separate plots. 
    - I liked the decision to transition from a raw scale for your temporal scatter plots to a generalized scale  where each value is relative to the variable’s minimum and maximum. 
    - I would argue that you don’t see seasonality in the benzene concentrations because you are plotting hourly values. Note that in the “Scatter Plot of Benzene vs. Time” plot, values recorded from the middle of the night to dawn are almost all below the median concentration. 
    - Between code blocks [22] and [23], you accidentally spell “correlation” as “correlationt”. 
    - You sometimes wait until after a code block to explain what that code block does; an example is block [23]. This may lead the reader to dwell on the code block and outputs before realizing you explain it in the text block below the output. 
    - The separate plots for each variable across hours of the day (e.g., Scatter Plot of Benzene vs. Time) make comparisons challenging. It may be better to plot hourly means for multiple variables on the same plot using either your generalized “Relative Measurement” scale or a dual-axis plot. 
    - Similar to a previous comment I made, I recommend excluding any plot you find too dense and then replot in subsets. Thus, I would remove “Scatter Plot of Benzene and Multi-Sensor Measurement”. 
    - I view the following as my most important feedback: **Due to the fact that night-time benzene concentrations are generally low, I think you will gain additional insights by looking at daily and weekly average concentrations rather than, or at least in addition to, the daily minimums and maximums. You could also plot other statistics, similar to what we did when studying the NFL game data for Homework 4. In general, when a variable’s daily minimum is almost always near its global minimum, any temporal scatterplots will be difficult to process.**
    - Between code blocks 31 and 32, you refer to the carbon monoxide sensor readings as "CO concentrations." This may confuse the reader because the original dataset has a true concentration variable for carbon monoxide. 
    - Before creating `plot_relative_dailyminmax()`, I recommend describing it and its inputs within a text block. This will help the reader understand what the function is inputting and outputting. 
  + Non-Temporal Plots section:
    - I recommend removing the Time_num variable from your pairs plot as you already created the same plots when you created the temporal scatterplots across hours of the day. 
    - The relationship between benzene concentrations and NMHC sensor readings is incredibly strong! Good find! 
  + Non-Temporal Numeric Summaries section:
    - I recommend removing the covariance matrix. The lack of a constant scale for covariance across variable pairs makes this heatmap potentially misleading. 
    - When formally generating numeric summaries using `.describe()`, as opposed to using the method for basic data validation, I advise against including the date and time variables. We don’t glean any new information by reporting those variables’ statistics beyond confirmation they are correctly defined. 
    - You include the following sentence when discussing the unconditional standard deviations: *Too big or too small of swings are each disadvantageous.* I would argue large swings are only an issue when they correspond to noise in predicting. When big swings in a predictor correspond to big swings in the response, that’s a good thing. 
  + Temporal Numeric Summaries section:
    - While I like the MinMax scaling for some of the plots, I find it a bit confusing when looking at measures of center. An example is your heatmap of mean values by month (“Heatmap of Monthly Measurement Average Values”). It is difficult to interpret the variations of skewed variables such as `benzene`. If you want to rescale for a plot/table such as this, I recommend normalizing. 
    - In this section, you make the below claim. I don’t think you can write off the weather variables as bad predictors when looking at correlations without conditioning on other predictors. It may be the case that one of these variables adds value in predicting benzene concentration once other variables are controlled for. 
        + "The weather variable standard deviations also show that the previously observed potential weekday dependency is likely not statistically significant; the standard deviation is many times greater than the difference in average values. That means the weather variables are poor candiates for benzene level prediction because they don't follow the same trends (potentially unless a sophisticated model had different calibration parameters based on the day of the week)."
    - The heat map of variable means by hour is one of my favorite tables/plots I've seen in a long time! 
    - Similar to my above comment, the following statement about the weather variables may not be true once other variables are controlled for: 
        + "None of the weather variables have hourly standard deviation trends matching those of benzene, which makes weather variables poor candiates for benzene level prediction."
  + Key Findings: 
    - While your Key Findings section is very informative, it may contain too much detail. I found the “Overall Conclusions” to offer the exact depth I sought in a conclusion for this notebook. I recommend converting this subsection to a narrative style and using it alone for your Key Findings section. 



- Joy Zhou
- Added 2/20/2026
  + Overall:
    - You provided a detailed narrative with smooth transitions between sections.
    - The EDA is thorough, and you included helpful information about the data to facilitate further analysis.
    - Your analysis is solid and clearly communicated, just a few refinements would make it even more strong.
  + Task overview
    - This section is clear and well-written. 
    - You explained the purpose of the EDA concisely, and I particularly like how you framed the problem.
  + Read in Dataset
    - The conversion of air_quality.data.features into a DataFrame is not necessary.
  + Clean the dataset
    - You spent a considerable amount of time addressing missing values. This approach is fine, but I’m not sure all of that detail was needed for the data‑cleaning step.
  + Temporal Plots
    - You could consider removing the first plot (In [19], using col_list = benzene, T, RH, AH) since it doesn’t add meaningful insight. 
    - For In [20], you may want to either suppress the warnings or move them so that they don’t interrupt the narrative flow.
    - Your plot_relative_dailyminmax function is well defined and efficiently to check the trends across variables. The plots make the trends very easy to see. Nice work on that!
  + Non-Temporal Plots
    - You may want to revise the phrase 'the numeric summaries in this section may be displayed using a heatmap,' since you are already using a heatmap to summarize your numeric variables.
    - There is a lot of information presented in these plots, but your interpretation is strong and helps the reader understand the key patterns.
  + Non-Temporal Numeric Summaries
    - The heatmap for the correlation matrix is effective, and your explanation is clear and accurate.
    -	This section is well done.
  + Temporal Numeric Summaries
    - The overall structure is strong, and the patterns in the variables are clearly visible.
  + Key Findings
    - In your conclusion, you mentioned that benzene did not follow the same seasonal (or day to day) trend as any weather variable. However, in my section, when looking at the mean benzene levels, I did observe a seasonal trend. This difference may be we used different aggregation methods or different values to generate our plots. 
    - In the Non Temporal Plots section, you missed a colon after “Benzene vs. Other Pollutants”.








Each group member should provide feedback on the other group members’ work. Be detailed and specific where possible. The quality of this feedback can play a part in your grade.

You can provide feedback to your group members in many different ways (live in a meeting, offline, or however else you devise) but the feedback must be documented here! 

Please replace “Feedback giver #x” with a group member’s name below and add feedback as a bulleted list below. Note: There is a pencil icon on the top right of the README file (when you are viewing the README.md file) that allows you to edit.

- Cass Crews (feedback added 02/20/26)
  + Overall:
    - Your notebook flows well, and the descriptions of the summaries you have created are very good. With a few updates to your plots, you’ll have a strong EDA. 
    - I find it more natural to transition from numeric summaries to graphical summaries. This may be my personal preference, but I also find your numeric summaries to be a great analytical base to build your graphical summary sections on!
      - Response: Thanks for the suggestion! I used to do numerical and then graphical, but I changed my approach in the last year because of the simplicity of plotting dataframes and the rich insights you can very quickly obtain to guide numerical summaries afterwards. Particularly for this task, I needed to understand what periodic relationships may exist before stabbing in the dark at different groupings of numeric variables into pseudo-categorical variables. I'll definitely keep considering that in the future, but aside from using the `.decribe()` function early on, I've found much more benefit in starting with exploratory plots. 
    - Given the size used for your section headings, I find them difficult to spot when scrolling. You might consider second- or third-level headings instead of fourth-level.
      - Response: Agreed. Bumped all of the headers up two levels. 
    - Side note: I really appreciated the way you inserted valuable nuggets of information throughout the text. My favorites were the note that benzene is emitted by cars and the note that air’s maximum water vapor capacity declines with temperature. 
  + Introduction:
    - Overall, great introduction. My recommendations for this section are minimal.
    - I recommend further indenting the bullet containing the link to the “On Field Calibration…” paper; the second bullet feels like a child of the first bullet.
      - Incorporated
    - When you list out the EDA elements you cover in the notebook, ensure this list indicates the sections you have created: Temporal Plots, Non-Temporal plots, Non-Temporal Numeric Summaries, and Temporal Numeric Summaries. You can explicitly map these sections to the task instructions, but I think it’s important to specify the notebook sections in the introduction.
      - Response: To address your comment, I tried listing the sections that each list element corresponds to. The list elements (as directed in the task instructions) don't map one-for-one to the notebook sections, so it was getting messy and repetitive to try to map out a precise "crosswalk" in the introduction. Instead, I added a separate portion of the introduction to list the main sections of the notebook.
    - This may be a personal preference: Because you change the variable names in the Clean the Dataset section, I don’t think you need to list the original variable names in the introduction. You can discuss the variables more generally in the introduction and formally define them in the data reading and cleaning sections.
      - Response: Good point. I wrote that section before choosing my variable nicknames. I think it's helpful to mention the main variables of interest in the overview, so I also added the alias when introducing them with the full name. 
  + Read in the Data section:
    - You do not need to apply `pd.DataFrame()` to `air_quality.data.features` because `air_quality.data.features` is already a `pandas` data frame.
      - Incorporated.
  + Clean the Dataset secton:
    - When renaming the variables, you might consider indicating the benzene variable is a true concentration and/or indicating the other chemical readings are only sensor readings. As it stands, a reader might forget about the nuanced differences between the benzene variable and the other chemical variables.
      - Response: I'm not sure this is important. There is only one benzene variable in the dataset and adding descriptors to the end of the variable name adds clutter for the rest of the notebook. Regardless of whether there is a "ground truth" measurement of benzene or not, we are predicting the levels of one chemical based on measurements of other chemical levels and environmental variables. If the benzene measurement was with a metal oxide chemical sensor instead of a sophisticated laboratory-grade unit, the EDA steps would not change.   
    - Nice use of `.any()` in `df_missing = df_air_quality.loc[df_air_quality.isin([-200]).any(axis=1)]`. Definitely learned a trick when reading that line! 
  + Temporal Plots section:
    - I don’t think the plot “Scatter Plot of Benzene and Weather Measurements” adds any value given that you decide the plot contains too much information and then plot subsets of the same information in separate plots.
      - Response: I think that if I didn't show a plot of it, there could be unresolved questions about whether multi-variable plots would yield better insights than pairwise plots. To me, part of EDA is highlighting the complexity of the data and showing when you tried something that you thought would be useful even when it didn't work out. 
    - I liked the decision to transition from a raw scale for your temporal scatter plots to a generalized scale  where each value is relative to the variable’s minimum and maximum. 
    - I would argue that you don’t see seasonality in the benzene concentrations because you are plotting hourly values. Note that in the “Scatter Plot of Benzene vs. Time” plot, values recorded from the middle of the night to dawn are almost all below the median concentration.
      - Response: The benzene concentrations are also plotted on other plots showing the full 13-month measurement period. Those plots showed clear seasonality with weather variables but not with benzene levels. That bullet point in the summary at the end of the document was not intended to be correlated with the plots grouped by hour.
    - Between code blocks [22] and [23], you accidentally spell “correlation” as “correlationt”.
      - Corrected. 
    - You sometimes wait until after a code block to explain what that code block does; an example is block [23]. This may lead the reader to dwell on the code block and outputs before realizing you explain it in the text block below the output.
      - Incorporated. I discussed my intentions a couple cells prior, but you're right that the reader can lose track after reading code and outputs in between. 
    - The separate plots for each variable across hours of the day (e.g., Scatter Plot of Benzene vs. Time) make comparisons challenging. It may be better to plot hourly means for multiple variables on the same plot using either your generalized “Relative Measurement” scale or a dual-axis plot.
      - Response: You are correct that comparison is challenging. Because the `Time` is discrete (vs. continuous), these scatter plots appear almost as if they are histograms, which makes it difficult to show multiple variables at a time. Plotting the hourly trend of a statistic (e.g., median) of each of these variables would be a valid way to make comparisons on the same plot. However, the existing plotting technique shows are more data-rich (showing trends in min and max hourly values, accounting for outliers and the bulk trends all at once). Because there are only four plots and each has a very different shape, I did not consider it worth the time to create yet another plot to highlight those four vastly different hourly distributions all together. I'll add a description of that at the end of the hourly plots to better explain my thinking while conducting the EDA.  Thanks for highlighting this!
    - Similar to a previous comment I made, I recommend excluding any plot you find too dense and then replot in subsets. Thus, I would remove “Scatter Plot of Benzene and Multi-Sensor Measurement”.
      - Response: Incorporated, and agree because I demonstrated the data complexity earlier. (However, I still think it's a good idea to show the first one so the reader understands that the data is too complex to visualize more than two time-series variables at once). 
    - I view the following as my most important feedback: **Due to the fact that night-time benzene concentrations are generally low, I think you will gain additional insights by looking at daily and weekly average concentrations rather than, or at least in addition to, the daily minimums and maximums. You could also plot other statistics, similar to what we did when studying the NFL game data for Homework 4. In general, when a variable’s daily minimum is almost always near its global minimum, any temporal scatterplots will be difficult to process.**
      - Response: Incorporated. I considered what you recommended when I first developed these plots. Because the sensor data typically only includes interesting trends in the max _or_ the min value (and the other is relatively constant), I believed that showing the median or mean daily value would only clutter the plot by showing the same trend but with a suppressed magnitude. Based on your feedback, I went back and plotted the daily mean value trends (separate from the daily min/max plot to prevent over-crowding). The same trend did occur with the mean values as with the more prominent of the daily min or max values, as expected. But because a third-party reader might not intuitively know that the same trend is baked into the daily min/max plots, it was worth adding explicitly. 
    - Between code blocks 31 and 32, you refer to the carbon monoxide sensor readings as "CO concentrations." This may confuse the reader because the original dataset has a true concentration variable for carbon monoxide.
      - Incorporated.
    - Before creating `plot_relative_dailyminmax()`, I recommend describing it and its inputs within a text block. This will help the reader understand what the function is inputting and outputting.
      - Response: Isn't this what the function `doc string` is for? I'll add a sentence to the markdown cell above the function definition, but it would be redundant to include all of the same information included in the `doc string`. 
  + Non-Temporal Plots section:
    - I recommend removing the Time_num variable from your pairs plot as you already created the same plots when you created the temporal scatterplots across hours of the day.
      - Incorporated. With so many variables, space is certainly at a premium!
    - The relationship between benzene concentrations and NMHC sensor readings is incredibly strong! Good find! 
  + Non-Temporal Numeric Summaries section:
    - I recommend removing the covariance matrix. The lack of a constant scale for covariance across variable pairs makes this heatmap potentially misleading.
      - Response: I understand the concern but disagree. While we need to be cautious with the interpretation, covariance is often analyzed alongside covariance for a reason. Covariance can show interesting properties that are not clearly highlighted by sample correlation. For example, two variables can have a high correlation if there is a clear, linear, positive relationship between them. However, that doesn't make them the best match for predicting one as a function of the other. If the sensor is precise but has low sensitivity (e.g., low range of outputs for the expected range of inputs), its measurements can have a low variance, which can contribute to a lower covariance between the sensor and Ground Truth measurements. This is an early indicator that, although there is a consistent positive relationship between the values, the sensor would be a sub-optimal predictor of the Ground Truth values. A different sensor with higher sensitivity (higher range of accurate outputs) would have a higher absolute variance and a higher covariance with the Ground Truth values, indicating better suitability for prediction (ultimately evidenced by a tighter confidence interval for the calibration curve).
        - [As note for other Machine Learning tasks, the combination of high correlation and low covariance between two features (input variables) is a good indicator that you can drop one of the two without substantially reducing model effictiveness because the featuers communicate redundant information]. 
    - When formally generating numeric summaries using `.describe()`, as opposed to using the method for basic data validation, I advise against including the date and time variables. We don’t glean any new information by reporting those variables’ statistics beyond confirmation they are correctly defined.
      - Response: I don't think it hurts to include them. They are still variables we analyze across, and the holes in the data introduced during measurement or by cleaning can show up in the `.describe()` summary. When there is potential value and no clear detriment, I don't think it's worth going through extra work to explicitly exclude them.
    - You include the following sentence when discussing the unconditional standard deviations: *Too big or too small of swings are each disadvantageous.* I would argue large swings are only an issue when they correspond to noise in predicting. When big swings in a predictor correspond to big swings in the response, that’s a good thing.
      - Response: Agree that it isn't inherently disadvantagrous to have large standard deviations. It *could* indicate an issue, so I adjusted the language accordingly.
  + Temporal Numeric Summaries section:
    - While I like the MinMax scaling for some of the plots, I find it a bit confusing when looking at measures of center. An example is your heatmap of mean values by month (“Heatmap of Monthly Measurement Average Values”). It is difficult to interpret the variations of skewed variables such as `benzene`. If you want to rescale for a plot/table such as this, I recommend normalizing.
      - Response: If you eliminate the data standardization (e.g., MinMax scaling), it prevents you from quickly visualizing trends with the heat map. Each column would have to be interpreted separately. You couldn't compare the color of the columns against each other to see if one shows a more prominent trend than another because of the differing magnitudes. Further, there would be a bigger total range of values represented by the shared color scale; this would partially or completely mute any trends within a single variable, too. I don't think the absolute values matter here; what matters is whether there is a trend or relationship that can be exploited. A calibration "gain" factor would be used on the back end to recover the absolute scale of the target variable.  
    - In this section, you make the below claim. I don’t think you can write off the weather variables as bad predictors when looking at correlations without conditioning on other predictors. It may be the case that one of these variables adds value in predicting benzene concentration once other variables are controlled for. 
        + "The weather variable standard deviations also show that the previously observed potential weekday dependency is likely not statistically significant; the standard deviation is many times greater than the difference in average values. That means the weather variables are poor candiates for benzene level prediction because they don't follow the same trends (potentially unless a sophisticated model had different calibration parameters based on the day of the week)."
          + Response: While I agree that there could be a trend hidden in there, I think it's obvious that weather variables don't have a first-order effect on benzene concentration. I think my initial wording is appropriate because it doesn't exclude the possibility of a correlation; it just states that the "dependency is likely not statistically significant." It could be, but I wouldn't bet on it. The variation in weekday weather averages are eclipsed by the associated standard deviations. That makes the weather-vs.-weekday trend not statistically significant. 
    - The heat map of variable means by hour is one of my favorite tables/plots I've seen in a long time!
      - Response: Isn't it great how quickly we can create such informative and visually appealing plots with Seaborn?!?
    - Similar to my above comment, the following statement about the weather variables may not be true once other variables are controlled for: 
        + "None of the weather variables have hourly standard deviation trends matching those of benzene, which makes weather variables poor candiates for benzene level prediction."
          + Response: The statement wasn't absolute. Based on available evidence, I believe the weather variables are _poor candidates_ for benzene level prediction. Poor candidates can still prove useful if a sophisticated model finds a way to use them beneficially. But based on the much better correlation and trending with other features, it is clear that the weather variables are not likely as useful.  
  + Key Findings: 
    - While your Key Findings section is very informative, it may contain too much detail. I found the “Overall Conclusions” to offer the exact depth I sought in a conclusion for this notebook. I recommend converting this subsection to a narrative style and using it alone for your Key Findings section. 
      + Response: You're right - this section ended up far longer than intended. Due to the importance of brevity when someone looks for the "key findings", I renamed my lengthier roll-up to "Summary" and renamed the "Overall Conclusions" to "Key Findings."


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
      - Response: Agree, and incorporated. I didn't realize this until you and Cass did it without explicit DataFrame conversion. I got confused because the repository object was a dictionary; I forgot to check what the feature attribute's data type was.
  + Clean the dataset
    - You spent a considerable amount of time addressing missing values. This approach is fine, but I’m not sure all of that detail was needed for the data‑cleaning step.
      - Response: I agree that not all of that work was necessary for simply cleaning the data. Because my task was focused on EDA, I spent some extra time exploring the nature of those missing values to see if it provided any insights as to why they existed (e.g., a single extended outage affecting everything vs. seemingly random, short outages affecting everything vs. random outages only affecting some of the measurements at a time). I definitely took the "scenic route" getting to a cleaned data set.
  + Temporal Plots
    - You could consider removing the first plot (In [19], using col_list = benzene, T, RH, AH) since it doesn’t add meaningful insight.
      - Response: Cass mentioned the same thing. I think it's worth showing one instance of how even a partial dataset is too crowded to view all at once. This justifies the need to use lots of plots with only or two variables later on. 
    - For In [20], you may want to either suppress the warnings or move them so that they don’t interrupt the narrative flow.
      - Incorporated
    - Your plot_relative_dailyminmax function is well defined and efficiently to check the trends across variables. The plots make the trends very easy to see. Nice work on that!
  + Non-Temporal Plots
    - You may want to revise the phrase 'the numeric summaries in this section may be displayed using a heatmap,' since you are already using a heatmap to summarize your numeric variables.
      - Incorporated
    - There is a lot of information presented in these plots, but your interpretation is strong and helps the reader understand the key patterns.
  + Non-Temporal Numeric Summaries
    - The heatmap for the correlation matrix is effective, and your explanation is clear and accurate.
    -	This section is well done.
  + Temporal Numeric Summaries
    - The overall structure is strong, and the patterns in the variables are clearly visible.
  + Key Findings
    - In your conclusion, you mentioned that benzene did not follow the same seasonal (or day to day) trend as any weather variable. However, in my section, when looking at the mean benzene levels, I did observe a seasonal trend. This difference may be we used different aggregation methods or different values to generate our plots.
      - Response: This is an interesting discussion point. I think it comes down to how we define "seasonal." Even though the values were not uniform or randomly distributed throughout the year, I didn't consider the dip in August and the subsequent peak to be "seasonal" because they are relatively short duration and don't appear to have a periodicity that would be repeated in future years. I saw these more as anomalies. The temperature and absolute humidity plots clearly show a behavior that I would consider "seasonal." It's hard to tell if benzene has seasonal variation based on a single year of data and trends that don't match climate-based seasonal patterns.
    - In the Non Temporal Plots section, you missed a colon after “Benzene vs. Other Pollutants”.
      - Incorporated








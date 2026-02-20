Each group member should provide feedback on the other group members’ work. Be detailed and specific where possible. The quality of this feedback can play a part in your grade.

You can provide feedback to your group members in many different ways (live in a meeting, offline, or however else you devise) but the feedback must be documented here! 

Please replace “Feedback giver #x” with a group member’s name below and add feedback as a bulleted list below. Note: There is a pencil icon on the top right of the README file (when you are viewing the README.md file) that allows you to edit.

- Cass Crews
  + item


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








Each group member should provide feedback on the other group members’ work. Be detailed and specific where possible. The quality of this feedback can play a part in your grade.

You can provide feedback to your group members in many different ways (live in a meeting, offline, or however else you devise) but the feedback must be documented here! 

Please replace “Feedback giver #x” with a group member’s name below and add feedback as a bulleted list below. Note: There is a pencil icon on the top right of the README file (when you are viewing the README.md file) that allows you to edit.

- Cass Crews
  + Overall:
    - I recommend adjusting the text in the *Introduction* and *Read in Data and Data Cleaning* sections so that they flow as well as the Modeling section. 
    - I think you should include a conclusion to summarize the notebook. 
  + Introduction:
    - The introduction feels choppy, as it begins with more technical details of the dataset before transitioning to the purpose of the notebook. I recommend summarizing the dataset in the introduction and moving the more technical aspects of the dataset to the data reading and cleaning section. 
  + Read in Data and Data Cleaning section:
    - I noted this line of code in the data reading and cleaning section: `clean_df['Time'] = clean_df['Time'].str.replace('.', ':', regex=False)`. 
When reviewing the data, I listed out all the time values present, and I did not see any instances of a “.”. Thus, I don’t think this line is necessary. 
    - It may be worth noting, in a text chunk, that by dropping rows with missing values prior to averaging the hourly values, the number of hourly observations you average varies across the days. 
  + Modeling section:
    - The introduction to this section is extremely well-written. I enjoyed reading it!
    - I found the text `benzene (C6H6(GT))` confusing because you had already renamed the corresponding variable `benzene` and the format of text such as `temperature (T)` implies the text in the parantheses is the current variable name. I recommend simply using `benzene` to refer to the benzene concentration.
    - Your description of the line plot is very well written and informative! 
    - The fourth bullet of your procedure should indicate the MSE values are averaged rather than summed. 
    - I’m not certain about this, but I believe the instructions for the MSE helper function imply you should calculate the MSE yourself rather than use a pre-built function within your helper function. 
    - I recommend adding some text between your example calls to the `get_mse()` function to make it clear exactly what each example is doing. 
    - You generally do a great job of formatting code and objects as code within your text chunks. However, there are a few instances, such as in the chunk just before you define `get_CV_error()`, where you don’t use the code formatting. 
    - In the source code for your `get_CV_error()` function, you are accidentally failing to make a prediction for the n’th observation because the `range()` iterative does not include the “stop” value within the sequence. That is, the final value in the range iterative is n-2. The issue arises in the for loop: `for i in range(initial_day, len(df)-1)`.
    - Similarly, the summed MSE values should be divided by `len(df) - initial_day` because you are predicting through the n’th observation. 
    - Nice use of f-strings when printing your model results! 
    - If you are going to express your final model in a standard equation, I recommend defining both the SLR and MLR model generally at the top of the Modeling section. That is, you should specify each model with placeholder parameter estimates. Even if you prefer not to do so, you should indicate $\hat{Y}$ in the final model fit equation is the predicted value of benzene concentration. 



- Trevor Lillywhite
  + item

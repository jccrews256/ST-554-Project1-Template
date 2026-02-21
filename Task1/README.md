Each group member should provide feedback on the other group members’ work. Be detailed and specific where possible. The quality of this feedback can play a part in your grade.

You can provide feedback to your group members in many different ways (live in a meeting, offline, or however else you devise) but the feedback must be documented here! 

Please replace “Feedback giver #x” with a group member’s name below and add feedback as a bulleted list below. Note: There is a pencil icon on the top right of the README file (when you are viewing the README.md file) that allows you to edit.

- Trevor Lillywhite
- _Added 2/15 [early review]_
  + Data cleaning: When iterating through column names, recommend using `for v in df.columns` instead of `for v in df.describe()`. Although the results are the same, it is more readable by a third party to explicitly iterate over the column names instead of a table full of statistics. 
  + I saw at least one cell with a very long line of code. Recommend reviewing and breaking up into different lines when possible for readability.
  + Wow! There are a ton of missing values for some of the "ground truth" variables! Luckily, since benzene is the only GT variable we care about, we can drop the other GT columns without worrying about whether to drop or impute those rows. An added benefit is being able to make even simpler column names since none of the chemical analytes will have both a GT and a simple sensor reading. I did this in Task 2 - feel free to check out my work and copy it, if desired. It is more important for me (in Task 2) to have simpler names since I will be referencing them much more often for EDA. Don't think we have to perfectly match between the tasks.
- _Added 2/20/26 [full review]_
  + Introduction:
    + Readings were only over 13 months, not 14 (per the paper and the dataset start/end dates).
    + Second paragraph: The first and last sentences are redundant. Recommend removing the first sentence for brevity without losing meaning.
  + Data Cleaning: After renaming columns, you used the `.info()` method. Your markdown description of `.info()` misleadingly says that it shows the number of null values by column. It actually shows the number of non-null values, and it takes extra time to determine the number of null values by subtraction from the number of entries. Recommend saying "non-null" instead of "null."
  + Grid Search
    + I'm impressed by your mathematical notation in the markdown cell!
    + Are 10,000 grid elements really warranted? While this data set isn't terribly large and computation time was quick, it's good to get in the practice of being judicious with hyperparameter selection and overall computation time.
      + When you later wrapped this into a function, the description says you'd try 1,000 candidates of c. That seems like a more reasonable sample size. 
    + When using `np.linspace()`, I recommend adding one to the sample size (in this case, you'd create 10,000 evenly spaced _intervals_ using 10,001 points). That helps you avoid ugly decimals with neater spacing. 
    + When printing the minimum RMSE and corresponding c, it is unclear why you used such a complex line of code to find the minimum RMSE.  Why not use something much simpler and easier to interpret like `rmse_df.rmse.min()`? I think the code to find the corresponding value of c can also be simplified a great deal.
    + Astute observation about the optimal RMSE being very close to the sample standard deviation! As sample size gets large, `1/n` and `1/(n-1)` become indistinguishable.
    + I found it interesting that you actually created a grid of parameter options for grid search. When I've seen this done in the past, people normally just have 1D lists of parameters to consider and loop through those directly, instead of populating a grid and iterating through that. The grid isn't usually literally constructed. You can be more computationally efficient if you skip making a literal grid and simply create a list of tuples at the end of the inner `for` loop: `(parameter 1, parameter 2, result)`. That would also let you simplify coding later (no unraveling or using `.argmin()`.  (I don't think it's worth the effort to re-engineer your approach - just food for thought).
    + Did you do anything to verify if the regressed parameters or check values were reasonable? A simple plot of CO_sensor vs. benzene_truth would go a long way, and a superimposed calibration curve would be even better. 


- Joy Zhou
- Added 2/20/2026
  + Overall
    - The data cleaning step is very impressive.
    - You did a nice job building both algorithms. Your steps are clearly explained, and both algorithms run successfully and produce results. All parameters used in the algorithms are well defined and clearly explained.
    - Grid search and gradient descent give similar outputs, except prediction benzene concentration at CO readings of 946, 1075, and 1246
	  - All algorithm functions are working correctly and efficiently, with clear accompanying narrative.
 	  - Nice summary and well writing for this task
    - You might consider using a few bullet points to make the content more readable.
  + Introduction
    - Please check this sentence: 'In particular, we will explore two algorithms the fit our predictive models: grid search and gradient descent'. Maybe change the fit to that fit.
    - For the last three sentences in this introduction section, you might consider using bullet points to make the sequence of steps easier to read and follow.
  + Importing and Cleaning Data
    - I really like how clearly you explained your variables and chose their names.
    - I might consider adding `air_quality_df.describe()` in my task to illustrate how missing values are coded in the dataset.
    - Your approach to handling missing values and constructing the `data_time` variable is appropriate and effective.
    - Verifying the earliest and latest date‑time stamps and ensuring there were no duplicate date‑time entries were good steps to make sure the entire time range was accurately captured.
    - You missed punctuation or a transition word in the sentence ‘carbon monoxide sensor readings were recorded each time benzene concentration was measured, and vice versa.
  + Grid Search Algorithm
     - You may need to revise this sentence to make it clear: 'That is, we will identify c such that we minimize the training RMSE'.
     - Nice work for extracting the minimum RMSE and c value
  + Grid Descent Algorithm
     - Your explanation of the gradient descent steps is clear and easy to follow, and Your code is well structured and readable.
     - Both algorithms identify nearly identical optimal values of c for benzene and CO_sensor, which is nice
     - I am not sure what you intended to say in this comment 'Interestingly, the gradient descent result is inferior to the g'.
     - The predictions of benzene concentration for CO readings of 946, 1075, and 1246 using gradient descent (‑23.42, ‑23.51, ‑23.64) differ substantially from those using grid search (6.02, 9.35, 14.48). Adding one or two sentences explaining why this occurred (e.g., convergence issues, step size, initialization) would strengthen the discussion.
  + Conclusion
    - Your conclusion is clear and captures the main lessons from comparing grid search and gradient descent. I like the fact that you emphasize how a simpler approach can sometimes perform better. 
    - You might consider adding a brief discussion of potential reasons why gradient descent didn’t perform well (such as step size, convergence issues, or sensitivity to initialization) to give readers a fuller understanding of the results.






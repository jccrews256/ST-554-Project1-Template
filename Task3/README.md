Each group member should provide feedback on the other group members’ work. Be detailed and specific where possible. The quality of this feedback can play a part in your grade.

You can provide feedback to your group members in many different ways (live in a meeting, offline, or however else you devise) but the feedback must be documented here! 

Please replace “Feedback giver #x” with a group member’s name below and add feedback as a bulleted list below. Note: There is a pencil icon on the top right of the README file (when you are viewing the README.md file) that allows you to edit.

- Cass Crews
  + item


- Trevor Lillywhite
  + _Added 2/19/26_
  + Overall impression: Your narrative was clear. Code was well documented with #comments and markdown. Code was not overly complex. Good work!
  + [Minor editorial comments]
      + The first cell would be a little more professional using header formatting (# key)
      + The "Introduction" cell includes a list of variables. This would be easier to read if formatted as bullets (+ key)
      + The "Introduction" cell has a grammar error in the second sentence: "dataset is a time-series dataset contains 9,358 hourly air-quality measurements records"
      + The code under "Read in Data" has a typo ("first" spelled as "frist")
      + The markdown cell above your `get_CV()` function definition says "VC" instead of "CV"
  + 2nd cell (`git! clone ...`): Recommend deleting. Don't know why it's needed, and it returns a fatal error.
  + When creating a subset with one row per day, you adjusted the `Time` format, and created a `Date_Time column`. These steps were unnecessary and unhelpful because you grouped by `Day` right afterwards - `Time` is irrelevant for Task 3. Recommend deleting those unnecessary steps.
  + "Modeling" description: first off, I love this. Very well communicated. I have a question about one of your claims. You said that classical CV assumes data is i.i.d.  I think that's largely true, but very commonly used methods like K-fold CV can easily accommodate imbalanced datasets (some categories are much more prominent than others) via sample stratification in each fold. So does classical CV need data to be i.i.d., or just independent? Not sure the "identically distributed" property is required. (I'm also not a statistician like most of you in this class, so please let me know if I'm thinking about this incorrectly!)
  + "Modeling" description: Per the discussion on Slack, we should average the MSEs instead of simply summing them. It looks like you actually fixed the code, but the last bullet of the description needs to be updated to match.
  + Your temporal plot cell unnecessarily imports `pyplot` and `seaborn` a second time. This was already done at the beginning.(This also occurs near the bottom with `linear_model`.)
  + When you wrapped the MSE calculation into a function, you asked for arguments of the entire DataFrame and column names for the predictors and response variable. It defintiely works (and I actually think your method is more user-friendly), but it might not be 100% compliant with the instructions, which asked for X as a DataFrame and a 1D response y. Just in case that's a grading issue, I recommend modifying the function to pass in a DataFrame and a Series instead of the current arguments.
  + The `return` line for `get_CV()` calculates an average MSE. I think you should use `len(df)` instead of `(len(df)-1)` in the denominator. For example, if `initial_day` = 250 and `len(df)` = 251, it would still calculate one single MSE, and the denominator would need to be 1 instead of 0.
  + When interpreting the final comparison between SLR and MLR, I recommend also saying that MLR is chosen because the results are significantly better than SLR, making the additional complexity worth it.  (If the MLR was only very slightly better, we might have had grounds for going with SLR anyways). 

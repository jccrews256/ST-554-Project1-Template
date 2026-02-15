Each group member should provide feedback on the other group members’ work. Be detailed and specific where possible. The quality of this feedback can play a part in your grade.

You can provide feedback to your group members in many different ways (live in a meeting, offline, or however else you devise) but the feedback must be documented here! 

Please replace “Feedback giver #x” with a group member’s name below and add feedback as a bulleted list below. Note: There is a pencil icon on the top right of the README file (when you are viewing the README.md file) that allows you to edit.

- Trevor Lillywhite
- _Added 2/15_
  + Data cleaning: When iterating through column names, recommend using `for v in df.columns` instead of `for v in df.describe()`. Although the results are the same, it is more readable by a third party to explicitly iterate over the column names instead of a table full of statistics. 
  + I saw at least one cell with a very long line of code. Recommend reviewing and breaking up into different lines when possible for readability.
  + Wow! There are a ton of missing values for some of the "ground truth" variables! Luckily, since benzene is the only GT variable we care about, we can drop the other GT columns without worrying about whether to drop or impute those rows. An added benefit is being able to make even simpler column names since none of the chemical analytes will have both a GT and a simple sensor reading. I did this in Task 2 - feel free to check out my work and copy it, if desired. It is more important for me (in Task 2) to have simpler names since I will be referencing them much more often for EDA. Don't think we have to perfectly match between the tasks.    


- Feedback giver #2
  + item

# Quiz questions

This is only a "quiz" in the loosest sense that it's asking questions whose
answers will be part of your grade. Please use *any resources you want*, as
long as you list those resources (e.g. peers, websites, etc.)

## Navigating logs

1. What is the SHA for the last commit made by Prof. Xanda on the branch
xanda_0000_movie_processing?
(For this and future questions, the first 5 characters is plenty - neither
Git nor I need the whole SHA.)

c492aa23

2. What is the SHA for the last commit associated with line 9 of this file?

b2ed39de

3. What did line 12 of this file say in commit d1d83?

"I should really finish writing this."

4. What changed between commit e474c and 82045?

processs_movie_data.py was changed on the following lines: 

-    gross_sort = lambda x : x["Gross"]
+    gross_sort = lambda x : int(x["Gross"])

-    top_five = rows[:-5:-1]
+    top_five = rows[:-6:-1]

## Predicting merges

Assume at the start of each of these three questions that your
branch for switching to a top-10 list was called `top_ten`
and your branch generalizing to any number of movies was called `top_N`.
Predict the behavior of these three possible operations - you don't
have to provide a full `diff` but you should describe at a high level
what changes would happen.

These questions are supposed to be separate paths, not cumulative;
for example, you should *not* assume that the operations of 5 were run
before 6. When testing outcomes later in the lab, you should make sure to
revert back to the state of the branch before you started these questions.

5. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git merge top_N

When I merged top_N into test, there were not any merge conflicts. The message git showed explained that it was updating the branch from commit bd46ca0 (prevous commit on test) to 6ecaffb (latests state on top_N). Git used a fast forward merge which means that a merge wasn't required because top_N was ahead of test so instead the pointer for test is changed to match the latest of top_N. In this process, only the process_movie_data file had any changes. 

6. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout top_ten
git merge test
```
When I merged test into top_ten, there were not any merge conflicts, and git gave the following message: Merge made by the 'ort' strategy. Upon googling, ort is a new merge operation that helps more efficiently solve conflicts. The top_ten branch changed because it took on the latest changes frolm test. 

7. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git rebase top_ten
git rebase top_N
```
On the first rebase command when we tried to rebase with top_ten, git returned that "Current branch test is up to date" which means there were not any new commits on the top_ten branch that the test branch wasn't already up to date with. This command essentially didn't do anything. When I ran the second rebase command with top_N, there was a merge conflict on the process_movie_data file because one version had N and the other had 10 so git didn't know which part to keep. Once resolving the conflict, Git "Successfully rebased and updated refs/heads/test" indicating the rebase operation worked as expected. 
```

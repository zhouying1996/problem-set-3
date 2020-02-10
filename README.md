## Problem Set 3: Trees & Machines 

#### Fork the repository

Fork the repository for the problem set 3, `problem-set-3` (https://github.com/macss-ml20/problem-set-3). _Remember, all final submissions should be a single rendered PDF with code produced in-line._ Also, don't forget to **open the pull request** once you've committed your final submission to your forked repository. It needs to be merged back into the course master branch to be considered "submitted". See the syllabus for details.

#### The Data

##### ANES 2008

For the first part of this problem set, you will again be using the ANES data to predict feelings toward Joe Biden, but this time by growing and tuning several decision trees. 

As a refresher, the `nes2008.csv` data contains a paired down selection of features from the full [2008 American National Election Studies survey](http://www.electionstudies.org/). These data will allow you to test competing factors that may influence attitudes towards Joe Biden.

##### OJ Data

For the second part of the problem set on support vector machines, you will use the `OJ` data from the `ISLR` package, which contains 1070 purchases where the customer data related to orange juice purchases. A number of characteristics of the customer and product are recorded. Your goal here is to find a classification solution by tuning support vector classifiers that optimially predict whether customers buy either Citrus Hill (CH) or Minute Maid (MM) Orange Juice.

_Important Note:_ Recall, there are many R and Python packages that allow you to complete the problem set in a variety of ways. I care less about your coding approach and selected packages, and significantly more about your results. Thus, feel free to use any programming language, and also any package/approach in your selected language.

### Decision Trees

1. Set up the data and store some things for later use:
    * Set seed
    * Load the data 
    * Store the total number of features minus the biden feelings in object `p`
    * Set $\lambda$ (shrinkage/learning rate) range from 0.0001 to 0.04, by 0.001

2. (10 points) Create a training set consisting of 75% of the observations, and a test set with all remaining obs. **Note**: because you will be asked to loop over multiple $\lambda$ values below, these training and test sets should only be integer values corresponding with row IDs in the data. This is a little tricky, but think about it carefully. If you try to set the training and testing sets as before, you will be unable to loop below.

3. (15 points) Create empty objects to store training and testing MSE, and then write a loop to perform boosting on the training set with 1,000 trees for the pre-defined range of values of the shrinkage parameter, $\lambda$. Then, plot the training set and test set MSE across shrinkage values.

4. (10 points) The test MSE values are insensitive to some precise value of $\lambda$ as long as its small enough. Update the boosting procedure by setting $\lambda$ equal to 0.01 (but still over 1000 trees). Report the test MSE and discuss the results. How do they compare?

5. (10 points) Now apply bagging to the training set. What is the test set MSE for this approach?

6. (10 points) Now apply random forest to the training set. What is the test set MSE for this approach?

7. (5 points) Now apply linear regression to the training set. What is the test set MSE for this approach?

8. (5 points) Compare test errors across all fits. Discuss which approach generally fits best and how you concluded this.

### Support Vector Machines

1. Create a training set with a random sample of size 800, and a test set containing the remaining observations.

2. (10 points) Fit a support vector classifier to the training data with `cost = 0.01`, with `Purchase` as the response and _all_ other features as predictors. Discuss the results. 

3. (5 points) Display the confusion matrix for the classification solution, and also report both the training and test set error rates. 

4. (10 points) Find an optimal cost in the range of 0.01 to 1000 (specific range values can vary; there is no set vector of range values you must use).

5. (10 points) Compute the optimal training and test error rates using this new value for cost. Display the confusion matrix for the classification solution, and also report both the training and test set error rates. How do the error rates compare? Discuss the results in substantive terms (e.g., how well did your optimally tuned classifer perform? etc.)

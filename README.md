# loan-default-prediction
Explorations of loan data and predicting defaults

csv dataset located here: https://www.kaggle.com/wendykan/lending-club-loan-data

### Part 1: Data Exploration and Evaluation

Since there were only 4 rows of data that had null values (in annual income), I removed these directly

After visualizing distributions of continuous variables, I removed 16k+ values of outliers (> 99th percentile) for annual income, debt-to-income ratio, and revolving balance.

### Part 2: Business Analysis

For this part, I filtered down the dataset into only loans with term = 36 months and issued in 2012 or earlier.

1) 87% of loans among this subset were fully paid
2) 2007's grade G loans had the highest default rate (100%), which makes sense going into the financial crisis.
3) As expected, grade A loans have the highest rates of return on average (~2%) but have dropped slightly across 2007-2012. Contrarily, the return on lower grade loans has climbed pretty steadily over this period (from being negative in 2007).
See graph in notebook


### Part 3: Modeling

I initially chose manually selected features based on which ones seemed to have highest impact on loans.

The resulting logistic regression model did not perform very well. Although it had a 87% accuracy, it was just assuming all loans would not default (null hypothesis). For this scenario, I also wanted to use recall as a measure of model performance, since we'd want to identify as many defaults as possible to minimize bad debt.

I used the following 3 methods to try and improve model performance (measured through overall accuracy as well as recall).

1) grid search across different model parameters with cross validation
Result: accuracy and recall of 74%

2) feature engineering (added funded-to-loan-ratio as possible indicator of risk)
Result: no improvement in accuracy or recall

3) feature selection starting with an expanded feature set
Result: no improvement in accuracy or recall

Ultimately, my original manually-selected features model with grid search seemed to work best.

# econ3916-lab12-ols-prediction
Lab 12 submission

# OLS as a Line of Best Fit: Estimation versus Prediction

## Objective
I wanted to see how the same OLS regression can serve two different goals, estimating a coefficient and predicting new outcomes, and why the tools for judging each one are different.

## Methodology
- I fitted the same OLS line three ways: with the closed-form formula, with `statsmodels`, and with `scikit-learn`. All three gave the same intercept and slope.
- I added up to 100 columns of pure noise to a regression and tracked R-squared and adjusted R-squared as each set of columns went in.
- I split the data into training and test rows before fitting anything, then fitted an eight-feature model on the training rows only.
- I scored that model with RMSE twice: once on the rows it was fitted to and once on the test rows it never saw.
- I used one specification for two jobs: reading off a coefficient with its 95% confidence interval, and computing a test RMSE.
- I wrote a small function, `holdout_rmse()`, that takes any list of predictors and scores the resulting model on the same test rows. I used it on median income alone.
- *(Challenge)* I dropped the districts sitting at the 5.0 ceiling and refitted.

## Key Findings
- **Three methods, one line:** the closed form, `statsmodels` and `scikit-learn` all gave a slope of [YOUR VALUE].
- **R-squared never goes down:** R-squared was [YOUR VALUE] with no noise and [YOUR VALUE] with 100 noise columns. It rose every time I added noise, even though the noise has no relationship with the outcome. Adjusted R-squared did not rise, because it penalizes each extra column.
- **Training fit overstates performance:** the eight-feature model had a train RMSE of [YOUR VALUE] and a test RMSE of [YOUR VALUE]. Only the test number tells me how the model does on data it has not seen.
- **Estimation and prediction answer different questions:** the AveRooms coefficient was [YOUR VALUE], with a 95% CI of [YOUR VALUE]. That interval describes how precisely I estimated one relationship. The test RMSE describes how well the whole model predicts. A good result on one says nothing about the other.
- **A single predictor as a baseline:** with median income alone, the test RMSE was [YOUR VALUE].
- *(Challenge)* **Dropping the 5.0 ceiling:** [YOUR RESULT]

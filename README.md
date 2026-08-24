# MAT 303 Module One Problem Set: Multiple Regression Analysis

## Project Overview

This repository contains the work for the Module One Problem Set for MAT 303 (Applied Statistics for STEM). The primary goal of this project is to perform a multiple regression analysis on the classic `mtcars` dataset using R.

As an analyst for a car manufacturer, the objective is to investigate the relationship between a vehicle's fuel economy (`mpg`) and two key design specifications: its rear axle ratio (`drat`) and gross horsepower (`hp`). The analysis includes building a first-order multiple regression model, evaluating its statistical significance, verifying model assumptions, and using the model to make predictions with associated confidence and prediction intervals.

## Repository Contents

This repository includes the following files:

- **`MAT303_Module_One_Problem_Set_Report.docx`**: The final written report in Word format. This document contains the full analysis, including the introduction, methodology, results, interpretation, and conclusion, following the problem set's guidelines.
- **`Module One Problem Set Jupyter Notebook V2.html`**: An HTML export of the Jupyter Notebook that contains all the R code used to perform the analysis. This file is a comprehensive log of the code execution, including data loading, visualization, model fitting, and diagnostic checks. It serves as the technical appendix for the report.
- **`MAT 303 Module One Problem Set Guidelines and.txt`**: A text file containing the original assignment instructions and rubric provided by the course.

## Key Analysis Performed

The analysis within the Jupyter Notebook and report follows these key steps:

1.  **Data Preparation**: Loading the `mtcars` dataset and ensuring variables are correctly typed.
2.  **Correlation Analysis**: Visualizing the relationships between `mpg`, `drat`, and `hp` using scatterplots, and quantifying these relationships with Pearson correlation coefficients.
3.  **Multiple Regression Model**: Building a first-order multiple linear regression model with `mpg` as the response variable and `drat` and `hp` as predictors.
4.  **Model Evaluation**:
    - Reporting R-squared and Adjusted R-squared values to assess model fit.
    - Performing an overall F-test to determine the model's significance.
    - Conducting individual t-tests for each predictor to evaluate their unique contribution.
5.  **Diagnostic Checking**: Using residual plots (Residuals vs. Fitted) and Q-Q plots to verify the assumptions of homoscedasticity and normality of errors.
6.  **Predictions**: Using the final model to predict the fuel economy for a new vehicle with a specified rear axle ratio (3.15) and horsepower (120). This is accompanied by 95% prediction and confidence intervals.

## How to Use This Repository

1.  **For Reviewers/Instructors**: The primary documents for review are the **Problem Set Report (DOCX)** and the **Jupyter Notebook (HTML)**. The report provides the narrative and interpretation, while the HTML file provides the underlying code and raw outputs.

2.  **For Students**: This repository can be used as a reference example for performing a similar analysis on the `mtcars` dataset or for understanding the structure of a comprehensive statistics report. To replicate the analysis:
    - Open the `Module One Problem Set Jupyter Notebook V2.html` file in any web browser to view the code and its outputs.
    - The `mtcars` dataset is built into R and can be loaded directly, or you can use a `mtcars.csv` file as shown in the notebook.

### Key Code Blocks from the Notebook

The notebook breaks down the analysis into clear, executable steps:

```r
# ----- Block 4: Multiple regression model -----
model2 <- lm(mpg ~ drat + hp, data=mtcars_subset2)
summary(model2)

# ----- Block 8: 95% confidence intervals for parameters -----
conf_95_int <- confint(model2, level=0.95)
round(conf_95_int, 4)

# ----- Block 9: Prediction for drat=3.15, hp=120 -----
newdata2 <- data.frame(drat=3.15, hp=120)

prediction_pred_int2 <- predict(model2, newdata2, interval="predict", level=0.95)
round(prediction_pred_int2, 4)

prediction_conf_int2 <- predict(model2, newdata2, interval="confidence", level=0.95)
round(prediction_conf_int2, 4)

Key Findings
The multiple regression model is statistically significant (F-statistic = 41.52, p < 0.001).

Both predictor variables are significant at the 5% level.

Rear Axle Ratio (drat): Holding horsepower constant, a one-unit increase in rear axle ratio is associated with an average increase of 4.70 mpg.

Horsepower (hp): Holding rear axle ratio constant, a one-unit increase in horsepower is associated with an average decrease of 0.052 mpg.

The model explains approximately 74.1% of the variance in fuel economy (R-squared = 0.7412).

Residual diagnostic plots suggest that the model assumptions (normality and constant variance of errors) are reasonably satisfied.

For a new car with drat=3.15 and hp=120, the predicted fuel economy is 19.37 mpg, with a 95% prediction interval of (12.64, 26.10) and a 95% confidence interval of (17.57, 21.18).

Technologies Used
Language: R

Environment: Jupyter Notebook (via Codio)

Key R Functions: lm(), summary(), plot(), cor(), predict(), confint()

Author
Kevin Simmons

Acknowledgments
Dataset: Motor Trend Car Road Tests (1974)

Course: MAT 303 Applied Statistics for STEM, Southern New Hampshire University

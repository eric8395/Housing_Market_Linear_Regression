# Housing_Market_Linear_Regression
Phase 2 - DS Project

## The Business Problem

The King County Development Group (KCDG) wants to look into building a new community of family homes in King County (located in Washington State and near Seattle). Along with the King Contractors (KC), the KCDG needs a better idea on what metrics influence the sale price of a home and would like to get a sense of how to price these homes. KCDG and KC would like to bring on engineers and architects to assist with the design of these homes but need to understand how the sale price of the home will change depending on the design parameters. 

**The intention is to develop a sale price algorithm to help set a target price for a new housing development in King County.** 

 - The main purpose of this algorithm is predictive, meaning that the model should be able to take in attributes of a home that does not yet have a set price, and to predict a sale price for that home. 
 
 - We will also take a look at the model's attributes and explain possible relationships between the attributes of a home and its price. 

**Stakeholders:** The King County Housing Authority (KCHA), King Contractors (KC), prospective architects and engineers. 

## The Dataset
This project uses the King County House Sales dataset found in the `data` folder in this repository. The description of the column names for the data set can be found in `column_names.md` in the same folder. 

## Methods

### Baseline Model
The target variable for this project is `price` with all other columns in the dataset chosen as preliminary predictors for this project. A 75%-25% Train-Test split was performed with `price` as the target variable, `y`. 

As a baseline, the predictor variable with the highest correlation with `price` was `sqft_living` as it was the highest correlated predictor. However, this simple baseline model did not perform well. 

`Base Training R2: 0.4848`<br>
`Base Test R2: 0.475`

<p align="center">
  <img src = "https://github.com/eric8395/Housing_Market_Linear_Regression/blob/main/images/livingroomVSprice.png" width="500" height="400">
</p> 

However, further exploration into the other predictors was needed to determine an accurate model. 

### Target Variable 
Distribution of the target variable `price` was skewed and transformed using a log function to have a more normalized distribution. The target variable `price` would need to be exponentially scaled back to determine final price after conclusion of modeling. 

<p align="center">
  <img src = "https://github.com/eric8395/Housing_Market_Linear_Regression/blob/main/images/scaled_saleprice_distribution.png" width="700" height="350">
</p> 

###Data Cleaning & Preprocessing

The following transformations summarizes the steps done with regards to cleaning and preprocessing and applied to the `X_test` set as follows:

- Drop unnecessary columns, clean the `date`, `grade`, and `basement` columns to integer values. 

- Create encoded nominal values for `waterfront`, `view`, `condition` and `yr_built` columns.

- Log scale the continuous predictors and drop unnecessary columns not logged.

- Encode the zipcodes and concat zipcodes back to the previous dataframe set.

- Apply a standardized scaler to the final dataframe set.

### Note: Transformations and scaling of the testing set was not performed until after assessing the R2 scores after each model was test. However, cross-validation was performed on the test set throughout each iterative model, which was a good indicator that the test set will also perform well after trasnformation and scaling.

## Modeling & Regression Results
The following summarizes the coefficient of determination scores (R2) on each model after scaling/transforming. 

### 2nd Model (after initial preprocessing)
`2nd Model Train R2: 0.7721`

### 3rd Model (removed excess predictors, log numerical variables, added encoded zipcodes)
`3rd Model Train R2: 0.8743`

### 4th Model (applied Standard Scaler)
`4th Model Train R2: 0.8743`

### Validation Checks
`4th Model Train score:       0.875`<br>
`4th Model Test score:        0.8711`

`3rd Model Train score:       0.875`<br>
`3rd Model Test score:        0.8711`

`2nd Model Train score:       0.7714`<br>
`2nd Model Test score:        0.7737`

`Baseline Model Train score:  0.4833`<br>
`Baseline Model Test score:   0.4889`

### Check for Multicollinearity aka Investigating Inference Variables
While the purposes of this project was to perform a predictive model, I also investigated the variables causing colinearity. Changes in one variable may be associated in huge changes in another variable, thus causing issues interpretting the coefficients associated with the predictors. 

## Recommendations


## Next Steps


## Repository Structure

```
├── data
├── images
├── .gitignore
├── Housing Market Analysis Slides.pdf
├── Housing Market Linear Regression.ipynb
└── README.md
```

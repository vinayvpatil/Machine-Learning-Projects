## Ford Car Price Prediction

### Project Overview

This project aims to predict the **price of used Ford cars** based on a dataset of their specifications. By analyzing features such as the car model, year, mileage, transmission type, fuel type, and engine size, the goal is to develop a regression model that can accurately estimate the selling price. This is a valuable tool for car dealerships, buyers, and sellers in the used car market.

-----

### Technical Highlights

  * **Dataset**: A dataset named `ford.csv` is used, which contains a collection of used Ford cars.
  * **Size**: 17,966 entries, 9 columns.
  * **Key Features**:
      * `model`, `year`, `transmission`, `mileage`, `fuelType`, `tax`, `mpg`, `engineSize`.
  * **Approach**:
      * **Data Cleaning**: Duplicate rows were dropped from the dataset. The dataset appears to be clean, with no missing values in the provided sample. The `model` column was cleaned to handle inconsistencies like 'Focus' and ' Focus'.
      * **Exploratory Data Analysis**: Histograms, box plots, and scatter plots were used for visualization to understand data distributions and the relationship between features and the target variable `price`.
      * **Label Encoding**: Applied to all categorical features (`model`, `transmission`, `fuelType`) to convert them into a numerical format.
      * **Data Standardization**: `StandardScaler` was applied to all feature columns to ensure they are on a similar scale.
      * **Regression Task**: The target variable is `price`.
      * **Models Used**:
          * A suite of regression models were trained, including Ridge, XGBoost, Random Forest, AdaBoost, Gradient Boosting, Bagging, Decision Tree, SVR, and K-Nearest Neighbors (KNN).
  * **Best R² Score**:
      * **0.934** with XGBoost Regressor.
      * **0.926** with Random Forest Regressor.
      * **0.921** with Gradient Boosting Regressor.
      * The high R² scores indicate that the models are highly effective at predicting the price of used Ford cars.

-----

### Purpose and Applications

  * Enable car dealerships and buyers to **accurately estimate the value of a used Ford car**.
  * Support data-driven decision-making in pricing and inventory management.
  * Provide a tool for consumers to assess the fairness of a car's price.
  * Serve as a foundational model for a used car market analysis platform.

-----

### Installation

Clone the repository and download the dataset.

Install the necessary libraries:

```bash
pip install pandas numpy seaborn matplotlib scikit-learn xgboost
```

-----

### Collaboration

We welcome contributions to improve the project. You can help by:

  * Performing comprehensive hyperparameter tuning for the top-performing regression models to maximize predictive performance.
  * Exploring more advanced feature engineering, such as creating new features from the dates or combining existing features.
  * Investigating the impact of the data cleaning steps and trying alternative methods.
  * Adding explainability (e.g., SHAP or LIME) to understand which car features are the most significant drivers of price.


LONDON AIRBNB PRICE PREDICTION
==============================

1. PROJECT OVERVIEW
-------------------
This project predicts the nightly price of Airbnb listings in London using
machine learning regression models.

The project uses listing information such as room type, property type,
location, accommodation capacity, bedrooms, beds, bathrooms, amenities,
reviews, availability and host-related features to estimate the nightly price.

2. OBJECTIVE
-----------
To build and compare regression models that estimate the nightly price of a
London Airbnb listing and identify the features that influence prices.

3. DATASET
----------
Dataset: Inside Airbnb - London listings.csv.gz
Snapshot date stated in the notebook: 17 September 2026
Source: Inside Airbnb (insideairbnb.com)

IMPORTANT:
Download the London listings file named "listings.csv.gz" and place it in the
same folder as the Jupyter Notebook or Python script. The project code reads
this exact filename.

The notebook states that the data is licensed under Creative Commons.
Check the dataset source page for the applicable licence and attribution terms.

4. DATA CLEANING
----------------
The project performs the following cleaning steps:
- Converts the price column from text (for example, "$267.50") to numeric.
- Removes listings with missing prices.
- Removes duplicate listings using the listing ID.
- Keeps listings with nightly prices from 20 to 1,000.
- Uses bathroom information from the bathrooms_text column because the
  bathrooms column is empty in the inspected data.

5. FEATURE ENGINEERING
----------------------
The project creates additional features:
- bathrooms_num: numeric bathroom count extracted from bathroom text.
- shared_bath: indicates whether the bathroom is shared.
- amenities_count: number of listed amenities.
- superhost: indicates whether the host is a Superhost.
- dist_centre_km: approximate distance from central London.
- property_group: groups less common property types into "Other".

6. EXPLORATORY DATA ANALYSIS
----------------------------
The notebook explores:
- Nightly price distribution and log-transformed price distribution.
- Price differences by room type.
- The 10 neighbourhoods with the highest median nightly prices.
- Correlations between selected numerical features using a heatmap.

7. MACHINE LEARNING
-------------------
Problem type: Supervised Machine Learning - Regression

Target:
- price (modelled as log1p(price), then converted back to price for evaluation)

Models compared:
- Linear Regression
- Ridge Regression
- Random Forest Regressor
- Histogram-based Gradient Boosting Regressor

The data is split into training and testing sets using an 80:20 split
(random_state=42).

Preprocessing:
- Missing numerical values are filled using the median.
- Numerical features are standardised for Linear Regression and Ridge.
- Categorical features are one-hot encoded.
- Unknown categories are handled by the OneHotEncoder.

8. MODEL EVALUATION
-------------------
The models are compared using:
- R-squared (R2)
- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)

The notebook selects the model with the highest R-squared score on the
original price scale. It also plots actual versus predicted prices and uses
permutation importance to examine feature influence.

9. PROJECT STRUCTURE
--------------------
Keep the project files together in one folder:

London_Airbnb_Price_Prediction/
    London_Airbnb_Price_Prediction.ipynb
    listings.csv.gz
    README.txt
    requirements.txt

10. HOW TO RUN
--------------
1. Install Python 3.10 or later.
2. Open the project folder in Visual Studio Code.
3. Open the VS Code terminal.
4. (Recommended) Create and activate a virtual environment:

   Windows:
   python -m venv .venv
   .venv\Scripts\activate

5. Install the required libraries:

   pip install -r requirements.txt

6. Place listings.csv.gz in the same folder as the notebook.
7. Open the notebook in VS Code and run the cells from top to bottom.

If you run the notebook in Jupyter, make sure the notebook's working
directory contains listings.csv.gz.

11. EXPECTED OUTPUTS
--------------------
- Dataset overview and cleaning information.
- Exploratory data analysis charts.
- Correlation heatmap.
- Comparison table for the four regression models.
- Best-performing model and training/testing R-squared scores.
- Actual-versus-predicted price plot.
- Permutation feature-importance chart.

Note: Model scores and the best model depend on the dataset file and its
contents. No performance score is assumed in this README.

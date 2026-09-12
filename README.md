# 🏠 House Price Prediction System

A machine learning project that predicts the estimated price of a house based on property, location, size, amenities, accessibility, and other housing-related features.

The project includes both a **machine learning notebook** for data analysis and model development and a **Streamlit web application** for making predictions through an interactive interface.

## 📌 Project Overview

The objective of this project is to build a regression-based machine learning system capable of predicting house prices.

The dataset contains **999 house records with 23 features**, including location, property type, BHK, area, construction year, furnishing status, nearby facilities, transportation accessibility, parking, security, amenities, ownership type, and availability status.

The project explores two regression approaches:

* Linear Regression
* Decision Tree Regressor

The trained model is then integrated into a Streamlit application where users can enter property details and receive an estimated house price.

## ✨ Features

* 📊 Exploratory Data Analysis (EDA)
* 🧹 Data preprocessing
* 🔤 Ordinal encoding of selected categorical features
* 🏙️ Location-based features such as state and city
* 🏠 Property-related features such as BHK and property type
* 📐 Area and price-related features
* 🚗 Parking and transportation information
* 🏥 Nearby schools and hospitals
* 🛡️ Security information
* 🏡 Amenities and furnishing details
* 🤖 Comparison of Linear Regression and Decision Tree Regression
* 🌐 Interactive Streamlit web application
* 💰 House price prediction in Indian Lakhs

## 📂 Dataset

The dataset contains **999 rows and 23 columns**.

### Main Features

| Feature                        | Description                            |
| ------------------------------ | -------------------------------------- |
| State                          | State where the property is located    |
| City                           | City where the property is located     |
| Property_Type                  | Apartment, Independent House, or Villa |
| BHK                            | Number of bedrooms                     |
| Size_in_SqFt                   | Property size in square feet           |
| Price_in_Lakhs                 | Target house price                     |
| Price_per_SqFt                 | Price per square foot                  |
| Year_Built                     | Year the property was built            |
| Furnished_Status               | Furnishing condition                   |
| Floor_No                       | Property floor number                  |
| Total_Floors                   | Total floors in the building           |
| Age_of_Property                | Age of the property                    |
| Nearby_Schools                 | Number of nearby schools               |
| Nearby_Hospitals               | Number of nearby hospitals             |
| Public_Transport_Accessibility | Low, Medium, or High                   |
| Parking_Space                  | Availability of parking                |
| Security                       | Security availability                  |
| Amenities                      | Available amenities                    |
| Facing                         | Property direction                     |
| Owner_Type                     | Owner, Builder, or Broker              |
| Availability_Status            | Ready to Move or Under Construction    |

The original dataset also contains `ID` and `Locality`, which are removed during preprocessing because they were not used as meaningful predictive features.

## 🔄 Machine Learning Workflow

```text
Dataset
   ↓
Data Loading
   ↓
Exploratory Data Analysis
   ↓
Data Cleaning & Preprocessing
   ↓
Remove ID & Locality
   ↓
Ordinal Encoding
   ↓
Categorical / Numerical Feature Separation
   ↓
Feature Vectorization
   ↓
Train-Test Split
   ↓
Model Training
   ├── Linear Regression
   └── Decision Tree Regressor
   ↓
Model Evaluation
   ↓
Save Trained Model
   ↓
Streamlit Web Application
   ↓
House Price Prediction
```

## 🧹 Data Preprocessing

The preprocessing pipeline includes:

### 1. Removing irrelevant columns

The `ID` column is removed because it does not provide useful information for predicting house prices.

The `Locality` column is also removed because the locality values in the dataset do not contain meaningful address information.

### 2. Ordinal Encoding

The following categorical features are converted into numerical values using `OrdinalEncoder`:

* Property Type
* Furnished Status
* Public Transport Accessibility
* Facing
* Security

The categories are explicitly defined before encoding.

### 3. Categorical and Numerical Features

The remaining features are separated into categorical and numerical columns.

Categorical features include:

* State
* City
* Parking Space
* Amenities
* Owner Type
* Availability Status

The project uses **DictVectorizer** to convert the input feature dictionary into a numerical feature representation.

## 🤖 Models Used

### Linear Regression

Linear Regression was implemented as a baseline regression model.

Test-set results from the notebook:

* **MAE:** 118.77
* **MSE:** 21,936.66
* **RMSE:** 148.11
* **R² Score:** 0.0312

The relatively low R² indicates that Linear Regression does not capture the relationships in this dataset particularly well.

### Decision Tree Regressor

A Decision Tree Regressor was then trained to capture non-linear relationships between the property features and house prices.

The model achieved:

**R² Score: 0.8983**

This was substantially better than the Linear Regression baseline for this experiment.

## 📊 Model Comparison

| Model                   |   R² Score |
| ----------------------- | ---------: |
| Linear Regression       |     0.0312 |
| Decision Tree Regressor | **0.8983** |

Based on the recorded test-set R² score, the **Decision Tree Regressor** performed better on this dataset.

## 💾 Model Serialization

The trained model and feature vectorizer are saved using Python's `pickle` module:

```text
house_price_model.pkl
vectorizer.pkl
```

These files are loaded by the Streamlit application when the app starts.

## 🌐 Streamlit Web Application

The project includes an interactive Streamlit application.

Users can enter:

* State
* City
* Property Type
* BHK
* Size in Sq.Ft
* Price per Sq.Ft
* Year Built
* Furnished Status
* Floor Number
* Total Floors
* Property Age
* Nearby Schools
* Nearby Hospitals
* Public Transport Accessibility
* Parking Space
* Security
* Amenities
* Facing
* Owner Type
* Availability Status

After entering the property details, the user can click **Predict House Price** to receive the estimated price in Indian Lakhs.

The application loads the trained model, vectorizer, encoder, and feature information before making predictions.

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **Matplotlib**
* **Seaborn**
* **Streamlit**
* **Pickle**
* **Jupyter Notebook**

## 📁 Project Structure

```text
House-Price-Prediction/
│
├── E06_House_Price_Prediction.ipynb
├── app.py
├── E06_house_price_data_less.csv
├── house_price_model.pkl
├── vectorizer.pkl
├── encoder.pkl
├── features.pkl
├── requirements.txt
└── README.md
```

> Make sure the filenames in the repository match the filenames used in the Python code.

## 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd House-Price-Prediction
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

Or install the required libraries manually:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn streamlit
```

### 3. Run the Streamlit application

```bash
streamlit run app.py
```

### 4. Open the application

Streamlit will provide a local URL, usually:

```text
http://localhost:8501
```

## 📓 Notebook

The Jupyter Notebook contains the complete machine learning workflow, including:

* Dataset loading
* Data exploration
* Statistical analysis
* Missing-value checking
* Feature preprocessing
* Encoding
* Model training
* Model evaluation
* Model serialization

The notebook records **999 observations and 23 original features** before preprocessing.

## 🎯 Objective

The main objective of this project is to demonstrate how machine learning regression techniques can be used to estimate house prices from structured property data and deploy the trained model through an interactive web interface.

## ⚠️ Limitations

* The dataset contains only 999 records.
* The predictions depend on the quality and representativeness of the dataset.
* The model should not be treated as a substitute for professional real-estate valuation.
* Property prices can vary significantly based on factors that may not be fully represented in the dataset.
* The model's performance may differ when applied to real-world data outside the training dataset.

## 🔮 Future Improvements

Possible improvements include:

* Testing Random Forest, Gradient Boosting, XGBoost, and other regression algorithms
* Hyperparameter tuning
* Better handling of categorical features
* More comprehensive real-world datasets
* Feature importance analysis
* Improved location-based features
* Adding prediction confidence or an estimated price range
* Improving the Streamlit UI
* Deploying the application online

⭐ If you found this project useful, consider giving the repository a star!

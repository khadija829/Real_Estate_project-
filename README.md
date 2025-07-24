# Real_Estate_project-
 Oman Real Estate Price Analysis:

 Project Objective:

This project simulates a real-world data science task in the real estate domain. The key goals are to:

- Scrape property listings data from two major websites in Oman.
- Clean and integrate the datasets into a consistent format.
- Engineer useful features related to pricing and location.
- Frame and solve a predictive modeling challenge: **predicting property prices**.
- Deliver a complete GitHub repository containing code, data, and documentation.

Websites Used:

The data was collected from the following real estate platforms in Oman:

1. [Dubizzle Oman - Properties for Sale](https://www.dubizzle.com.om/en/properties/)
2. [OpenSooq Oman - Property Listings](https://om.opensooq.com/en/property)

Only **properties for sale** were targeted (not rentals).




 Steps Taken:
 Data Collection:
- Used `requests` and `BeautifulSoup` to scrape listing pages and individual property details.
- Targeted key fields:
-	Title
-	Location
-	Price
-	Size (m²)
-	Number of rooms(if available)
-	Listing type

 Data Cleaning:
- Removed listings with missing or invalid values (e.g., `N/A`).
- Converted text fields like `price` and `size` to numeric.
- Removed top 1% outliers in price and size to reduce skew.
- Merged the datasets from both websites using common columns (`location`, `price`, `size`).

Feature Engineering:
- Created `price_per_m2`: price divided by size.
- Created `log_price`: log-transformed price to reduce skewness.
- Encoded `location` using:
  - Frequency encoding: `location_freq`
  - One-hot encoding for modeling: `location_Muscat`, `location_Sohar`, etc.



  Modeling Approach:

The challenge: **Predict property sale price** based on available features.

- Model Used: `RandomForestRegressor` (via scikit-learn)
- Target Variable: `log_price`
- Features Used:
  - `size`, `price_per_m2`, `location_freq`, and one-hot encoded location variables
- Train-Test Split: 80/20
- Evaluation Metrics:
  - Mean Squared Error (MSE)
  - R² Score

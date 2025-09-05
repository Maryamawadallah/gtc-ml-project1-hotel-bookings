# gtc-ml-project1-hotel-bookings

## 📌 Project Overview
This project focuses on analyzing and preparing the **Hotel Bookings Dataset** to build predictive models for **booking cancellations**.  
The main objective is to perform **data exploration, cleaning, feature engineering, and preprocessing** to create a high-quality dataset ready for machine learning.

---

## 🔍 Steps Performed

### 1. Exploratory Data Analysis (EDA)
- Inspected the dataset shape, column types, and summary statistics.
- Checked for missing values and duplicate records.
- Visualized important aspects of the data:
  - **Target distribution** (`is_canceled`).
  - Hotel types and their cancellation rates.
  - **Outliers** in `adr` (Average Daily Rate) and `lead_time`.
  - **Monthly trends** of bookings and cancellations.
  - Top 10 countries with the highest cancellations.

### 2. Data Cleaning
- Removed duplicates.
- Dropped irrelevant columns (`company`, `agent`).
- Converted `reservation_status_date` into datetime format.
- Handled missing values by dropping rows with small percentages of missing data.
- Treated outliers by capping extreme `adr` values at a reasonable threshold.

### 3. Feature Engineering
Created new informative features:
- **`total_guests`** = adults + children + babies  
- **`total_nights`** = stays_in_weekend_nights + stays_in_week_nights  
- **`is_family`** = binary flag indicating if children or babies are present  

### 4. Preventing Data Leakage
- Dropped columns that contain future information:
  - `reservation_status`
  - `reservation_status_date`

### 5. Encoding Categorical Variables
- **Country**: grouped infrequent categories into "Other" and applied frequency encoding.  
- **Other categorical features** (e.g., `meal`, `market_segment`, `deposit_type`, etc.): applied **One-Hot Encoding**.  

### 6. Final Dataset Preparation
- Removed unnecessary columns after encoding.
- Defined:
  - **Target variable (`y`)**: `is_canceled`
  - **Feature set (`X`)**: all remaining columns
- Split the dataset into **train (80%)** and **test (20%)** using `train_test_split` with stratification.

---

## 📊 Key Insights from EDA
- **Cancellation rate**: around 37% of all bookings.
- **City Hotel** has a higher cancellation rate compared to Resort Hotel.
- Longer **lead times** correlate with higher cancellation rates.
- Seasonal trends show higher cancellations during peak months.
- Certain countries contribute disproportionately to cancellations.

---

## ⚙️ Tech Stack
- **Python**
- **Libraries**: pandas, numpy, seaborn, matplotlib, missingno, scikit-learn

---


## 📂 Project Structure
├── hotel_bookings.csv # Original dataset
├── preprocessing_notebook.ipynb # Code with EDA & Preprocessing
└── README.md # Project documentation

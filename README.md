# Task 1: Data Cleaning and Preprocessing Pipeline

## 📌 Project Objective
The goal of this project was to clean, structure, and preprocess a raw, unformatted customer dataset containing anomalies such as duplicates, missing values, structural text inconsistencies, and mixed date styles. The final outputs have been fully normalized for analytical reporting.

---

## 🛠️ Tools & Libraries Used
* **Platform:** Google Colab
* **Language:** Python 3.14
* **Core Library:** Pandas (Data manipulation and transformation)
* **Data Generation:** Faker (For scaling out a realistic 500+ row simulation)
* **For Coding Help:** Gemini 

---

## 🧼 Step-by-Step Data Cleaning Actions

### 1. Header Standardization
* Removed hidden trailing/leading whitespaces using `.str.strip()`.
* Converted all column headers to a consistent lowercase format using `.str.lower()`.
* Replaced empty spaces between column headers with underscores (`_`) using `.str.replace(' ', '_')` to build uniform `snake_case` variables.

### 2. Duplicate Elimination
* Isolated identical copycat rows using `df.duplicated()`.
* Dropped 15 identical rows using `df.drop_duplicates(inplace=True)`, lowering the structural row baseline from 515 entries to 500 unique profiles.

### 3. Missing Value Imputation (Null Handling)
* Checked row gaps using `df.isnull().sum()`.
* Handled continuous columns (`age` and `annual_salary`) by filling empty slots with their respective column **median values** to maintain statistical balance.
* Dropped records where the essential target element `join_date` was entirely missing via `.dropna()`.

### 4. Text Feature Standardization
* Stripped padding spaces off categorical variables.
* Categorized gender representations cleanly into standard `Male` / `Female` groups.
* Mapped variable country entries (e.g., `US`, `United States`) uniformly into singular target records (`USA`).

### 5. Type Conversions
* Parsed mismatched system date string formats (`/`, `-`, `.`) into unified datetime timestamps (`datetime64[ns]`) using `pd.to_datetime()`.
* Cast float value classifications cleanly into solid tracking integers (`int64`) for `age` and `annual_salary`.

---

## 📊 Final Dataset Structure Verified
The pipeline successfully cleaned the dataset down to a final shape of **103 rows and 7 columns** with **0 missing entries**:

* `customer_id` (int64) - Non-Null
* `full_name` (object) - Non-Null
* `age` (int64) - Non-Null
* `gender` (object) - Non-Null
* `join_date` (datetime64[ns]) - Non-Null
* `country_name` (object) - Non-Null
* `annual_salary` (int64) - Non-Null

# Azure-Data-Factory Pipeline



##  Project Overview

This project demonstrates a complete data cleaning pipeline built using **Azure Data Factory (ADF)**.
The goal is to process raw transactional data and transform it into a clean, consistent, and analysis-ready dataset.

---

##  Pipeline Architecture

The pipeline consists of the following components:

1. **Source**

   * Input dataset: CSV file (Delimited Text)
   * Contains raw sales/order data

2. **Data Flow**

   * Core transformations applied step-by-step:

     * Select
     * Derived Column
     * Filter
     * Sink

3. **Sink**

   * Outputs the cleaned data into a new dataset/file

---

##  Data Cleaning Steps

### 1. Remove Null Values

Applied a filter at the beginning to ensure data quality by removing rows with missing values:

```
!isNull(customer_id) &&
!isNull(order_id) &&
!isNull(order_date) &&
!isNull(product) &&
!isNull(category) &&
!isNull(quantity) &&
!isNull(unit_price) &&
!isNull({Total Amount})
```

---

### 2. Data Type Conversion

* Converted numeric columns from **string → numeric**

  * `quantity`
  * `unit_price`
  * `Total Amount`

---

### 3. Handle Negative Values

* Applied `ABS()` function to ensure all numeric values are positive:

  * `quantity`
  * `unit_price`
  * `Total Amount`

---

### 4. Standardize Category

* Unified all values in the `category` column to:

```
Electronics
```

* Reason: Dataset represents an electronics store only

---

### 5. Column Selection & Structuring

* Selected only relevant columns:

  * order_id
  * order_date
  * customer_id
  * product
  * category
  * quantity
  * unit_price
  * Total Amount

---

## 📈 Output

* Cleaned dataset with:

  * No null values
  * Correct data types
  * Consistent category values
  * Valid positive numeric data

---

##  How to Run

1. Open Azure Data Factory
2. Navigate to the pipeline
3. Enable **Data Flow Debug**
4. Click **Debug** or **Trigger Now**
5. Monitor execution from the **Output** tab

---

##  Project Structure

```
/dataflow
   └── dataflow1

/pipeline
   └── pipeline1

/dataset
   ├── DelimitedText1 (source)
   └── DelimitedText3 (sink)
```

---

##  Key Learnings

* Handling null values early improves pipeline reliability
* Data type consistency is critical for transformations
* Using `ABS()` prevents issues with negative transactional data
* Standardization improves downstream analytics



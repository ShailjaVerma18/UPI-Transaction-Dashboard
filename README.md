# UPI Transactions Power BI Project

## Project Overview
This project demonstrates how to analyze UPI (Unified Payments Interface) transaction data using **Power BI Desktop**. The objective is to transform, profile, and visualize transactional data to generate meaningful insights regarding transaction patterns, customer demographics, and banking activity.

The dataset contains **20,000 records** of UPI transactions, including transaction details, customer demographics, banks involved, payment methods, and merchant information. This project focuses on creating interactive reports with slicers, line charts, column charts, matrix visuals, and bookmarks.

---

<img width="1187" height="664" alt="Screenshot 2025-10-01 195645" src="https://github.com/user-attachments/assets/cbba9851-13bd-455d-ad9a-e4828ec71040" />

<img width="1181" height="657" alt="Screenshot 2025-10-01 195710" src="https://github.com/user-attachments/assets/8841ea55-2830-4b23-8ab6-fc0fdad1c002" />

<img width="1196" height="672" alt="Screenshot 2025-10-01 195731" src="https://github.com/user-attachments/assets/fa79d292-2566-4e04-9edf-bc12a21002a8" />

<img width="1188" height="664" alt="Screenshot 2025-10-01 195817" src="https://github.com/user-attachments/assets/89658468-a1a3-42ce-bcf4-9dc3b2fc24d7" />

---


## Features

- Load UPI transactions from an Excel dataset into Power BI Desktop.
- Transform and clean data using Power Query Editor:
  - Rename queries.
  - Split and clean columns (e.g., Transaction Time).
  - Correct data types for accurate modeling.
- Perform data profiling to understand column quality, distribution, and statistics.
- Configure slicers for interactive filtering:
  - Bank Name Sent & Received
  - City
  - Device Type
  - Gender
  - Age Groups (created using DAX)
  - Merchant Name
  - Payment Method
  - Purpose
  - Transaction Type
- Create **line charts** and **column charts** for:
  - Transaction amounts by month
  - Remaining balance by month
- Use bookmarks to toggle between different chart types interactively.
- Sync slicers across multiple pages for consistent filtering.
- Apply conditional formatting in matrix visuals to enhance data visualization.
- Duplicate report pages for varied analysis.
- Add a matrix visual to display transaction amounts and balances across cities, months, and currencies.

---

## Dataset

- **File:** `Desktop UPI transactions.xlsx`
- **Columns Include:**
  - TransactionID
  - TransactionDate
  - Amount
  - BankNameSent
  - BankNameReceived
  - RemainingBalance
  - City
  - Gender
  - TransactionType
  - Status
  - TransactionTime
  - DeviceType
  - PaymentMethod
  - MerchantName
  - Purpose
  - CustomerAge
  - PaymentMode
  - Currency
  - CustomerAccountNumber
  - MerchantAccountNumber

---

## Data Preparation Steps

1. **Load Data:** Import Excel dataset into Power BI Desktop.
2. **Transform Data:** Use Power Query Editor to clean and transform:
   - Split `Transaction Time` column to remove date.
   - Correct data types for numeric and text fields.
3. **Add Columns:** 
   - Age Groups column using DAX:
     ```DAX
     Age Groups = IF(
         'UPI Transactions'[Customer Age] <= 25, "A1",
         IF('UPI Transactions'[Customer Age] <= 35, "A2", "A3")
     )
     ```
4. **Verify Data:** Ensure no nulls, blanks, or errors. Confirm column data types.

---

## Visualization and Reporting

- **Slicers:** Positioned and sized consistently for all pages.
- **Line Chart:** Visualize transaction amounts over months, smooth interpolation, markers, data labels.
- **Column Chart:** Toggle between line and column charts using bookmarks.
- **Matrix Visual:** Display transaction amounts and remaining balances across months, cities, and currencies.
- **Bookmarks:** Enable interactive switching between:
  - Line Chart Amounts
  - Column Chart Amounts
  - Line Chart Balance
  - Column Chart Balance
- **Conditional Formatting:** Apply color gradients to highlight high and low values in matrix visuals.
- **Syncing Slicers:** Filters applied on one page are reflected across all synced pages.

---

## Power BI Report Pages

1. **Page 1:** Slicers and line/column chart for transaction amounts.
2. **Page 2:** Matrix visual for transaction amounts and remaining balances by month, city, and currency.

---

## Setup Instructions

1. Download and install **Power BI Desktop**.
2. Open Power BI Desktop and click on **Blank Report**.
3. Load the Excel dataset (`Desktop UPI transactions.xlsx`).
4. Transform data using Power Query Editor as per project steps.
5. Build report visuals following the structure described above.
6. Use slicers, bookmarks, and conditional formatting to enhance interactivity.
7. Save the `.pbix` file for sharing or publishing to Power BI Service.

---

## Key Takeaways

- Importance of data understanding and proper data types.
- Data profiling to ensure data quality and completeness.
- Slicer positioning and sizing to maintain a professional report layout.
- Creating interactive reports using bookmarks for different chart types.
- Applying conditional formatting to enhance visual analytics.
- Syncing slicers across pages for consistent user experience.

---

## Tech Stack

- **Tool:** Power BI Desktop
- **Data Source:** Excel Workbook
- **Language:** DAX (for calculated columns and measures)
- **Visualization Types:** Line Chart, Column Chart, Matrix, Slicers, Bookmarks

---

## Author

**Shailja Verma**  

---
## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.


---




# BigMart Sales Data Pipeline - Azure Data Factory Project

## 📌 Project Overview
This project automates the ingestion, transformation, and categorization of a specific CSV file (`BigMart Sales.csv`) using Azure Data Factory (ADF) with Azure Data Lake Storage Gen2 (ADLS).  
The pipeline runs only when the required file is detected, processes it, and categorizes the data based on outlet size.

---

## 🏗 Architecture
1. **Azure Resources Created**
   - **Resource Group**
   - **Azure Data Lake Storage Gen2** (for source & destination folders)
   - **Azure Data Factory**

2. **Source Data**
   - The source folder in ADLS contains files uploaded by the manager.
   - Trigger runs **only** when a file named **`BigMart Sales.csv`** is present.

3. **Pipeline Flow**
   - **Trigger Condition**: Executes only if `BigMart Sales.csv` exists in the Source folder.
   - **Copy Activity**: Copies the file from **Source** (ADLS) to **Destination** (ADLS).
   - **Delete Activity**: Deletes the file from the Source after copying.
   - **Metadata Activity**: Lists all files in the Destination folder.
   - **ForEach Activity**: Iterates over each file.
     - **If Activity**: If file name matches `BigMart Sales.csv` → process further.
   - **Data Transformations** (via Data Flow in ADF):
     - **Select**: Choose required columns.
     - **Sort**: Sort records.
     - **Derived Column**: Add computed fields if needed.
     - **Filter**: Filter records by conditions.
     - **Split by Outlet Size**: Categorize into **Small**, **Medium**, **High** outlet size CSVs.
   - **Final Storage**: Processed files stored in Destination folder in ADLS.

---

## ⚙ Technologies Used
- **Azure Data Factory**
- **Azure Data Lake Storage Gen2 (ADLS)**
- **Data Flow Activities** in ADF

---

## 📂 Folder Structure

adls://source/csv_files/BigMart Sales.csv
adls://destination/csv_files/BigMart Sales.csv
outlet_size/small.csv
outlet_size/medium.csv
outlet_size/high.csv



# BigMart Sales Data Pipeline - Azure Data Factory Project

## 📌 Project Overview
This project automates the ingestion, transformation, and categorization of a specific CSV file (`BigMart Sales.csv`) using Azure Data Factory (ADF).  
The pipeline runs only when the required file is detected, processes it, and categorizes the data based on outlet size.

---

## 🏗 Architecture
1. **Azure Resources Created**
   - **Resource Group**
   - **Storage Account** (for source & destination containers)
   - **Azure Data Factory**

2. **Source Data**
   - The source folder contains files uploaded by the manager.
   - Trigger runs **only** when a file named **`BigMart Sales.csv`** is present.

3. **Pipeline Flow**
   - **Trigger Condition**: Executes only if `BigMart Sales.csv` exists in the source folder.
   - **Copy Activity**: Copies the file from **Source** to **Destination**.
   - **Delete Activity**: Deletes the file from the Source after copying.
   - **Metadata Activity**: Lists all files in the Destination container.
   - **ForEach Activity**: Iterates over each file.
     - **If Activity**: If file name matches `BigMart Sales.csv` → process further.
   - **Data Transformations** (via Data Flow):
     - **Select**: Choose required columns.
     - **Sort**: Sort records.
     - **Derived Column**: Add computed fields if needed.
     - **Filter**: Filter records by conditions.
     - **Split by Outlet Size**: Categorize into **Small**, **Medium**, **High** outlet size CSVs.
   - **Final Storage**: Processed files stored in the destination.

---

## ⚙ Technologies Used
- **Azure Data Factory**
- **Azure Blob Storage**
- **Data Flow Activities** in ADF

---

## 📂 Folder Structure
source/
BigMart Sales.csv
destination/
BigMart Sales.csv
outlet_small.csv
outlet_medium.csv
outlet_high.csv

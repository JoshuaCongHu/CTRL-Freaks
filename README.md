# CTRL-Freaks

## Phase 1: Data Cleaning & Processing Plan
**Due:** Saturday 9/26/2026 @ 11:59 PM

---

## Datasets
We are analyzing Buffalo 311 Service Requests from **2020 to 2026**, which requires merging two datasets:

- [311 Service Requests (July 2008 - May 2024)](https://data.buffalony.gov/Quality-of-Life/311-Service-Requests-July-2008-May-2024-/whkc-e5vr/about_data)
- [311 Service Requests (May 2024 - Present)](https://data.buffalony.gov/Quality-of-Life/311-Service-Requests-May-2024-Present-/3tj7-3tdz/about_data)

---

## Distinct Processing/Cleaning Operations

### 1. Data Integration
Merge the two 311 datasets into one.
- In the report, state the **key column** we joined/stacked on and the **merge method** used

### 2. Duplicate Removal
Both datasets include **May 2024**, so the merge may create overlapping records.
- Check for duplicates using the unique case ID column after merging

### 3. Handling Missing Data
- Some columns inputs say **UNKNOWN**

### 4. Removing Irrelevant Data
Drop columns/rows we don't need.
- Filter records to **2020 - 2026**

### 5. Data Type Conversion
Convert date strings to datetime.
- Example: `"September 3, 2026"` → `2026-09-03`

### 6. Setting Precision
- Round latitude and longitude to the nearest hundredth.

### 7. Feature Extraction
- Split date and time into separate columns for **Created Date** and **Closed Date**
- Extract the **year** from the date columns

### 8. String Cleaning
- Remove special characters from the **Point** column.

### 9. Standardization
- Make column names consistent across both datasets (ex: lowercase, underscores instead of spaces).

### 10. Data Validation
- Remove records where **Closed Date is before Created Date** so we don't get negative wait times.

---

## Submission
`member1_member2_member3_phase_1.zip` containing:
- `report.pdf`
- `src/` folder with commented code

---

## Task Split
| Operation | Assigned To | Status |
|---|---|---|
| 1. Data Integration | Jayda | In-Progress |
| 2. Duplicate Removal | | |
| 3. Handling Missing Data | | |
| 4. Removing Irrelevant Data | | |
| 5. Data Type Conversion | | |
| 6. Setting Precision | | |
| 7. Feature Extraction | | |
| 8. String Cleaning | | |
| 9. Standardizing Column Names | | |
| 10. Data Validation | | |

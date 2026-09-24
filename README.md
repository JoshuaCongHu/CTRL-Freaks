# CTRL-Freaks

## Phase 1: Data Cleaning & Processing Plan
**Due:** Saturday 9/26/2026 @ 11:59 PM

---

## Datasets
We are analyzing Buffalo 311 Service Requests from **2020 to 2026**, which requires merging two datasets:

- [311 Service Requests (July 2008 - May 2024)](https://data.buffalony.gov/Quality-of-Life/311-Service-Requests-July-2008-May-2024-/whkc-e5vr/about_data)
- [311 Service Requests (May 2024 - Present)](https://data.buffalony.gov/Quality-of-Life/311-Service-Requests-May-2024-Present-/3tj7-3tdz/about_data)

---

## Distinct Processing/Cleaning Operations (revised)
changed this after actually looking at the data. the old "dedup on case ID" and "closed before created" ops remove **0 rows** (every ID is unique, the two date ranges dont overlap, and there are no bad dates) so a grader would definately notice. also, rounding lat/lon to 0.01 is like 1.1 km, which kills neighborhood detail. swapped those for ops that actually change rows

| # | Operation | What it fixes |
|---|---|---|
| 1 | Data Integration | Map the two different schemas to one set of column names and stack them |
| 2 | Removing Irrelevant Rows/Columns | Filter to 2020+, drop "Test" rows, 34/28 cols -> 16 (kept census tract for per-person stats) |
| 3 | Data Type Conversion | Dates -> datetime, lat/lon -> float, duplicate flag -> bool, census tract -> same 6 digit code in both |
| 4 | Handling Missing Data | "UNKNOWN" -> NaN; fill aprox 150k missing council districts from `council_district_2011`; flag open cases |
| 5 | Duplicate Removal | 4,769 city-flagged dupes + 13,791 same type/address/day near-dupes |
| 6 | Coordinate Fixing/Validation | 10,126 swapped lat/lon; 309,526 fake (43, -79) placeholder coords; Buffalo bounding box |
| 7 | Category Harmonization | Old vs new type names ("Pot Hole (Req_Serv)" vs "Pothole Issue"), departments, status values |

after ops 2-6 we go from 564,932 rows to 523,933. code is `src/cleaning_ops_2_6.ipynb`, output is `data/cleaned_311.csv`

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
| 2. Removing Irrelevant Rows/Columns | Josh | Done |
| 3. Data Type Conversion | Josh | Done |
| 4. Handling Missing Data | Josh | Done |
| 5. Duplicate Removal | Josh | Done |
| 6. Coordinate Fixing/Validation | Josh | Done |
| 7. Category Harmonization | | |

**data:** csvs arent in the repo bc theyre to big (aprox 230MB), js run `src/cleaning_ops_2_6.ipynb` once and it downloads them into `data/`

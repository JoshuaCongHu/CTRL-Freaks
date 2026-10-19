# CTRL-Freaks: Who Waits Longer in Buffalo?

**CSE 487 Data Intensive Computing, Fall 2026**
**Team:** Jayda Johnson, Meena Kasina, Josh Hu

We study whether Buffalo 311 service requests are resolved equally fast across council districts and neighborhoods, using the City of Buffalo's 311 data from 2020 to 2026.

## Data
Loaded live from the City of Buffalo Open Data Portal, so no data files are stored in this repo:
- [311 Service Requests (July 2008 - May 2024)](https://data.buffalony.gov/Quality-of-Life/311-Service-Requests-July-2008-May-2024-/whkc-e5vr/about_data)
- [311 Service Requests (May 2024 - Present)](https://data.buffalony.gov/Quality-of-Life/311-Service-Requests-May-2024-Present-/3tj7-3tdz/about_data)

## Repo layout
| Path | What's in it |
|---|---|
| `phase1/Phase1report.pdf` | Phase 1 report (data cleaning and EDA) |
| `phase1/src/` | Phase 1 notebook with all cleaning operations and the EDA |
| `phase2/Phase2report.pdf` | Phase 2 report (machine learning and statistical models) |
| `phase2/src/` | One notebook per split: `phase2_A.ipynb`, `phase2_B.ipynb`, `phase2_C.ipynb` |
| `phase2/writeup_A/` | Extra write-up and figures for Split A |

Each Phase 2 notebook rebuilds the cleaned Phase 1 data, adds the shared Phase 2 features (resolution days, month, year, season, before/after May 2024, slow label), then has sections for that split's two algorithms, their charts, and their write-ups.

## Phase 1: Data Cleaning & EDA (completed)
Merged both datasets, applied 8 cleaning operations, and ran EDA, ending with about 524K clean requests.

## Phase 2: ML & Statistical Models (completed)

### Research Questions
1. Which council districts and neighborhoods wait the longest for 311 requests to be resolved?
2. Do response times differ by request type or department, and does that explain the gaps between areas?
3. Have these gaps gotten better or worse from 2020 to 2026?
4. Which neighborhoods share similar service patterns, and do the slowest-served areas have something in common?

### Phase 2 Work Contribution
| Split | Owner | Question it explores | Algorithms |
|---|---|---|---|
| A | Josh | How long do people wait? | Linear Regression, MapReduce |
| B | Meena | Can we predict which requests will be slow? | Logistic Regression, Naive Bayes |
| C | Jayda | What causes some requests to be answered slowly? | Random Forest (outside class), k-Means |

### Key findings
- **Q1:** NORTH stands out even after accounting for request type (about 13.5% longer than DELAWARE). Kenfield, Kensington-Bailey, Kaisertown, Riverside, Schiller Park, and Genesee-Moselle wait the longest.
- **Q2:** Request type explains most of the gaps. It is Random Forest's top factor (31% vs. 13% for location), but some district differences remain.
- **Q3:** The gap between districts roughly doubled from 0.94 days in 2020 to 1.95 days in 2024, the year Buffalo switched 311 systems, then narrowed slightly in 2025 and 2026.
- **Q4:** Neighborhoods fall into four groups. The slowest-served ones have more housing and building violation requests, while the fastest, mostly downtown, have more parking requests.


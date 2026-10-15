# CTRL-Freaks: Who Waits Longer in Buffalo?

**CSE 487 Data Intensive Computing, Fall 2026**
**Team:** Jayda Johnson, Meena Kasina, Josh Hu

We study whether Buffalo 311 service requests are resolved equally fast across council districts and neighborhoods, using the City of Buffalo's 311 data from 2020 to 2026.

## Data
Loaded live from the City of Buffalo Open Data Portal, so no data files are stored in this repo:
- [311 Service Requests (July 2008 - May 2024)](https://data.buffalony.gov/Quality-of-Life/311-Service-Requests-July-2008-May-2024-/whkc-e5vr/about_data)
- [311 Service Requests (May 2024 - Present)](https://data.buffalony.gov/Quality-of-Life/311-Service-Requests-May-2024-Present-/3tj7-3tdz/about_data)

## Repo layout
| Folder | What's in it |
|---|---|
| `phase1/` | Everything from Phase 1: `Report.pdf` and the notebook we submitted |
| `phase2/src/` | One notebook per split: `phase2_A.ipynb`, `phase2_B.ipynb`, `phase2_C.ipynb` |

Each Phase 2 notebook rebuilds the cleaned Phase 1 data, adds the shared Phase 2 features (resolution days, month, year, season, before/after May 2024, slow label), then has sections for that split's two algorithms.

## Phase 1: Data Cleaning & EDA (done)
Merged both datasets, applied 8 cleaning operations, and ran EDA, ending with about 524K clean requests.

## Phase 2: ML & Statistical Models
**Due:** Sunday 10/18/2026 @ 11:59 PM (one day late max, 15% penalty)

### Research questions
1. Which council districts and neighborhoods wait the longest for 311 requests to be resolved?
2. Do response times differ by request type or department, and does that explain the gaps between areas?
3. Have these gaps gotten better or worse from 2020 to 2026?
4. Which neighborhoods share similar service patterns, and do the slowest-served areas have something in common?

### Algorithm splits
| Split | Question it explores | Algorithms |
|---|---|---|
| A | How long do people wait? | Linear Regression, MapReduce |
| B | Can we predict which requests will be slow? | Logistic Regression, Naive Bayes |
| C | What causes some requests to be answered slowly? | Random Forest (outside class), k-Means |

## How we work (no merge conflicts)
- **`main` is the final submission only.** We don't touch it until we all agree we're ready.
- **Everyone works on their own branch** (`Jayda`, `Meena`, `Josh`) and only edits their own notebook.
- **In Colab:** open your notebook from your branch, then save with **File → Save a copy in GitHub** and pick your branch.
- **Sunday:** each person opens a pull request from their branch into `main`.

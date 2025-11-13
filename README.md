# Global Cancer Research vs. Disease Burden

**Repository Overview**  
This project analyzes the misalignment between global cancer research activity (clinical trials) and disease burden (measured in DALYs from the Global Burden of Disease dataset).

---

## Table of Contents

1. [Project Description](#project-description)  
2. [Folder Structure](#folder-structure)  
3. [Data Sources](#data-sources)  
4. [Dependencies](#dependencies)  
  

---

## Project Description



---

## Folder Structure

```

├── Code/
│   ├── Clean.R              # Clean data with LLM
│   ├── Visual.R 

├── Data/
│   ├── ctg_clean.csv
│   ├── gbd_death.csv
└── README.md                              # This file

````

---

## Data Sources

### **1. ClinicalTrials.gov — Global Interventional Cancer Trials**

**File:** `Data/ctg_clean.csv`

**Source:** U.S. National Library of Medicine

**Access:** [https://clinicaltrials.gov/](https://clinicaltrials.gov/)

This dataset contains over **12,000 cancer-related interventional trials** worldwide.
It includes:

* `NCT Number` — unique trial identifier
* `Study Title`, `Study Status`, `Study Type`, `Phase`
* `Conditions` (normalized into 35 cancer categories using an LLM)
* `Interventions` (DRUG, RADIATION, BEHAVIORAL, DEVICE, etc.)
* `Sponsor` and `Sponsor_type` (Academic, Industry, Government, Hospital)
* `Start Date` (standardized to year–month)
* Geographic `Locations`

**Used for:**
Computing **research activity** by cancer type (trial count and trial share %).

---

### **2. IHME Global Burden of Disease (GBD) — Global Cancer DALYs**

**File:** `Data/gbd_death.csv`

**Source:** Institute for Health Metrics and Evaluation (IHME)

**Access:** [https://ghdx.healthdata.org/gbd-results-tool](https://ghdx.healthdata.org/gbd-results-tool)

This dataset reports global disease burden metrics across cancer types.
It includes:

* `Cause` — mapped to the same 35 cancer categories used in CTG
* `Measure` — DALYs, Deaths, Incidence, etc.
* `Metric` — Number, Percent, Rate
* `Value (val)` — measurement value
* `Year`, `Sex`, `Age`, `Location`

For this project, we specifically use:

* **DALYs (% of total)**
* **Global** location
* **Both sexes**
* **All ages**
* **Most recent year** available per cancer type


---

## Dependencies

* **R (≥ 4.0.3)**

---





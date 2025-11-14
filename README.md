# Global Cancer Research vs. Disease Burden

#### Group Member: Gregory Forsberg, Khaleesi Chen, Xiaofan Liu


**Repository Overview**  
This project analyzes the misalignment between global cancer research activity (clinical trials) and disease burden (measured in DALYs from the Global Burden of Disease dataset).

---

## Table of Contents

1. [Project Description](#project-description) 
2. [Motivation](#Motivation) 
3. [Folder Structure](#folder-structure)  
4. [Data Sources](#data-sources)  
5. [Dependencies](#dependencies)  

---

## Motivation


Cancer imposes a substantial and growing global health burden. In 2022, there were **20 million new cancer cases** and **9.7 million deaths**, with lifetime risk reaching **1 in 5 people** worldwide. Projections indicate that by **2050**, annual incidence will rise to **35 million cases**.

Despite this scale, access to diagnosis and treatment remains highly uneven: for example, women in low-HDI countries are **50% less likely** to be diagnosed with breast cancer than those in high-HDI regions. These disparities raise a critical question for global health research:

 **Does clinical trial activity align with global cancer burden?**

Because clinical trials drive therapeutic innovation, mismatches between research focus and disease burden may exacerbate existing inequities. This project systematically compares **clinical trial distribution** with ** DALY-based global cancer burden** across 35 cancer types to evaluate the extent of alignment—and identify areas of underinvestment.





---

## Project Description

This project examines the alignment between global clinical trial activity and the global burden of cancer. Using data from ClinicalTrials.gov and the Global Burden of Disease (GBD) study, the analysis harmonizes over 12,000 cancer clinical trials and 20,000 disease burden records across 35 standardized cancer types.

A key component of the workflow is the use of a Large Language Model (GPT-4) to normalize heterogeneous clinical trial condition labels into a consistent ontology, enabling accurate comparison across datasets. Trial activity is quantified by each cancer type’s share of global trials, while disease burden is measured using DALY percent from GBD.

Through integrated visual and statistical analysis, the project identifies cancers that are over-represented in research relative to their global burden (e.g., breast and prostate cancer) and those that appear under-studied despite high morbidity and mortality (e.g., liver, cervical, and esophageal cancers). Additional analyses explore patterns in trial sponsors, intervention types, and temporal trends.

Overall, this work provides a reproducible framework for evaluating research equity, highlighting gaps in global cancer innovation and informing priorities for future clinical research efforts.


---

## Folder Structure

```

├── Code/
│   ├── Clean.R              # Clean data with LLM
│   ├── Visual.R 

├── Data/
│   ├── ctg_clean.csv
│   ├── gbd_death.csv

├── Result/
│   ├── Clinical Trial Share vs. Death Share by Cancer Type.png 
│   ├── Number of Clinical Trials by Sponsor Type.png
│   ├── Global Mortality Rates Map.png
│   ├── Average Death Rate by Cause.png
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





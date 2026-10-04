# Healthcare Analytics for Doctor Visits

Exploratory analysis and prediction of doctor visits using patient health, income, and coverage data. Built in Python on Google Colab.

## Problem Statement

Hospitals and health insurers often can't tell why some patients visit a doctor far more often than others, which makes it hard to plan resources, manage costs, and spot high-need patients early. This project analyzes 5,190 patient records to find which factors are most strongly linked to the number of doctor visits, and builds a simple model to flag likely visitors.

## Dataset

5,190 records and 13 columns.

| Category | Columns |
| --- | --- |
| Doctor visits (target) | `visits` |
| Personal | `gender`, `age` |
| Financial | `income` |
| Health | `illness`, `reduced`, `health`, `nchronic`, `lchronic` |
| Healthcare support | `private`, `freepoor`, `freerepat` |
| Record ID | `Unnamed: 0` (dropped) |

Notes: `age` is stored as age/100 and `income` as income/10,000. `visits` is a count with many zeros.

## Project Workflow

1. **Data cleaning:** dropped the ID column, converted yes/no columns to 1/0, converted scaled age to years, created age groups.
2. **Exploratory data analysis:** compared visits against age, gender, income, illness, chronic conditions, and coverage type, plus a correlation heatmap.
3. **Modeling:** trained Logistic Regression and Random Forest to predict whether a patient has at least one visit (80/20 stratified split, balanced class weights).
4. **Insights:** feature importance and group comparisons.

## Key Results

- About 20% of patients had at least one doctor visit; most had zero.
- Strongest drivers of visits: days of reduced activity, number of illnesses, and age.
- Patients with 2+ illnesses average about 0.48 visits, versus 0.19 for those with 0 or 1.
- Coverage differs: the free-repatriation group visits most (about 0.47 on average), the free-poor group least (about 0.16).
- Random Forest reached about 73% accuracy (Logistic Regression about 71%).

**Limitations:** the data is observational, so findings are associations rather than proof of cause. Because `visits` is mostly zeros, predictions for the "visited" class are imperfect.

## Tech Stack

- Python
- Google Colab / Jupyter Notebook
- Pandas, NumPy
- Matplotlib, Seaborn
- Scikit-learn

## How to Run

**On Google Colab**
1. Open `Healthcare_Analytics_Doctor_Visits.ipynb` in Colab (File, then Upload notebook).
2. Run the first code cell and upload the dataset CSV when prompted.
3. Run all cells.

**Locally**
```bash
git clone https://github.com/acsahpauline/Healthcare-analytics-for-doctor-visits.git
cd Healthcare-analytics-for-doctor-visits
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
jupyter notebook Healthcare_Analytics_Doctor_Visits.ipynb
```
Place the dataset CSV in the same folder as the notebook.

## Repository Structure

```
Healthcare-analytics-for-doctor-visits/
├── Healthcare_Analytics_Doctor_Visits.ipynb
├── 1776250375-P2-Healthcare_Analytics_for_Doctor_Visits.csv
└── README.md
```

## End Users

Hospitals and clinics, health insurers, public health planners, healthcare analysts, and care teams.

## Future Work

- Try count models (Poisson / Negative Binomial) suited to visit counts
- Tune the models and test other algorithms
- Build an interactive dashboard

## Author

**Acsah Pauline**, final-year Computer Science and Business Systems student, Rajalakshmi Institute of Technology

GitHub: [@acsahpauline](https://github.com/acsahpauline)

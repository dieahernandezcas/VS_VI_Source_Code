# An optimization model for the Violence Selective and Violence Indiscriminate in Colombia.

Source code for the analysis of Selective Violence (VS) and Indiscriminate Violence (VI) in Colombia.

![Status Badge](https://img.shields.io/badge/Status-In%20Development-yellow) ![License Badge](https://img.shields.io/badge/License-MIT-blue) ![Version Badge](https://img.shields.io/badge/Version-1.0.0-informational)

## Project Overview

This project focuses on developing a robust analytical framework to study and quantify patterns of Selective Violence (Violencia Selectiva) and Indiscriminate Violence (Violencia Indiscriminada) across Colombia.

Using data on violent **Cases** (events with or without life-threatening effects) and **Victims** (fatal and non-fatal persons affected), the project aims to:

1.  Clean and process violence data.
2.  Analyze violence dynamics at multiple administrative levels: National (**Pais**), Departmental (**Departamento**), and Regional (**Region**).
3.  Calculate key metrics to understand temporal changes:
    * **Escalation:** Comparison of current events/victims with the immediately preceding month's count.
    * **Intensity:** Comparison with the weighted average of the count over the last 3 years.
4.  Provide processed data and scripts for further analysis or modeling endeavors.

## Folder Structure

The repository is organized as follows:

```
.
Repo_Root/
├── data/               # All data files
│   ├── raw/            # Original raw data files (DO NOT MODIFY)
│   └── processed/      # Cleaned and preprocessed data (e.g., cases_processed_country.csv, victims_processed_dep.csv)
├── notebooks/          # Jupyter notebooks for exploration, analysis, or examples
├── scripts/            # Reusable Python scripts
│   ├── preprocessing/  # Scripts for initial data cleaning and transformation
│   ├── data_generation/ # Scripts to prepare data specifically for modeling (features, etc.)
│   └── modeling/       # Scripts for training and evaluating statistical or machine learning models
│   └── utils/          # (Optional) Directory for common helper functions
├── results/            # Outputs like model performance metrics, final tables, etc.
├── images/             # Visualizations, diagrams, images for README/reports
├── .gitignore          # Specifies intentionally untracked files (e.g., large data files, env files)
└── README.md           # This file

```

## Setup and Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/dieahernandezcas/VS_VI_Source_Code.git](https://github.com/dieahernandezcas/VS_VI_Source_Code.git)
    cd VS_VI_Source_Code
    ```

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    # On Windows:
    # venv\Scripts\activate
    # On macOS/Linux:
    source venv/bin/activate
    ```

3.  **Install dependencies:**
    The required libraries will depend on the specific scripts and models you implement. A `requirements.txt` file will list them.
    ```bash
    pip install -r requirements.txt
    ```

## Usage

1.  **Place Raw Data:** Put your original data files into the `data/raw/` directory. Do not modify these files.
2.  **Run Preprocessing:** Execute scripts in `scripts/preprocessing/` to clean and structure your data. Processed files will be saved in `data/processed/`.
    ```bash
    # Example:
    python scripts/preprocessing/clean_cases_data.py --level country
    python scripts/preprocessing/clean_victims_data.py --level department --id 52 # Example for Nariño
    ```
3.  **Generate Modeling Data:** Run scripts in `scripts/data_generation/` to prepare datasets for modeling (e.g., creating time series, features). These outputs might also go into `data/processed/` or a specific modeling subdirectory within `data`.
    ```bash
    # Example:
    python scripts/data_generation/create_ts_features.py --level region --name Pacifica
    ```
4.  **Run Modeling:** Execute scripts in `scripts/modeling/` to train and evaluate models. Results and model artifacts will be stored in `results/`.
    ```bash
    # Example:
    python scripts/modeling/train_escalation_model.py --level country --target cases
    ```
5.  **Explore and Visualize:** Use the Jupyter notebooks in `notebooks/` to explore data, visualize results, or demonstrate specific analyses.
    ```bash
    jupyter lab
    # or
    jupyter notebook
    ```


## Contributing

...

## References

* **Paper:** "Quantifying Fairness in Spatial Predictive Policing" (Include link or full citation to the paper when available).

## Contact

If you have questions, comments, or suggestions about this project or the paper, please contact:

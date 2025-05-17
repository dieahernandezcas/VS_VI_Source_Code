# An optimization model for the Violence Selective and Violence Indiscriminate in Colombia.

Source code for the analysis of Selective Violence (VS) and Indiscriminate Violence (VI) in Colombia.

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
    git clone [https://github.com/YOUR_USERNAME/VS_VI_Source_Code.git](https://github.com/YOUR_USERNAME/VS_VI_Source_Code.git)
    cd VS_VI_Source_Code
    ```
    *(Replace `YOUR_USERNAME` with your GitHub username or organization)*

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
    *(Note: You will need to create `requirements.txt` based on the libraries you use in your scripts, e.g., pandas, numpy, scikit-learn, etc.)*

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

## Metrics

The project defines and calculates the following key metrics:

* **Escalation:** Represents the change in the number of Cases or Victims compared to the count in the *immediately preceding month*.
    $$ \text{Escalation}_t = \text{Count}_t - \text{Count}_{t-1} $$
    *(Where $t$ is the current month and $t-1$ is the previous month)*

* **Intensity:** Compares the current count of Cases or Victims to the *weighted average* of the count over the *last 3 years*. The weighting could be uniform or favor more recent data, depending on implementation.
    $$ \text{Intensity}_t = \text{Count}_t - \text{WeightedAvg}(\text{Count}_{t-36 \dots t-1}) $$
    *(The exact weighting function for the average over the past 36 months (approx. 3 years) will be defined in the scripts).*

These metrics are calculated for both Cases and Victims at the Country, Department, and Region levels.

## Contributing

Contributions are welcome! Please feel free to open issues or submit pull requests.

## License

*(Optional: Add a license like MIT, Apache 2.0, etc. Here you would add a link to your LICENSE file.)*

## Contact

*(Optional: Add your contact information, e.g., email or GitHub profile link)*

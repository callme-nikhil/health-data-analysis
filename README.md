# Heart Disease Data Analysis & Preprocessing

This project performs **exploratory data analysis (EDA), data cleaning, categorical encoding, and numerical feature scaling** on a heart-disease dataset.

The work is implemented in the Jupyter notebook [`Heart.ipynb`](Heart.ipynb).

## Project Overview

The dataset contains demographic, clinical, exercise-related, and ECG-related attributes used to analyze the presence of heart disease.

### Dataset

- **File:** `heart.csv`
- **Rows:** 918
- **Columns:** 12
- **Target variable:** `HeartDisease`

| Column | Description |
|---|---|
| `Age` | Patient age |
| `Sex` | Patient sex (`M`/`F`) |
| `ChestPainType` | Type of chest pain |
| `RestingBP` | Resting blood pressure |
| `Cholesterol` | Cholesterol level |
| `FastingBS` | Fasting blood sugar indicator |
| `RestingECG` | Resting ECG result |
| `MaxHR` | Maximum heart rate achieved |
| `ExerciseAngina` | Exercise-induced angina indicator |
| `Oldpeak` | ST depression measurement |
| `ST_Slope` | Slope of the peak exercise ST segment |
| `HeartDisease` | Target indicator for heart disease |

## What the Notebook Does

### 1. Exploratory Data Analysis

The notebook investigates:

- Dataset columns and dimensions
- Data types and descriptive statistics
- Duplicate records
- Missing values
- Target-class distribution
- Numerical feature distributions
- Relationships between categorical variables and `HeartDisease`
- Cholesterol distributions by target class
- Age distributions by target class
- Correlations among numerical variables

### 2. Handling Zero Values

The notebook treats zero values in two clinical measurements as missing-like values:

- `Cholesterol == 0` values are replaced with the mean of non-zero cholesterol values.
- `RestingBP == 0` values are replaced with the mean of non-zero resting blood-pressure values.

The replacement values are rounded to two decimal places.

### 3. Additional Analysis

The notebook includes the `sheryanalysis` package for an automated dataset analysis report:

```python
import sheryanalysis as sh
sh.analyze(df)
```

The notebook also contains a package-installation cell for:

```bash
pip install sheryanalysis==0.1.0
```

### 4. Categorical Encoding

The cleaned dataset is transformed using Pandas one-hot encoding:

```python
pd.get_dummies(df, drop_first=True)
```

This converts categorical variables into numerical columns while dropping the first category from each categorical feature group.

### 5. Numerical Feature Scaling

`StandardScaler` is applied to:

- `Age`
- `RestingBP`
- `Cholesterol`
- `MaxHR`
- `Oldpeak`

The result is stored in `df_encode`.

> **Note:** The current notebook performs analysis and preprocessing; it does not train, evaluate, or save a machine-learning classification model.

## Technologies Used

- Python 3
- Jupyter Notebook
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- SciPy / related analysis dependencies
- `sheryanalysis==0.1.0`

## Installation

Install the core dependencies:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

For the automated analysis step used in the notebook:

```bash
pip install sheryanalysis==0.1.0
```

## How to Run

1. Clone or download the project.
2. Make sure `heart.csv` and `Heart.ipynb` are in the same directory.
3. Start Jupyter Notebook:

```bash
jupyter notebook
```

4. Open `Heart.ipynb`.
5. Run the cells from top to bottom.

## Project Structure

```text
.
├── heart.csv
├── Heart.ipynb
└── README_HEART.md
```

## Expected Outcome

After running the notebook, you will have:

- A descriptive overview of the heart-disease dataset
- Visual EDA of important clinical variables
- Zero-value handling for `Cholesterol` and `RestingBP`
- Encoded categorical features
- Standardized numerical features
- A preprocessed DataFrame (`df_encode`) suitable for a potential downstream classification workflow

## Important Notes

- The notebook modifies the in-memory DataFrame during preprocessing; the original CSV is not overwritten by the notebook.
- The `sheryanalysis` installation is written as a notebook cell. In some environments, installing packages from inside a notebook may require restarting the kernel afterward.
- The project does not currently include model training, test-set evaluation, hyperparameter tuning, or prediction output.

## Author / Project

This README documents the analysis contained in the supplied project notebook.

# 🛡️ Malware Infection Prediction

## 🔍 Overview
This project aims to **predict the probability of a system getting infected by various families of malware** using telemetry data collected by antivirus software. The data consists of machine-level attributes such as OS details, hardware configuration, antivirus versioning, and real-time protection status. This prediction task is framed as a **binary classification problem**, where the `target` variable indicates the presence (`1`) or absence (`0`) of malware infection on a given machine.

---

## 🗂️ Dataset Description

The dataset comprises three main CSV files:

- `train.csv` – Telemetry data for machines with the `target` malware label.
- `test.csv` – Same telemetry data without the `target` column.
- `sample_submission.csv` – Format template for final submission.

Each row corresponds to a unique machine identified by `MachineID`.

---

## 📁 File Columns

Sample of some important columns:

- `MachineID`: Unique Identifier
- `ProductName`, `EngineVersion`, `AppVersion`, `SignatureVersion`: Antivirus-related versions
- `IsBetaUser`, `RealTimeProtectionState`, `IsSystemProtected`: Security settings
- `OSVersion`, `OSBuildNumber`, `Processor`, `RAM`: System info
- `target`: Malware presence (1 = Yes, 0 = No)

The dataset includes dozens of additional columns with hardware, software, and region-specific data.

---

## 🧠 My Approach to the Malware Infection Prediction Challenge

This section outlines the end-to-end process I followed to tackle the malware prediction competition — from exploring the data to training machine learning models and evaluating their performance.

### 📌 Step 1: Data Cleaning & Preprocessing

- **Missing Value Treatment**:
  - Identified multiple placeholder values like `UNKNOWN`, `Unknown`, and `unknown` used to represent missing data.
  - Replaced these placeholders with `NaN` for consistent handling.
  - Used `SimpleImputer` with the strategy `"most_frequent"` to fill missing values for both categorical and numerical features.

- **Encoding Categorical Features**:
  - Identified all object-type columns using `select_dtypes`.
  - Applied `OrdinalEncoder` to transform categorical features into numerical format to make them compatible with Scikit-learn models.

### 📊 Step 2: Exploratory Data Analysis

- Conducted distribution analysis of the `target` column:
  - Approximately 50.5% of machines were malware-infected.
- Explored correlations among features and target.
- Assessed whether hardware specs (RAM, processor, etc.) and antivirus settings correlated with malware presence.

### 🧪 Step 3: Train-Test Split

Used `train_test_split` to divide the dataset into:
- 80% training data
- 20% test data
Ensured reproducibility with `random_state=42`.

###  🤖 Models Used & Performance

Below is a summary of the machine learning models used in this project along with their respective accuracy scores on the validation set:

| 🔢 Model                | ✅ Accuracy |
|------------------------|-------------|
| LGBMClassifier         | **0.62970** |
| XGBClassifier          | 0.62605     |
| Random Forest          | 0.61160     |
| Logistic Regression    | 0.59660     |
| K-Nearest Neighbors (KNN) | 0.55345  |

### 🔍 Observations:
- **LGBMClassifier** performed the best, likely due to its efficiency with large feature sets and handling of categorical variables.
- **XGBClassifier** followed closely, showing strong performance with boosted trees.
- **Random Forest** provided decent results, though less effective than boosting methods.
- **Logistic Regression** served as a useful baseline.
- **KNN** underperformed, likely due to the high dimensionality of the data and its sensitivity to irrelevant features.

Future improvements could focus on hyperparameter tuning and ensembling top-performing models.


# 🛡️ Malware Infection Prediction

## 🔍 Overview
This project aims to **predict the probability of a system getting infected by various families of malware** using telemetry data collected by antivirus software. The data consists of machine-level attributes such as OS details, hardware configuration, antivirus versioning, and real-time protection status. This prediction task is framed as a **binary classification problem**, where the target variable indicates the presence (`1`) or absence (`0`) of malware infection on a given machine.

---

## 🗂️ Dataset Description

The dataset comprises three main CSV files:

- `train.csv` – Contains telemetry data for machines along with the `target` label (1 = malware detected, 0 = no malware).
- `test.csv` – Contains the same telemetry data without the `target` column. You must predict the `target` for each row.
- `sample_submission.csv` – Provides the correct format for submitting predictions.

Each row corresponds to a unique machine identified by `MachineID`.

---

## 🧾 Columns Explained

Below is a breakdown of key columns in the dataset:

| Column Name | Description |
|-------------|-------------|
| `MachineID` | Unique identifier for each machine |
| `ProductName` | Name of the installed antivirus product |
| `EngineVersion`, `AppVersion`, `SignatureVersion` | Version information for the antivirus engine, application, and malware signatures |
| `IsBetaUser`, `IsPassiveModeEnabled`, `IsSystemProtected`, `AutoSampleSubmissionEnabled` | Antivirus usage preferences and protection states |
| `RealTimeProtectionState`, `FirewallEnabled`, `EnableLUA` | System security configurations |
| `CountryID`, `CityID`, `GeoRegionID` | Geographic information |
| `OSVersion`, `OSBuildNumber`, `OsPlatformSubRelease`, `SKUEditionName` | Operating system attributes |
| `Processor`, `ProcessorCoreCount`, `ProcessorManufacturerID` | Processor details |
| `PrimaryDiskCapacityMB`, `SystemVolumeCapacityMB`, `TotalPhysicalRAMMB` | Hardware specifications |
| `ChassisType`, `DeviceFamily`, `IsTouchEnabled`, `IsPenCapable`, `IsGamer` | Device form factor and user features |
| `FirmwareManufacturerID`, `FirmwareVersionID`, `IsSecureBootEnabled`, `IsVirtualDevice` | Firmware and virtualization status |
| `DateAS`, `DateOS` | Date of malware signature and last OS update |
| `target` | **Label column**: `1` if malware was detected, else `0` |

> ⚠️ Many categorical variables are encoded as numeric IDs. Feature decoding and engineering may be required for modeling.

---

## 🎯 Objective

Your task is to:

1. Analyze the provided telemetry features.
2. Build a machine learning model that predicts the likelihood of malware infection.
3. Generate a submission file predicting `target` for the test set in the following format:



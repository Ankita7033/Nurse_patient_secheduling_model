NURSE-PATIENT SCHEDULING MODEL

This project implements a machine learning-based model for scheduling nurses to patients, taking into account various factors such as patient priority, nurse availability, and required hours for each task. The goal is to optimize the allocation of nurses to patients efficiently, ensuring that the workload is distributed fairly among nurses while prioritizing urgent cases.

Features:
Data Preprocessing: Handles missing values, encodes categorical features, and processes numerical data.
Random Forest Classifier: Used to train a model on historical data for predicting the most suitable nurse for a patient.
Scheduling Optimization: Uses a priority-based approach to optimize nurse schedules based on patient needs and nurse availability.
Synthetic Data Generation: If no patient data exists for a given day, synthetic data is generated for the scheduling model.

Project Structure:
- nurse_patient_schedule.zip            # Contains the dataset and other necessary files for training the model.
- nurse_patient_schedule_model.py       # The main script for training the model and generating the schedule.
- README.md                            # This file.

Installation:
 1. Clone the repository:
  git clone https://github.com/Ankita7033/Nurse_patient_secheduling_model.git
 2. install required libraries:
  pip install pandas numpy scikit-learn

Usage:
 1. Data Preparation:
    Place your dataset (e.g., Final Dataset.xlsx) in the same directory as nurse_patient_schedule_model.py.
    The dataset should contain columns like blood_pressure, blood_sugar_levels, lifestyle_interventions, last_checkup_date, age, gender, chronic_disease, Department, Shift_Type, and Hours_Required.

  2. Running the Model:
    Run the script to train the model and generate schedules:
      python nurse_patient_schedule_model.py
     
  3. Input:
    The script will ask you to input a date (in the format DD-MM-YYYY) for which you want to generate a nurse-patient schedule.
    
  4. Output:
    The model will display the nurse assignments for each shift (day/night) and the nurse workload for the day.
    It will also handle missing data or generate synthetic data if no appointments are found for the requested date.

Model Description:
The model uses a Random Forest Classifier to predict the most suitable nurse for each patient based on the following features:
  age, gender, chronic_disease, Acuity_Level, Department, Shift_Type, Hours_Required, and a priority_score.

The priority score is calculated as follows:
priority_score = (Acuity_Level * 0.5) + (Hours_Required * 0.3) + (age / 100 * 0.2)

Example:
After training the model and inputting a date, the script will generate a schedule like this:
  Schedule for 22-04-2025:
=========================
Shift_1:
  Patient_1 -> Nurse_3
  Patient_2 -> Nurse_1
  Patient_3 -> Nurse_2

Shift_2:
  Patient_4 -> Nurse_4
  Patient_5 -> Nurse_5

Nurse Workload Summary:
-----------------------
Nurse_1: 8.0 hours
Nurse_2: 6.5 hours
Nurse_3: 7.5 hours
Nurse_4: 7.0 hours

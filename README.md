# PIMA Diabetes Prediction

## Project Overview
This project aims to develop a machine learning model to predict the likelihood of diabetes in patients based on various health-related attributes. Utilizing a Gradient Boosting Classifier, the objective is to provide an early diagnosis system that can identify high-risk individuals, enabling timely medical intervention and improved healthcare outcomes. The solution includes a complete MLOps pipeline, from data registration and preparation to model training, deployment, and continuous integration with GitHub Actions and Hugging Face Spaces.

## Business Context
A healthcare clinic seeks to enhance its decision-making process for predicting diabetes. The clinic has collected patient data, including metrics like plasma glucose concentration, blood pressure, BMI, and others. The challenge is to accurately identify high-risk patients who require further medical attention or lifestyle adjustments. This project leverages machine learning to address this need, ultimately improving patient care by facilitating early diagnosis and intervention.

## Objective
As a data scientist, your goal is to build a predictive model that classifies whether a patient is likely to have diabetes (class label 1) or not (class label 0). The core of this project involves developing a machine learning pipeline using a Gradient Boosting classifier. The final outcome will be a deployed model capable of real-time predictions for clinical use.

## Data Description
The dataset comprises health-related attributes for patients, with the following features:

*   **Pregnancies (preg):** Number of times the patient has been pregnant.
*   **Plasma glucose concentration (plas):** Plasma glucose concentration during an oral glucose tolerance test.
*   **Blood pressure (pres):** Diastolic blood pressure (mm Hg).
*   **Skin thickness (skin):** Triceps skin fold thickness (mm).
*   **Serum insulin (test):** 2-Hour serum insulin (mu U/ml).
*   **Body mass index (mass):** BMI (weight in kg/height in m²).
*   **Diabetes pedigree function (pedi):** A function that scores the likelihood of diabetes based on family history.
*   **Age (age):** Age of the patient (years).
*   **Class (class):** Diabetes outcome (1: diabetes, 0: no diabetes).

## Setup and Deployment

### Prerequisites
Before running the MLOps pipeline, ensure you have the following set up:

1.  **GitHub Repository:**
    *   Create a GitHub repository named `PIMA_Diabetes_Prediction`.
    *   Initialize it with a `README.md` file.

2.  **Hugging Face Space:**
    *   Create a Hugging Face Space named `PIMA-Diabetes-Prediction`.
    *   Select Docker as the Space SDK and Streamlit as the Docker template.
    *   **Note:** Use hyphens (`-`) instead of underscores (`_`) in the space name to avoid API access issues.

3.  **Hugging Face Access Token:**
    *   Generate a Hugging Face Access Token with `Write` permissions.
    *   Add this token as a GitHub Secret in your `PIMA_Diabetes_Prediction` repository, named `HF_TOKEN`.

### Project Structure

The project is organized into `self_paced_courses_1_mlops` directory:
self_paced_courses_1_mlops/ ├── data/ │ └── pima.csv ├── deployment/ │ ├── Dockerfile │ ├── app.py │ └── requirements.txt ├── hosting/ │ └── hosting.py ├── model_building/ │ ├── data_register.py │ ├── prep.py │ └── train.py └── requirements.txt

### Running the MLOps Pipeline

The MLOps pipeline is automated using GitHub Actions. The workflow is defined in `.github/workflows/pipeline.yml`.

1.  **Configure `pipeline.yml`:**
    *   Create the `.github/workflows/` directory in your GitHub repository.
    *   Create a file named `pipeline.yml` within this directory.
    *   Copy the provided YAML content (from the Colab notebook) into `pipeline.yml`.

2.  **Commit and Push:**
    *   Push all project files, including the `self_paced_courses_1_mlops` directory and the `.github/workflows/pipeline.yml` file, to your GitHub repository.
    *   Ensure your `HF_TOKEN` GitHub Secret is correctly configured.

3.  **Trigger Workflow:**
    *   The `workflow_dispatch` event allows you to manually trigger the workflow from the 'Actions' tab in your GitHub repository.

### Deployment to Hugging Face Space
The `deploy-hosting` job in the GitHub Actions workflow automatically pushes the Streamlit application and its dependencies to your designated Hugging Face Space. Once the workflow completes successfully, your application will be live at `https://huggingface.co/spaces/<your-username>/PIMA-Diabetes-Prediction`.

## How to Use the Deployed Application
Navigate to your Hugging Face Space URL. You will see a Streamlit application where you can input patient health metrics (Pregnancies, Plasma Glucose, Blood Pressure, etc.) and click 'Predict Diabetes' to get an instant prediction.


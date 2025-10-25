
## Overview
This repository demonstrates an **end-to-end workflow** for a machine learning project, including data ingestion, preprocessing, feature engineering, model training, evaluation, deployment, and monitoring. The project is structured for easy extension to new datasets and problems.

## How the Project Works

1. **Data Ingestion**: Raw data is imported, validated, and stored in a structured format.
2. **Data Preprocessing**: Handles missing values, encodes categorical variables, and scales numerical features.
3. **Feature Engineering**: Extracts and transforms relevant features to boost model performance.
4. **Model Training**: Multiple algorithms (e.g., CatBoost, etc.) are trained and tuned on the prepared dataset.
5. **Evaluation**: Compares models on relevant metrics (accuracy, F1, etc.) and logs results.
6. **Deployment**: The best model is packaged and can be deployed to services like AWS or Azure (see `.ebextensions` and `.github/workflows`).
7. **Monitoring**: Loggers and exception handlers are included for robust tracking and troubleshooting.

## Steps to Run

1. **Clone the repository**:
    ```
    git clone https://github.com/Sidhanth-2005/ML-deployment
    cd ML-deployment
    ```

2. **Install dependencies**:
    ```
    pip install -r requirements.txt
    ```

3. **Prepare data**:
    - Place your raw data in the `artifacts` folder
    - Update paths/configs in the relevant scripts under `src/components` and `src/pipeline`

4. **Run Notebooks for EDA**:
    - Check the `notebook` directory for example workflows

5. **Train the model**:
    ```
    python src/pipeline/train_pipeline.py
    ```

6. **Evaluate / Predict**:
    ```
    python src/pipeline/predict_pipeline.py
    ```

7. **Deploy**:
    - Use `app.py` to serve predictions via a web server (Flask/FastAPI)
    - See `.ebextensions` for AWS deployment configurations

## Problems Faced & How to Resolve Them

- **Data Quality Issues**: Raw datasets often have missing or inconsistent entries. Scripts in `src/components` detect and impute these, but still review logs for anomalies.
- **Model Overfitting/Underfitting**: Automated cross-validation and hyperparameter tuning (e.g., with CatBoost) help mitigate these, but re-examine feature engineering for best results.
- **Deployment Failures**: Cloud deployment scripts may fail due to platform-specific requirements—double-check configurations in `.ebextensions` or workflow .yml files and ensure all environment variables are set.
- **Dependency Errors**: All necessary packages are listed in `requirements.txt`. If you encounter an error, update the requirements or use a virtual environment.

## Uniqueness of the Project

- **Modular Structure**: The codebase is divided into reusable modules for ingestion, preprocessing, and model handling.
- **Cloud Native**: Ready for deployment on AWS and Azure using existing config and workflow files.
- **Comprehensive Logging & Exception Handling**: Custom logger (`src/logger.py`) and exception modules provide end-to-end traceability.
- **Easy Experiment Tracking**: Results and artifacts are stored in dedicated folders for reproducibility.
- **Extensible**: New algorithms/components can be added with minimal changes.


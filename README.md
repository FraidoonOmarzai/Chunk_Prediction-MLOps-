<h1 align=center> Chunk_Prediction(MLOps)</h1>

End-to-end MLOps project with Docker, Kubernetes, and AWS

# 🚀 DEVELOPMENT PHASES:

📊 What I'm Building: A production-ready, enterprise-grade MLOps platform with:

```
✅ Phase 1: ML Pipeline & Training
✅ Phase 2: API & Streamlit UI
✅ Phase 3: Docker Containers
✅ Phase 4: Testing Suite
✅ Phase 5: CI/CD 
✅ Phase 6: Kubernetes Deployment (AWS)
```

---

# 🎯 Business Problem

- Predict customer churn to enable proactive retention strategies, reducing customer attrition by 15% and improving customer lifetime value.

### Key Questions to Answer First:

#### 1. Business Problem & Use Case

What problem are we solving?

- Suggestion: Let's build a Customer Churn Prediction System (simple, practical, demonstrates full MLOps pipeline)

What's the impact?

- Business value: Reduce customer churn by 15%
- Target: Marketing team can proactively reach at-risk customers

#### 2. Data Questions

What data do we have?

- Customer demographics (age, location, tenure)
- Usage patterns (login frequency, feature usage)
- Transaction history (revenue, plan type)

Data size & freshness?

- For demo: Use Kaggle dataset (Telco Customer Churn)
- In production: Daily batch updates from database

#### 3. ML Model Requirements

What's good enough?

`Target Metrics:`

- Recall ≥ 80% (catch most churners)
- Precision ≥ 70% (avoid too many false alarms)
- F1-Score ≥ 0.75
- AUC-ROC ≥ 0.85

`Model type?`

- Start: Logistic Regression (baseline)
- Experiment: Random Forest, XGBoost, LightGBM

#### 4. System Requirements

- Latency: < 200ms for predictions (REST API)
- Throughput: Handle 100 requests/second
- Availability: 99.5% uptime

---

# 🛠️ Installation & Setup

### Prerequisites
- Python 3.10+
- pip
- Git

### 1. Clone the Repository
```bash
git clone https://github.com/FraidoonOmarzai/Chunk_Prediction-MLOps-.git
cd Chunk_Prediction-MLOps-
```

### 2. Create Virtual Environment
```bash
# Create virtual environment
conda create -p ./venv python=3.11 -y

# Activate virtual environment
conda activate C:\Users\44787\Desktop\Chunk_Prediction-MLOps-\venv

```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Create Directory Structure (Define template of the project)
```bash
touch template.py
python3 template.py

```

### 5. Define Logger and Custom Exception

---

# ML Pipeline (Phase 1)
```
✅ Data ingestion & validation
✅ Feature engineering
✅ Model training (4 algorithms)
✅ MLflow experiment tracking
✅ Model evaluation & selection
```

## 📥 Download Dataset

### Option 1: Automatic Download (Recommended)
```bash
python scripts/download_data.py
```

### Option 2: Manual Download
1. Visit: https://www.kaggle.com/datasets/blastchar/telco-customer-churn
2. Download the dataset
3. Save as: `data/raw/churn_data.csv`

### Option 3: Kaggle API
```bash
# Install Kaggle
pip install kaggle

# Set up credentials (~/.kaggle/kaggle.json)
# Then run:
python scripts/download_data.py
```

## Run Jupyter Notebook for Experiments 

### ✅ Typical Experiment Workflow

1. Prototype in Jupyter Notebook

- You explore ideas, try models, test functions, visualize results, etc.

- This is the “playground” phase.

2. Move Stable Code to Python Scripts (.py)

- Once your experiment code is working in the notebook, you usually move the clean, reusable parts into Python files.

1. **Components:**
   - `src/components/data_ingestion.py`
   - `src/components/data_validation.py`
   - `src/components/data_preprocessing.py`
   - `src/components/model_trainer.py`
   - `src/components/model_evaluation.py`

2. **Pipelines:**
   - `src/pipeline/training_pipeline.py`

3. **Utilities:**
   - `scripts/train.py`
```


3. Run Experiments From Scripts

- Running .py files is better for:

    - long training jobs
    - large experiments
    - automated logging
    - reproducibility

## 🎯 Run Training Pipeline

### Execute Complete Pipeline
```bash
python scripts/train.py
```


### What Happens:
1. **Data Ingestion**: Loads and splits data (80/20)
2. **Data Validation**: Checks schema and quality
3. **Data Preprocessing**: Cleans and transforms features
4. **Model Training**: Trains 4 models with MLflow tracking
5. **Model Evaluation**: Compares models and selects best

### Expected Output:
```
======================================================================
TRAINING PIPELINE COMPLETED SUCCESSFULLY!
======================================================================

Best Model: xgboost
Models trained: 4
Preprocessor saved at: artifacts/preprocessors/preprocessor.pkl

Check MLflow UI for detailed experiment tracking:
  Run: mlflow ui
  Open: http://localhost:5000
======================================================================
```

## 📊 View Experiments with MLflow

### Start MLflow UI
```bash
mlflow ui
```

### Access Dashboard
Open browser: http://localhost:5000

### What You'll See:
- All experiment runs
- Parameters for each model
- Metrics (accuracy, precision, recall, F1, ROC-AUC)
- Model artifacts
- Comparison charts

## 📈 Evaluation Metrics

### Model Performance Targets
- **Recall**: ≥ 80% (catch most churners)
- **Precision**: ≥ 70% (avoid false alarms)
- **F1-Score**: ≥ 0.75
- **ROC-AUC**: ≥ 0.85

### Metrics Calculated
- Accuracy
- Precision, Recall, F1-Score
- ROC-AUC
- Confusion Matrix
- Specificity, Sensitivity
- Classification Report

### View Results
```bash
# Check evaluation report
cat artifacts/metrics/evaluation_report.json

# Check validation report
cat artifacts/validation_report.json
```

## 🔧 Configuration

### Main Configuration (`config/config.yaml`)
- Data paths
- Train/test split ratio
- Feature lists
- Artifact locations
- MLflow settings

### Model Configuration (`config/model_config.yaml`)
- Hyperparameters for each model
- Algorithm-specific settings
- Training parameters

## 📝 Logs

### Log Files
Logs are saved in: `logs/`

### Log Format
```
[2024-11-04 10:30:45] INFO - ChurnPrediction - Starting training pipeline
[2024-11-04 10:30:46] INFO - ChurnPrediction - Data loaded: (7043, 21)
```

## 🧪 Generated Artifacts

### After Training:
```
artifacts/
├── models/
│   ├── logistic_regression.pkl
│   ├── random_forest.pkl
│   ├── xgboost.pkl
│   └── lightgbm.pkl
├── preprocessors/
│   ├── preprocessor.pkl
│   └── preprocessor_label_encoder.pkl
├── metrics/
│   └── evaluation_report.json
└── validation_report.json
```

## 🎓 Model Training Details

### Models Trained:
1. **Logistic Regression** (Baseline)
2. **Random Forest** (Ensemble)
3. **XGBoost** (Gradient Boosting)
4. **LightGBM** (Fast Gradient Boosting)

### Training Process:
- Stratified train/test split (80/20)
- Standard scaling for numerical features
- One-hot encoding for categorical features
- Automated hyperparameter configuration
- MLflow tracking for all experiments

<!-- 



## API & UI (Phase 2)

✅ FastAPI REST API
✅ Streamlit dashboard
✅ Real-time predictions
✅ Batch processing

## Containerization (Phase 3)

✅ Docker images (API, Streamlit, Training)
✅ Docker Compose orchestration
✅ Multi-stage builds
✅ Pushed to Docker Hub

## Testing (Phase 4)

✅ Unit tests (70%+ coverage)
✅ Integration tests
✅ Data quality tests
✅ Model performance tests
✅ Automated test suite



## CI/CD (Phase 5)

✅ GitHub Actions workflows
✅ Automated testing
✅ Docker builds & pushes
✅ Security scanning
✅ Code quality checks
✅ Deployment automation

## Cloud Deployment (Phase 6)

✅ AWS EKS cluster
✅ Kubernetes orchestration
✅ Auto-scaling (HPA)
✅ Load balancing
✅ Monitoring & logging
✅ High availability -->

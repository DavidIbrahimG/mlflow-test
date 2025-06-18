# 🍷 Wine Quality Regression with MLflow and DagsHub

This project demonstrates a full machine learning workflow for predicting wine quality using **ElasticNet regression**, **MLflow** for experiment tracking, and **DagsHub** for remote collaboration and version control.

It fetches the [Wine Quality dataset](https://archive.ics.uci.edu/ml/datasets/Wine+Quality), trains an ElasticNet regression model, evaluates its performance, logs all relevant parameters and metrics using MLflow, and (optionally) registers the model remotely to **DagsHub's MLflow server**.

---

## 🚀 Project Goals

- Build a regression model to predict wine quality.
- Log all experiments (hyperparameters, metrics, model) using MLflow.
- Push experiment data and artifacts to DagsHub via remote tracking URI.
- Optionally register the trained model.

---

## 🧱 Project Structure

```
.
├── train.py               # Main script that trains, evaluates, and logs the model
├── requirements.txt       # Project dependencies
├── README.md              # Project documentation
```

---

## 🔧 Technologies Used

- **Python**
- **scikit-learn** (ElasticNet regression)
- **pandas & numpy**
- **MLflow** (experiment tracking & model logging)
- **DagsHub** (remote MLflow server and Git+DVC platform)

---

## ⚙️ How the Pipeline Works

1. **Import Dependencies**  
   Essential libraries for regression, metrics, and logging.

2. **Read Dataset**  
   Downloads the red wine quality dataset from the MLflow GitHub repo.

3. **Data Preparation**  
   - Splits data into training and testing sets.
   - Separates features and target (`quality`).

4. **Parameter Handling**  
   Accepts `alpha` and `l1_ratio` as command-line arguments (or defaults to 0.5).

5. **Model Training & Evaluation**  
   - Fits an ElasticNet model.
   - Computes RMSE, MAE, and R².

6. **Experiment Logging with MLflow**  
   - Logs hyperparameters, metrics, and the model itself.
   - If connected to a remote server (DagsHub), registers the model in the MLflow registry.

---

## 🧪 Example Output

```
Elasticnet model (alpha=0.500000, l1_ratio=0.500000):
  RMSE: 0.729
  MAE: 0.57
  R2: 0.31
```

---

## 📦 Installation

```bash
# Create and activate virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows

# Install dependencies
pip install -r requirements.txt
```

---

## 🏃 How to Run the Script

```bash
# With default parameters
python train.py

# With custom alpha and l1_ratio
python train.py 0.8 0.3
```

---

## 🌐 Connect to DagsHub (MLflow Remote Logging)

DagsHub automatically exposes an MLflow server. To enable remote logging:

1. Install the DagsHub Python client:
   ```bash
   pip install dagshub
   ```

2. Add this line before the MLflow run block:
   ```python
   dagshub.init(repo_owner='DavidIbrahimG', repo_name='mlflow-test', mlflow=True)
   ```

3. Set the MLflow remote tracking URI:
   ```python
   mlflow.set_tracking_uri("https://dagshub.com/DavidIbrahimG/mlflow-test.mlflow")
   ```

4. Use `mlflow ui` to run a local MLflow dashboard, or view experiments on [https://dagshub.com/DavidIbrahimG/mlflow-test](https://dagshub.com/DavidIbrahimG/mlflow-test).

---

## ✅ Features Implemented

- ElasticNet model training and evaluation
- RMSE, MAE, and R² metric logging
- Parameter logging (alpha, l1_ratio)
- Model artifact logging
- Remote MLflow experiment tracking on DagsHub
- Optional model registration

---

## 📌 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 🙋‍♂️ Author

**David Ibrahim G.**  
GitHub: [@DavidIbrahimG](https://github.com/DavidIbrahimG)

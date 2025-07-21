# Framingham CVD Risk Prediction API

This project is a RESTful web service that serves a trained logistic regression model to predict a patient's 10-year risk of cardiovascular disease (CVD), using data from the Framingham Heart Study. It demonstrates how machine learning models can be deployed through simple, accessible APIs to enable real-time risk analysis.

## 🔍 Project Highlights

- Trained a logistic regression model using the Framingham Heart Study dataset
- Built a Flask-based REST API with endpoints to evaluate risk, explain input requirements, and provide sample data
- Created a Python client script to consume and test the API
- Designed for practical deployment and ease of integration with other health-related applications

---

## 🧠 Model Overview

- **Type**: Logistic Regression
- **Target Variable**: `TenYearCHD` – indicates whether a patient develops coronary heart disease within 10 years
- **Framework**: Python (Flask, scikit-learn)
- **Dataset Source**: Framingham Heart Study (open dataset)

---

## 📂 Project Structure

├── app.py # Main Flask app with REST endpoints
├── model.pkl # Trained logistic regression model (pickled)
├── consumer.py # Client script to test all API endpoints
├── requirements.txt # Python package dependencies
└── README.md # Project documentation


---

## 🌐 API Endpoints

### `GET /cvd/sample`
Returns a sample JSON object with valid input features for prediction.

json
{
  "age": 55,
  "male": 1,
  "education": 4,
  "currentSmoker": 0,
  "cigsPerDay": 0,
  "BPMeds": 0,
  "prevalentStroke": 0,
  "prevalentHyp": 1,
  "diabetes": 0,
  "totChol": 210,
  "sysBP": 130,
  "diaBP": 80,
  "BMI": 25.5,
  "heartRate": 75,
  "glucose": 85
}

GET /cvd/explain
Returns a description of each expected field and its acceptable format or value.

Example Output:

- 'male': 1 = male, 0 = female
- 'currentSmoker': 1 = yes, 0 = no
- 'BPMeds': 1 = on blood pressure medication, 0 = not on it
- 'prevalentStroke': 1 = had a stroke, 0 = no stroke history
- 'education': Integer from 1 to 4
...

POST /cvd/evaluate
Takes in a JSON object (same format as /cvd/sample) and returns:

"1" → Patient is at risk of cardiovascular disease in 10 years

"0" → Patient is not at risk

Example request:

POST /cvd/evaluate
Content-Type: application/json

{
  "age": 60,
  "male": 0,
  "education": 3,
  "currentSmoker": 1,
  "cigsPerDay": 10,
  "BPMeds": 1,
  "prevalentStroke": 0,
  "prevalentHyp": 1,
  "diabetes": 0,
  "totChol": 250,
  "sysBP": 145,
  "diaBP": 95,
  "BMI": 30,
  "heartRate": 85,
  "glucose": 100
}

---

## 📊 Use Cases

- Educational demo for ML deployment
- Backend API for health-tech tools
- Prototype for integrating cardiovascular risk screening in digital health apps

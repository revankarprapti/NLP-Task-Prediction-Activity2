# Automatic Task Prediction Using NLP and Machine Learning

A full-stack academic project that predicts the category of customer-support tickets using Natural Language Processing (NLP) and Machine Learning. The application includes a React frontend, FastAPI backend, and three classification algorithms:

- Logistic Regression
- Linear Support Vector Machine (Linear SVM)
- Recurrent Neural Network (RNN)

The system is developed as an academic prototype for automated customer-support ticket categorisation.

---

## Table of Contents

1. Project Overview
2. Key Features
3. Algorithms Used
4. Technology Stack
5. Dataset Description
6. Model Performance
7. Project Structure
8. Installation and Setup
9. Running the Application
10. API Endpoints
11. Testing
12. Team Members
13. Limitations and Future Scope

---

## 1. Project Overview

Customer-support teams receive numerous tickets containing questions, complaints, refund requests, cancellation requests, and technical issues.

Manually categorising these tickets can be time-consuming. This project implements an NLP-based classification system that analyses customer-support ticket descriptions and automatically predicts their categories.

The system classifies tickets into five categories:

1. Billing Inquiry
2. Cancellation Request
3. Product Inquiry
4. Refund Request
5. Technical Issue

The application provides an interactive dashboard for exploring the dataset, comparing machine learning models, predicting ticket categories, and viewing prediction history.

---

## 2. Key Features

- Customer-support ticket dataset analysis.
- Text preprocessing and feature extraction.
- Implementation of three classification algorithms.
- Logistic Regression and Linear SVM comparison.
- RNN-based sequential text classification.
- Real-time ticket category prediction.
- Model evaluation using accuracy, precision, recall, and F1-score.
- Confusion matrix visualisations.
- Interactive React dashboard.
- FastAPI backend integration.
- Prediction history and CSV export functionality.

---

## 3. Algorithms Used

### 3.1 Logistic Regression

Logistic Regression is a supervised machine learning algorithm used for classification.

In this project, TF-IDF vectorisation converts the cleaned ticket descriptions into numerical features. Logistic Regression uses these features to predict the appropriate ticket category.

### 3.2 Linear Support Vector Machine (SVM)

Linear SVM is a supervised classification algorithm that identifies an optimal decision boundary between different classes.

It uses TF-IDF features extracted from customer-support ticket descriptions to classify tickets into the five predefined categories.

### 3.3 Recurrent Neural Network (RNN)

A Recurrent Neural Network is a deep learning algorithm designed to process sequential data.

In this project, the RNN processes customer-support ticket descriptions as sequences of tokens.

The architecture includes:

- Tokenisation
- Embedding Layer
- Recurrent Layer
- Dropout Layer
- Fully Connected Output Layer

The RNN learns sequential patterns from ticket descriptions and predicts the corresponding ticket category.

The implementation uses PyTorch for model development and training.

---

## 4. Technology Stack

| Component | Technologies |
|---|---|
| Frontend | React.js, TypeScript, Vite |
| Styling | Tailwind CSS |
| Backend | Python, FastAPI |
| Machine Learning | Scikit-learn, PyTorch |
| NLP | TF-IDF, Tokenisation, Word Embeddings |
| Data Processing | Pandas, NumPy |
| Visualisation | Recharts, Matplotlib |
| Database / Storage | CSV, JSON, Model Artifacts |
| Development Tools | VS Code, Git, GitHub |

---

## 5. Dataset Description

The project uses a Customer Support Ticket Dataset containing customer queries and their corresponding categories.

**Dataset details:**

- Total records: 8,469
- Total columns: 17
- Number of target categories: 5
- Training split: 80%
- Testing split: 20%
- Random state: 42

The dataset is divided into training and testing sets using stratified sampling to maintain the distribution of categories.

### Text Preprocessing

The following preprocessing operations are performed:

1. Convert text into lowercase.
2. Remove email addresses.
3. Remove URLs.
4. Replace product placeholders.
5. Remove unnecessary numeric characters and punctuation.
6. Remove extra whitespace.
7. Tokenise the cleaned text for RNN processing.

For Logistic Regression and Linear SVM, TF-IDF vectorisation is used.

For RNN, tokenisation and integer sequence encoding are performed before passing the sequences to the embedding layer.

---

## 6. Model Performance

The three algorithms are evaluated using the same held-out test dataset.

### Performance Comparison

| Evaluation Metric | Logistic Regression | Linear SVM | RNN |
|---|---:|---:|---:|
| Accuracy | 21.49% | 21.07% | 20.31% |
| Precision | 21.51% | 21.09% | 20.84% |
| Recall | 21.49% | 21.07% | 20.31% |
| F1-Score | 21.49% | 21.07% | 19.27% |

### Result Analysis

- Logistic Regression achieved the highest accuracy and F1-score.
- Linear SVM performed slightly below Logistic Regression.
- RNN was implemented to evaluate sequential learning capabilities.
- RNN performance was lower than the two traditional machine learning algorithms in the current experiment.

Logistic Regression is the best-performing model based on the recorded weighted F1-score.

**Note:** The model scores are close to the approximate 20% random-guess reference for five classes. Therefore, the models should be considered experimental and should not be used for fully automated ticket routing without further improvement.

---

## 7. Project Structure

```text
NLP LAB/
│
├── backend/
│   ├── app/
│   │   ├── routers/
│   │   ├── services/
│   │   ├── config.py
│   │   ├── main.py
│   │   └── schemas.py
│   │
│   ├── tests/
│   ├── requirements.txt
│   └── .env.example
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── context/
│   │   ├── lib/
│   │   └── pages/
│   │
│   ├── package.json
│   └── .env.example
│
├── ml/
│   ├── artifacts/
│   ├── preprocessing.py
│   ├── rnn_model.py
│   ├── train.py
│   ├── train_rnn.py
│   └── reference_notebook.ipynb
│
├── data/
│   ├── Customer Support Ticket Dataset.csv
│   └── prediction_history.csv
│
├── RNN_IMPLEMENTATION_GUIDE.md
└── README.md
```

---

## 8. Installation and Setup

### Prerequisites

Install the following software:

- Python 3.11 or later
- Node.js 18 or later
- npm
- Git
- Visual Studio Code

### Step 1: Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/NLP-Task-Prediction-RNN.git
```

Navigate to the project directory:

```bash
cd NLP-Task-Prediction-RNN
```

Replace `YOUR-USERNAME` with your GitHub username and use your actual repository URL.

### Step 2: Create a Virtual Environment

```bash
python -m venv .venv
```

Activate the environment.

**Windows Command Prompt:**

```cmd
.venv\Scripts\activate
```

**Windows PowerShell:**

```powershell
.\.venv\Scripts\Activate.ps1
```

### Step 3: Install Backend Dependencies

From the main project directory:

```bash
python -m pip install -r backend/requirements.txt
```

### Step 4: Install Frontend Dependencies

```bash
cd frontend
npm install
```

---

## 9. Running the Application

The frontend and backend must run simultaneously in two separate terminals.

### Terminal 1: Start the Backend

Navigate to the backend directory:

```bash
cd backend
```

Start the FastAPI server:

```bash
python -m uvicorn app.main:app --reload --host 127.0.0.1 --port 8000
```

Backend URL:

```text
http://127.0.0.1:8000
```

API documentation:

```text
http://127.0.0.1:8000/docs
```

### Terminal 2: Start the Frontend

Navigate to the frontend directory:

```bash
cd frontend
```

Start the React development server:

```bash
npm run dev
```

Open the application in your browser:

```text
http://localhost:5173
```

**Important:** Keep both terminals running while using the application.

### Training the Models

The project includes saved model artifacts.

To retrain the models, run the following commands from the project root after activating the virtual environment:

```bash
python ml/train.py
```

```bash
python ml/train_rnn.py
```

Restart the backend after retraining.

---

## 10. API Endpoints

The FastAPI backend provides endpoints for dataset access, model comparison, prediction, and prediction history.

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/health` | Check API status |
| GET | `/api/dashboard/stats` | Retrieve dashboard statistics |
| GET | `/api/dataset` | Retrieve dataset information |
| GET | `/api/models/comparison` | Compare model performance |
| POST | `/api/predict` | Predict ticket category |
| GET | `/api/predictions/history` | Retrieve prediction history |
| GET | `/api/predictions/export` | Export prediction history |
| DELETE | `/api/predictions/history` | Clear prediction history |

For complete API information, visit:

```text
http://127.0.0.1:8000/docs
```

---

## 11. Testing

### Backend Testing

Run the following command from the project root:

```bash
python -m pytest backend/tests -v
```

### Frontend Build Testing

Navigate to the frontend directory:

```bash
cd frontend
```

Run:

```bash
npm run build
```

This checks the frontend production build.

---

## 13. Limitations and Future Scope

### Limitations

- The current classification accuracy is relatively low.
- Some ticket descriptions contain overlapping vocabulary.
- The models may struggle with ambiguous customer queries.
- The current RNN configuration requires further optimisation.

### Future Scope

- Implement LSTM and GRU architectures.
- Experiment with Bidirectional RNN.
- Integrate pretrained transformer models such as BERT.
- Improve dataset quality and category distribution.
- Perform hyperparameter tuning.
- Improve model accuracy through additional feature engineering.
- Introduce confidence-based predictions and human verification.

---

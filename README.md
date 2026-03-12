# Binary Classification Web App (Mushroom Classifier)

### Live App: https://binary-classification-webapp.streamlit.app

An interactive **Machine Learning web application** built with **Streamlit** that predicts whether a mushroom is **edible** or **poisonous** using multiple classification algorithms.

The app allows users to:
- Select different **machine learning classifiers**
- Adjust **model hyperparameters**
- Train models interactively
- Evaluate performance using multiple **visual metrics**

The application demonstrates how machine learning models can be deployed through a simple and intuitive web interface without requiring users to write any code.

## Project Overview

This project implements a **binary classification system** using the **Mushroom dataset**. The application trains different machine learning models and provides an interface where users can experiment with various algorithms and hyperparameters.

The workflow includes: 
1. Loading and preprocessing the dataset
2. Encoding categorical features
3. Splitting data into training and testing sets
4. Training different classification models
5. Evaluating models using multiple performance metrics
6. Visualizing model performance

All interactions are handled through a **Streamlit UI sidebar**, allowing users to control model behavior dynamically.

## Features
### Interactive Model Selection:
Users can choose from three different machine learning algorithms:
- Support Vector Machine (SVM)
- Logistic Regression
- Random Forest

### Hyperparameter Tuning:
The app allows users to tune important parameters for each algorithm.

**SVM Parameters:**
- `C` – Regularization parameter
- `Kernel` – Linear or RBF kernel
- `Gamma` – Kernel coefficient

**Logistic Regression Parameters:**
- `C` – Regularization strength
- `max_iter` – Maximum number of training iterations

**Random Forest Parameters:**
- `n_estimators` – Number of trees
- `max_depth` – Maximum depth of trees
- `bootstrap` – Bootstrap sampling toggle

### Model Evaluation Metrics:

Users can visualize different evaluation metrics after training a model:
- Confusion Matrix
- ROC Curve
- Precision-Recall Curve

The app also displays:
- Accuracy
- Precision
- Recall

### Dataset Visualization:
Users can optionally view the raw encoded dataset directly inside the application.

## Example Workflow
1. Select a classifier from the sidebar.
2. Adjust the hyperparameters.
3. Select the evaluation metrics to display.
4. Click **Classify** to train the model.
5. View performance metrics and plots.

## Dataset

This project uses the **Mushroom Dataset** from the UCI Machine Learning Repository.

### Dataset Source: https://archive.ics.uci.edu/dataset/73/mushroom

The dataset contains descriptions of hypothetical samples corresponding to **23 species of gilled mushrooms**.

Each sample is labeled as:
- **Edible**
- **Poisonous**

All features in the dataset are **categorical**, describing properties such as:
- Cap shape
- Cap color
- Odor
- Gill size
- Habitat
- Spore print color

## Data Preprocessing

Before training the models, the dataset undergoes preprocessing steps:

### 1. Loading the Dataset

The dataset is loaded using **Pandas** from the CSV file.
```
pd.read_csv('dataset/mushrooms.csv')
```
### 2. Label Encoding

Since all features are categorical, they are converted into numeric values using **LabelEncoder**. Each column is encoded separately.

### 3. Train-Test Split

The dataset is split into:
- **70% training data**
- **30% testing data**

Using:
```
train_test_split(test_size=0.3, random_state=0)
```
This ensures reproducibility.

## Machine Learning Models

The app supports three classifiers implemented with **Scikit-learn**.

### Support Vector Machine (SVM):

A powerful supervised learning algorithm used for classification tasks.

The implementation allows configuration of:
- Regularization parameter (`C`)
- Kernel type (`linear`, `rbf`)
- Kernel coefficient (`gamma`)

Model used:
```
sklearn.svm.SVC
```

### Logistic Regression:

A linear model commonly used for binary classification.

Configurable parameters:
- Regularization strength (`C`)
- Maximum training iterations (`max_iter`)

Model used:
```
sklearn.linear_model.LogisticRegression
```

### Random Forest:

An ensemble learning method that builds multiple decision trees and combines their predictions.

Configurable parameters:
- Number of trees (`n_estimators`)
- Maximum tree depth (`max_depth`)
- Bootstrap sampling (`bootstrap`)

Model used:
```
sklearn.ensemble.RandomForestClassifier
```

## Evaluation Metrics

The application evaluates model performance using several metrics.

### Accuracy:
Measures the percentage of correctly classified samples.
```
Accuracy = Correct Predictions / Total Predictions = (TP + TN) / (TP + TN + FP + FN)
```

### Precision:
Measures how many predicted positives are actually positive.
```
Precision = True Positives / Predicted Positives = TP / (TP + FP)
```

### Recall:
Measures how many actual positives are correctly predicted.
```
Recall = True Positives / Actual Positives = TP / (TP + FN)
```

### Confusion Matrix:
Displays counts of:
- True Positives (TP)
- False Positives (FP)
- True Negatives (TN)
- False Negatives (FN)

Implemented using:
```
ConfusionMatrixDisplay
```

### ROC Curve:
The Receiver Operating Characteristic curve shows the trade-off between:
- True Positive Rate
- False Positive Rate

Implemented using:
```
RocCurveDisplay
```

### Precision-Recall Curve:
Visualizes the balance between precision and recall.

Implemented using:
```
PrecisionRecallDisplay
```

## Application Interface

The app UI is divided into two main sections.

### Main Page
Displays:
- Application title
- Model results
- Evaluation plots
- Dataset preview (optional)

### Sidebar
Controls the application:
- Classifier selection
- Hyperparameter tuning
- Metric selection
- Run model button
- Show dataset toggle

## Project Structure
```
Binary-Classification-Web-App
├── app.py
├── dataset
│   └── mushrooms.csv
├── requirements.txt
└── README.md
```

## Tech Stack

- Python
- Streamlit
- Scikit-learn
- Pandas
- NumPy
- Matplotlib

## Running the Project Locally
**1.** Clone the repository.
```
git clone https://github.com/Avik-Das-567/Binary-Classification-Web-App.git
```
**2.** Navigate to the project directory.
```
cd Binary-Classification-Web-App
```
**3.** Install dependencies.
```
pip install -r requirements.txt
```
**4.** Run the Streamlit application.
```
streamlit run app.py
```
**5.** Open in browser.

Streamlit will automatically launch the app at:
```
http://localhost:8501
```

## Key Implementation Details
### Data Caching:

To improve performance, the app caches dataset loading and preprocessing using Streamlit’s caching decorator.
```
@st.cache_data(persist=True)
```
This prevents reloading and reprocessing the dataset every time the UI updates.

### Dynamic Model Training:

Models are trained **only when the user clicks the "Classify" button**, allowing users to experiment with parameters without retraining unnecessarily.

### Dynamic Metric Visualization:

Users can select which evaluation metrics to display. The application dynamically generates the corresponding plots.

---

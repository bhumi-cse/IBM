Network Intrusion Detection System (NIDS) using Machine Learning
​Executive Summary
​The Network Intrusion Detection System (NIDS) is an advanced machine learning framework developed to identify, classify, and mitigate cyber threats across enterprise network architectures. As modern network security environments evolve, traditional rule-based and signature-matching detection techniques often fall short against sophisticated, zero-day attacks and dynamic payload variations.
​This project implements an automated, high-precision intrusion detection engine using Python and Scikit-learn. By leveraging data preprocessing techniques, dynamic feature normalization (StandardScaler), categorical label encoding, and ensemble decision trees (RandomForestClassifier), the system analyzes high-throughput network traffic logs to separate legitimate connections from malicious intrusions with minimal false-positive rates.
​Key System Features
​End-to-End Data Pipeline: Streamlined pipeline for reading raw network connection logs, cleaning missing values, and formatting inputs for model ingestion.
​Categorical Feature Encoding: Automated translation of string-based protocol properties (e.g., TCP, UDP, ICMP), service flags, and connection statuses into numerical representations via LabelEncoder.
​Feature Scaling & Standardization: Implementation of StandardScaler to transform numeric attributes to a uniform scale (\mu = 0, \sigma = 1), improving convergence and stability across multi-dimensional feature spaces.
​Ensemble Machine Learning Architecture: Uses an ensemble of decision trees (RandomForestClassifier) configured with multi-threading optimization (n_estimators=100) to yield high stability and resistance to dataset noise and overfitting.
​Multi-Metric Evaluation: Comprehensive performance diagnosis featuring Precision, Recall, F1-Score, micro/macro averages, and graphical Confusion Matrix visualization via Seaborn/Matplotlib.
​Technical Stack & Dependencies
​Programming Language & Runtime
​Language: Python 3.8+
​Environment: Google Colab / Jupyter Notebook / Local Python Virtual Environments (venv, conda)
​Core Machine Learning & Scientific Computing Stack
​pandas: Advanced dataframe manipulation, data cleaning, and tabular network log parsing.
​numpy: Fast multi-dimensional array operations, mathematical transformations, and linear algebra computing.
​scikit-learn: Production-grade implementations of StandardScaler, LabelEncoder, RandomForestClassifier, and metrics validation suites (accuracy_score, confusion_matrix, classification_report).
​matplotlib: Low-level graphical plotting engine for rendering multi-class distributions and matrix figures.
​seaborn: Advanced statistical data visualization built on Matplotlib, used for formatted heatmap renderings.

​Project Directory & Architecture

├── Bhumi_NetworkIntrusionDetector1.ipynb     # Main Jupyter Notebook containing model pipeline & code
├── requirements.txt                         # Project dependency manifest with version constraints
├── README.md                                # Detailed technical documentation and setup guide
└── Bhumi_ProjectReport.docx                 # Complete project documentation report

Detailed Data Processing & Machine Learning Workflow
+--------------------------+
|   Raw Network Logs       |
+--------------------------+
             |
             v
+--------------------------+
|   Categorical Encoding   | --> (LabelEncoder for Protocol, Service, State)
+--------------------------+
             |
             v
+--------------------------+
|    Feature Scaling       | --> (StandardScaler for numerical standardization)
+--------------------------+
             |
             v
+--------------------------+
|  Train / Test Splitting  | --> (80% Training Data, 20% Holdout Testing)
+--------------------------+
             |
             v
+--------------------------+
| Random Forest Classifier | --> (Ensemble Training with 100 Estimators)
+--------------------------+
             |
             v
+--------------------------+
| Evaluation & Reporting   | --> (Accuracy, Precision, Recall, F1-Score, Confusion Matrix)
+--------------------------+

1. Data Cleaning & Encoding
​Network logs contain categorical features representing network layer protocols and connection flags. The LabelEncoder class processes these columns to map each unique string label to a zero-indexed integer:

f(x_i) \to \{0, 1, 2, \dots, K-1\}

2. Feature Standardization
​Variance across numerical features (such as byte throughput, connection duration, and error packet counts) can bias machine learning estimators. Applying StandardScaler scales attributes independently:

z = \frac{x - \mu}{\sigma}

where \mu is the mean and \sigma is the standard deviation of the training dataset.

​3. Model Architecture
​The primary classifier utilizes Random Forest, an ensemble learning method that constructs a multitude of decision trees during training and outputs the mode of the classes predicted by individual trees:

H(x) = \text{mode}\{h_1(x), h_2(x), \dots, h_T(x)\}

Setup & Local Installation Guide
​Prerequisites
​Ensure Python 3.8 or higher is installed on your operating system. You can verify your local installation by running:
python --version
Step 1: Clone or Extract Project Files
​Download or extract the project directory to your local file system:
cd /path/to/project-directory

Step 2: Create a Virtual Environment (Optional but Recommended)
​Creating an isolated virtual environment prevents dependency conflicts with global packages:
# On Linux/macOS:
python -m venv venv
source venv/bin/activate

# On Windows (Command Prompt):
python -m venv venv
venv\Scripts\activate

Step 3: Install Required Dependencies
​Install all required libraries using the included requirements.txt manifest:
pip install -r requirements.txt
Execution Instructions
​Running via Google Colab (Cloud Instance)
​Navigate to Google Colab.
​Select File > Upload notebook.
​Choose Bhumi_NetworkIntrusionDetector1.ipynb from your local machine.
​Go to Runtime > Run all (or press Ctrl + F9) to execute all cells sequentially.
​Running via Local Jupyter Notebook

Start the local Jupyter server:
jupyter notebook

In the browser dashboard, open Bhumi_NetworkIntrusionDetector1.ipynb.

3. Select Kernel > Restart & Run All to verify
end-to-end execution.

Performance Evaluation & Results Analysis

The machine learning model is evaluated across multiple criteria to ensure robust detection capability:

1. Accuracy: Measures the ratio of total correct predictions over all evaluation traffic instances.

2. Precision: Measures the proportion of correctly identified intrusive packets relative to all packets flagged as anomalies: TP Precision TP+ FP

3. Recall (Sensitivity): Measures the ability of the system to correctly identify actual

<ntrusions out of all true intrusion attempts:

TP Recall = TP+FN

4. F1-Score: Harmonic mean of Precision and Recall, balancing false alarms against undetected breaches:

Precision Recall F1-Score 2. Precision + Recall

Confusion Matrix Insights

The confusion matrix plot illustrates overall system accuracy:

True Negatives (TN): Legitimate traffic correctly recognized as Normal.

False Positives (FP): Legitimate traffic incorrectly flagged as an Anomaly (False Alarm).

Ο False Negatives (FN): Malicious traffic that bypassed detection (Missed Breach).

True Positives (TP): Malicious traffic correctly flagged as an Anomaly.

Future Enhancements & Deployment Roadmap

Real-Time Packet Inspection: Integration with live packet capture engines like Scapy or PyShark for real-time interface monitoring.

Deep Learning Architectures:

Implementation of Convolutional Neural Networks (CNN) or Long Short-Term Memory (LSTM) networks for temporal sequence analysis of packet streams.

REST API Deployment: Wrapping the trained model using FastAPI or Flask to serve real-time prediction endpoints for Security Information and Event Management (SIEM) dashboards.

Author Information :

Student Name: Bhumi

Program: IBM SkillsBuild Cyber Security Internship 2026 (conducted by BharatCares)

Project Topic: Intrusion Detection System (VIDS)


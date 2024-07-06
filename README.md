<h1 align="center">
  🤖 DDoS Attack Prediction with Machine Learning
</h1>

<p align="center">
  <img src="https://github.com/aidos-askhatuly/DDos_attack_detection/raw/main/pics/ddosattacks.jpg" alt="Description" width="600" height="400">
</p>

## 🎯 Project Overview
Traditional security solutions such as firewalls, antivirus software, and cryptography systems are no longer sufficient to address the evolving security threats including distiributed denial-of-service (DDoS) attacks due to:

- **Static Defence.** They operate on a static basis, often relying on predefined rules and signatures to detect and mitigate threats. This approach fails to adapt to the dynamic nature of modern cyber threats, making it easier for attackers to evade detection.

- **Limited Visibility.** They offer limited visibility into network traffic and user behavior, making it challenging to detect and respond to sophisticated attacks that may go unnoticed for extended periods.

- **Lack of Advanced Threat Detection.**  They can not detect advanced threats such as zero-day exploits, polymorphic malware, and targeted attacks. So, cybercriminals can exploit vulnerabilities in legacy systems to infiltrate networks and compromise sensitive data.

##  📊 Dataset
The dataset comes from open source network analyzing software **Wireshark**. Each entry represents a network packet and each column respresents different network packet attributes, including:
* Source and Destination address
* Packet Size
* Packet Rate
* Packet Delay
* Packet Send Time and Packet Received Time
* Byte Rate
* Network Utilization

## 🛠️ Project Workflow
### 🧹 <a href=https://github.com/aidos-askhatuly/DDos_attack_detection/blob/main/1.%20Data%20Cleaning.ipynb> Data Cleaning</a>
We began by inspecting the data format, identifying and addressing duplicates, and handling missing values.

### 📉 <a href=https://github.com/aidos-askhatuly/DDos_attack_detection/blob/main/2.%20EDA.ipynb> Exploratory Data Analysis (EDA) </a>
Used various plots like histograms and box plots to visualize data distributions and relationships. We examinined pairwise correlations between numerical features. Overall, EDA facilitated understanding the distribution of features and relationships between independent variables and the target value.

### ⚙️ <a href=https://github.com/aidos-askhatuly/DDos_attack_detection/blob/main/3.%20Data%20Preprocessing.ipynb> Data Preprocessing </a>
This included scaling, normalization, encoding categorical variables, and handling imbalanced classes by applying SMOTE oversampling technique. We reduced the multi-class classification problem to a binary classification because the total amount of all attack classes accounted for only 10% of the entire dataset.
### 🔮 <a href=https://github.com/aidos-askhatuly/DDos_attack_detection/blob/main/4.%20Modelling.ipynb> Modelling </a>
Assessed three predictive models to address the problem at hand:
* Logistic Regression
* XGBoost
* Dense Neural Network.
  
Conducted extensive hyperparameter tuning using grid search with cross validation.

To evaluate model performance, **F1 score** was selected as the primary metric. The F1 score is particularly suitable for imbalanced datasets as it considers both precision and recall, providing a balanced assessment of model performance across both classes.
## 🔍 Findings and Conclusions
Among the models evaluated, **XGBoost** emerged as the top performer with an F1 score of **93.2**%. This indicates that the XGBoost model effectively captured patterns in the data and made accurate predictions.

Potential improvements inlcude:

**1. Incorporating More Features:** Additional features not included in the current dataset could potentially enhance the predictive power of the model.

**2. Interpretability and Explainability:** Employ techniques such as SHAP (SHapley Additive exPlanations) values or LIME (Local Interpretable Model-agnostic Explanations) to interpret and explain model predictions, enhancing model transparency and trustworthiness.

**3. Data Quality and Pipeline Automation:** Implement data monitoring and automated pipelines for data preprocessing, feature engineering, model training, and evaluation to streamline the workflow and ensure consistency.

This project showcases the practical application of machine learning techniques in predicting distributed denial-of-service attacks. Through comprehensive data exploration and rigorous model evaluation, we successfully built predictive models capable of identifying potential DDoS attacks.

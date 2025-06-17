# Cyber_Attack_Detection

"""Cyber Attack Detection with Random Forest

"""## Detecting Cyber Attacks using machine learning

* To improve cyber security, machine learning algorithms can be implemented to detect cyber attacks.
* The approach involves analyzing network data to identify potential attacks by identifying correlations between various variables.
* By leveraging machine learning algorithms, the accuracy and efficiency of cyber attack detection can be improved. It will enhance the security of digital networks and systems.

## Cyber attack data

* The data is collected by the University of New South Wales (Australia). That includes records of different types of cyber attacks. The dataset contains network packets captured in the Cyber Range Lab of UNSW Canberra. The data is provided in two sets of training and testing data.

* The dataset includes nine types of attacks, including:

1. Fuzzers: Attack that involves sending random data to a system to test its resilience and identify any vulnerabilities.

2. Analysis: A type of attack that involves analyzing the system to identify its weaknesses and potential targets for exploitation.

3. Backdoors: Attack that involves creating a hidden entry point into a system for later use by the attacker.

4. DoS (Denial of Service): Attack that aims to disrupt the normal functioning of a system, making it unavailable to its users.

5. Exploits: Attack that leverages a vulnerability in a system to gain unauthorized access or control.

6. Generic: A catch-all category that includes a variety of different attack types that do not fit into the other categories.

7. Reconnaissance: Attack that involves gathering information about a target system, such as its vulnerabilities and potential entry points, in preparation for a future attack.

8. Shellcode: Attack that involves executing malicious code, typically in the form of shell scripts, on a target system.

9. Worms: A type of malware that spreads itself automatically to other systems, often causing harm in the process.

* These nine categories cover a wide range of attack types that can be used to exploit a system, and it is important to be aware of them to protect against potential security threats.


#Cyber Attack Detection with Machine Learning

#Project Overview

This project implements machine learning techniques to detect cyber attacks using the UNSW-NB15 dataset from the University of New South Wales. The dataset includes network traffic data with nine types of cyber attacks: Fuzzers, Analysis, Backdoors, DoS, Exploits, Generic, Reconnaissance, Shellcode, and Worms. The goal is to enhance cybersecurity by identifying potential threats through data analysis and machine learning models, focusing on high recall for robust detection.

##Dataset

The UNSW-NB15 dataset contains network packet captures from the Cyber Range Lab at UNSW Canberra. It is split into training and testing sets, which are combined and preprocessed for analysis. Key features include:
Network traffic attributes: Source to destination time to live (sttl), connection states (ct_state_ttl, state), connection rates (ct_dst_sport_ltm, rate), and more.
Attack categories: Nine distinct attack types, with 'Generic' and 'Exploits' being the most frequent.
Label: Binary indicator (0 for normal, 1 for attack).

#Project Structure

The code performs the following steps:

Data Preprocessing:
Combines training and testing datasets, drops the 'id' column, and encodes categorical variables ('proto', 'service', 'state') into numerical values.
Visualizes attack category distribution using a pie chart.

Feature Selection:
Analyzes correlations between features and the attack label using heatmaps.
Uses a Random Forest model to rank feature importance, selecting the top 10 features for further analysis.

Model Training and Evaluation:
Decision Tree: Optimized via grid search to maximize recall, with rules visualized for interpretability (e.g., sttl <= 61).
Random Forest: Applied to filtered data to classify attacks, achieving high recall for key attack types.
XGBoost and LightGBM: Additional models evaluated for comparison, with performance metrics (accuracy, precision, recall) visualized via confusion matrices.
Wilcoxon Rank Sum Test: Conducted to assess statistical significance of recall differences across models.

Attack Category Prediction:
A Random Forest model is trained on the top 10 features to predict specific attack categories, with performance evaluated using classification reports and multilabel confusion matrices.

#Key Findings
Feature Importance: Top features like sttl, ct_state_ttl, state, ct_dst_sport_ltm, and rate are strongly correlated with cyber attacks, reflecting behaviors like port scanning or DDoS attacks.

Model Performance: The Random Forest model achieves high recall for 'Generic', 'Normal', and 'Exploits' categories, while 'Fuzzers', 'Reconnaissance', and 'Analysis' show more false negatives.

Filtering Efficiency: Decision tree rules filter out 23% of non-threatening network traffic, streamlining further analysis.

Statistical Analysis: The Wilcoxon test indicates no significant difference in recall among Random Forest, XGBoost, and LightGBM, suggesting flexibility in model choice.

#Requirements
To run the code, install the following Python libraries:
pip install numpy pandas matplotlib seaborn scikit-learn nbformat graphviz dtreeviz xgboost lightgbm
Usage

Download the Dataset: The UNSW-NB15 dataset is sourced via kagglehub from the mrwellsdavid/unsw-nb15 dataset.
Run the Notebook:
Execute the Jupyter notebook (cyber_attack_detection.ipynb) in an environment like Google Colab or a local setup with the required libraries.
Ensure the dataset files (UNSW_NB15_training-set.csv and UNSW_NB15_testing-set.csv) are accessible.

Outputs:
Visualizations: Pie charts, heatmaps, and decision tree diagrams.
Metrics: Accuracy, precision, recall, and classification reports.
Feature rankings and correlation analyses.

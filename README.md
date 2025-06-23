Fraud Detection Using XGBoost
Project Overview
This project implements a fraud detection system using the XGBoost algorithm to classify financial transactions as fraudulent or non-fraudulent. The dataset contains transaction details such as amount, sender and recipient balances, and transaction types. The project addresses class imbalance using SMOTE (Synthetic Minority Over-sampling Technique) and evaluates the model's performance with metrics like accuracy, precision, recall, F1-score, and a confusion matrix.




Repository Structure
Fraud_detection_using_Xgboost/
│
├── data/
│   └── Fraud_detection.csv           # Dataset used for training and testing
├── notebooks/
│   └── Fraud_detection.ipynb         # Jupyter notebook with the complete analysis
├── scripts/
│   └── fraud_detection.py            # Python script version of the notebook (optional)
├── README.md                         # Project documentation
├── requirements.txt                  # Python dependencies
└── LICENSE                           # License file
 

Installation
To set up the project locally, follow these steps:

Clone the repository:
git clone https://github.com/dunaidutta007/Fraud_detection_using_Xgboost.git
cd Fraud_detection_using_Xgboost


Create a virtual environment (recommended):
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate


Install dependencies:
pip install -r requirements.txt


Run the notebook:

Open notebooks/Fraud_detection.ipynb in Jupyter Notebook or JupyterLab.
Ensure the dataset (data/Fraud_detection.csv) is in the correct path or update the file path in the notebook.



Dataset
The dataset (Fraud_detection.csv) contains the following columns:

step: Time step of the transaction.
type: Transaction type (e.g., PAYMENT, TRANSFER, CASH_OUT, CASH_IN, DEBIT).
amount: Transaction amount in local currency.
nameOrig: Identifier of the customer initiating the transaction.
oldbalanceOrg: Sender's balance before the transaction.
newbalanceOrig: Sender's balance after the transaction.
nameDest: Identifier of the transaction recipient.
oldbalanceDest: Recipient's balance before the transaction.
newbalanceDest: Recipient's balance after the transaction.
isFraud: Binary label (1 for fraudulent, 0 for non-fraudulent).
isFlaggedFraud: Indicates if the transaction was flagged as fraudulent (transfers > 200,000).

Note: Due to the large size of the dataset, it is not included in the repository. 
You can download it from https://drive.google.com/file/d/1negPlIMCT62oVpixMPEWrZHt7iWnJtgL/view?usp=sharing or use your own dataset with a similar structure.


Methodology

Data Preprocessing:

Loaded the dataset and checked for missing values (none found).
Dropped irrelevant columns (type, nameOrig, nameDest) for model training.
Encoded the type column as label_type for potential feature engineering.
Applied SMOTE to balance the dataset, addressing the class imbalance (fraudulent transactions: 8,213; non-fraudulent: 6,354,407).


Model Training:

Used XGBoost classifier with default parameters.
Split data into 80% training and 20% testing sets.
Trained the model on the balanced dataset.


Evaluation:

Achieved an accuracy of ~99.85%.
Precision: ~99.80%, Recall: ~99.91%, F1-Score: ~99.85%.
Cross-validated recall: ~99.93% ± 0.01%.
Visualized performance using a precision-recall curve.



Results
The XGBoost model demonstrates excellent performance, with high precision and recall, indicating robust detection of fraudulent transactions. The confusion matrix shows minimal false positives (2,576) and false negatives (1,145) out of ~2.54 million test samples.
Usage
To run the analysis:

Ensure all dependencies are installed (requirements.txt).
Open notebooks/Fraud_detection.ipynb in Jupyter Notebook.
Update the dataset path in the notebook to point to data/Fraud_detection.csv.
Execute the cells sequentially to preprocess data, train the model, and evaluate results.

Alternatively, run the script version (if provided):
python scripts/fraud_detection.py

Requirements
See requirements.txt for the list of required Python packages.
License
This project is licensed under the MIT License. See the LICENSE file for details.
Contributing
Contributions are welcome! Please follow these steps:

Fork the repository.
Create a new branch (git checkout -b feature-branch).
Make your changes and commit (git commit -m 'Add feature').
Push to the branch (git push origin feature-branch).
Create a pull request.

Contact
For questions or suggestions, please open an issue or contact [saptajit.bhu.stats26@gmail.com].

Built with ❤️ using Python, XGBoost, and Jupyter Notebook.

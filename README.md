<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f172a,50:0f766e,100:2dd4bf&height=220&section=header&text=Telco%20Customer%20Churn&fontSize=52&fontColor=ffffff&fontAlignY=36&animation=fadeIn&desc=Who%20is%20about%20to%20leave%20%E2%80%94%20and%20can%20we%20predict%20it%3F&descSize=18&descAlignY=58" width="100%" alt="Telco Customer Churn"/>
</p>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=20&duration=2600&pause=800&color=2DD4BF&center=true&vCenter=true&width=640&lines=7%2C032+customers+%E2%80%A2+4+engineered+features;5+models+%E2%80%A2+stratified+5-fold+CV;Winner%3A+Logistic+Regression+%F0%9F%8F%86;80.4%25+accuracy+%E2%80%A2+0.836+ROC-AUC" alt="typing"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white"/>
  <img src="https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
</p>

---

## 🧠 What I Built

An end-to-end **churn-prediction study** on the IBM Telco Customer Churn dataset, completed for Week 3 of a Data Science internship (Feature Engineering, Model Building & Feature Scaling). I cleaned the data, engineered new features, compared **five classifiers** under the same protocol, and justified the final model in a written report.

**My role:** individual assignment — all cleaning, feature engineering, modelling, evaluation and the report are my own work.

---

## 🔁 Pipeline

```mermaid
flowchart LR
    A[(7,043 rows<br/>raw CSV)] --> B[Clean<br/>fix TotalCharges · drop customerID]
    B --> C[(7,032 rows)]
    C --> D[Feature engineering<br/>+4 features]
    D --> E[One-hot encoding]
    E --> F[Stratified 80/20 split<br/>random_state=42]
    F --> G[Scaling<br/>StandardScaler · MinMaxScaler]
    G --> H[5 classifiers]
    H --> I[Test metrics +<br/>5-fold stratified CV]
    I --> J[🏆 Model selection]
```

### Data cleaning

- `TotalCharges` was stored as text with blanks for brand-new customers → converted to numeric; the **11 invalid rows** removed (7,043 → 7,032).
- `customerID` dropped as a non-predictive identifier.
- Target imbalance analysed before modelling (churners are the minority class), which is why F1, recall and ROC-AUC matter more than accuracy here.

### Engineered features

| Feature | Idea |
|---|---|
| `AvgMonthlySpend` | Total charges ÷ tenure — real average spend, robust for new customers |
| `ContractCommitment` | Contract type mapped to an ordinal commitment level (month-to-month → two-year) |
| `ServiceCount` | Number of add-on services a customer subscribes to |
| `ChargeCommitmentInteraction` | Interaction between monthly charges and commitment — high bill + low commitment is a churn signal |

---

## 📊 Results

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC | CV F1 (mean ± std) |
|---|---:|---:|---:|---:|---:|---:|
| 🏆 **Logistic Regression** | **0.8038** | 0.6503 | **0.5668** | **0.6057** | **0.8363** | **0.5931 ± 0.022** |
| Random Forest (200 trees) | 0.7854 | 0.6169 | 0.5080 | 0.5572 | 0.8224 | 0.5663 ± 0.019 |
| Support Vector Machine | 0.7974 | **0.6540** | 0.5053 | 0.5701 | 0.7827 | 0.5779 ± 0.010 |
| K-Nearest Neighbors | 0.7633 | 0.5553 | 0.5508 | 0.5530 | 0.7798 | 0.5578 ± 0.010 |
| Decision Tree | 0.7122 | 0.4608 | 0.4866 | 0.4733 | 0.6400 | 0.5031 ± 0.024 |

```mermaid
xychart-beta
    title "ROC-AUC by model"
    x-axis ["LogReg", "RandomForest", "SVM", "KNN", "DecisionTree"]
    y-axis "ROC-AUC" 0.5 --> 0.9
    bar [0.8363, 0.8224, 0.7827, 0.7798, 0.6400]
```

### Why Logistic Regression won

It led on accuracy, recall, F1, ROC-AUC **and** cross-validated F1, so its lead isn't a lucky split. The strongest signals — contract commitment, charges and tenure — relate to churn in a close-to-linear way, and the model's coefficients are interpretable — a telecom team can see *why* a customer is flagged. The Decision Tree overfit, which is exactly the problem Random Forest's bagging reduces.

**Limitation & next step:** recall of ~57% means roughly 4 in 10 churners are missed. Class weighting or SMOTE and threshold tuning toward recall would be the next experiment, since missing a churner usually costs more than a false alarm.

---

## 📂 Files

| File | Contents |
|---|---|
| `Telco_Customer_Churn_Week3.ipynb` | Full analysis and modelling notebook |
| `Telco_Customer_Churn_Week3_Report.pdf` | Written report with algorithm research and justification |
| `WA_Fn-UseC_-Telco-Customer-Churn.csv` | IBM Telco Customer Churn dataset |

```bash
pip install pandas numpy scikit-learn matplotlib jupyter
jupyter notebook Telco_Customer_Churn_Week3.ipynb
```

<p align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:2dd4bf,50:0f766e,100:0f172a&height=110&section=footer" width="100%" alt=""/>
</p>

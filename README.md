AI Worker Burnout & Attrition Risk
Every company is forcing employees to use AI tools. But nobody has measured — at what point does using too many AI tools actually start burning people out instead of helping them. That's what I tried to find.
Project Phases:
1. Problem Identification: At what threshold of AI tool saturation does workplace productivity transition into occupational burnout?
2. Exploratory Data Analysis, Visualization & Preprocessing: Understand the data through statistical & visual analysis, then apply principled preprocessing to prepare a clean dataset for modeling in Phase 3.
3. Feature Engineering: 7 new features created-burnout_satisfaction_ratio, ai_overload_score, productivity_burnout_gap, salary_experience_ratio, upskilling_ai_ratio, stress_composite, team_isolation_score
4. Methodology: Attrition Risk Classification Logistic Regression, SVM (RBF), Random Forest, XGBoost, LightGBM
   Evaluation: F1-macro, F1 for High-risk class specifically, ROC-AUC, Confusion matrices for all 5, ROC curves per class
   Burnout Score Regression (4 models): Ridge → Random Forest → XGBoost → LightGBM, with actual vs predicted scatter, residual plot, and 5-Fold CV R²

Best Result:
My model XGBoost got 86.3% accuracy and F1 score of 0.817 — which means it correctly identifies whether an employee is at Low, Medium, or High attrition risk 86 times out of 100. 
The ROC-AUC was 0.952 out of 1.0 

Class Imbalance Problem:
Here's the tricky part — only 5.7% of employees were High risk. That means if a dumb model just says 'everyone is Low risk' it gets 94% accuracy but catches zero high-risk employees — useless for HR. We used a technique called SMOTE which creates synthetic examples of rare cases so the model actually learns to catch the dangerous ones. After SMOTE our High-risk detection F1 went from basically zero to 0.70.


---

📌 DESCRIPTION

This project builds a binary classification model to predict Drug-Induced Autoimmunity (DIA) using supervised machine learning. It leverages RDKit-generated molecular descriptors and evaluates two core models:

- K-Nearest Neighbours (KNN)
- Decision Tree (DT)

Both models were trained using SMOTE to address class imbalance. KNN was additionally scaled using StandardScaler due to its reliance on distance-based metrics. To improve model reliability beyond a single train-test split, KNN was validated using:

- StratifiedKFold Cross-Validation  
- RepeatedStratifiedKFold Cross-Validation

These resampling strategies demonstrated strong generalisation, yielding average F1-scores of 0.80 and 0.81, respectively. The final KNN model (k=3) selected via cross-validation achieved a training accuracy of 93% and AUC of 0.99. While KNN (k=5) gave the best recall on the test set (0.70), the cross-validated KNN model was retained for its superior robustness to unseen data.

📄 HOW TO RUN

Recommended: In Google Colab
1. Upload `model.ipynb` to Google Colab.
2. Mount your Google Drive:
   from google.colab import drive  
   drive.mount('/content/drive')

3. Ensure these files are in your Drive:
   - DIA_trainingset_RDKit_descriptors.csv
   - DIA_testset_RDKit_descriptors.csv

Alternative (Manual):
Update local file paths in the notebook:
   df_train = pd.read_csv('path/to/DIA_trainingset_RDKit_descriptors.csv')  
   df_test = pd.read_csv('path/to/DIA_testset_RDKit_descriptors.csv')

---

📊 DATASET

Dataset source: UCI Machine Learning Repository  
Drug-Induced Autoimmunity Prediction  
https://archive.ics.uci.edu/dataset/1104/drug_induced_autoimmunity_prediction

---

📈 EXPECTED OUTPUT

- Cleaned and preprocessed feature dataset
- Balanced data using SMOTE
- Model training: DT and KNN (with scaling)
- Extended validation: StratifiedKFold and RepeatedStratifiedKFold
- Evaluation metrics:
  - Confusion Matrix
  - Recall, Precision, F1-Score
  - ROC Curves
  - AUC Bar Charts  
- Best performing:
  - KNN (k=5) for test recall (0.70, AUC = 0.74)
  - KNN (k=3) for robust cross-validated F1-score (0.81)

---

📝 NOTES

- Emphasis placed on DIA-positive recall, as false negatives pose safety risks.
- Models prioritised interpretability and reproducibility.
- All results were validated across multiple resampling strategies.
- The final KNN (k=3) was retained due to its superior generalisation on unseen data, despite KNN (k=5) showing better test recall.

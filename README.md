🫀 Heart Failure Prediction — Supervised Learning Lab
A complete supervised learning analysis on the Heart Failure Prediction Dataset.
Built as part of a Machine Learning hands-on lab covering Decision Tree, Linear Regression, Logistic Regression, and Naïve Bayes.

📁 Project Structure
heart-disease-supervised-learning/
│
├── heart.csv                                  # Dataset (918 patients, 12 features)
├── heartfailure.ipynb    # Main Jupyter Notebook
├── README.md                                  # Project documentation
└── requirements.txt                           # Python dependencies

📊 Dataset Overview
Source: Heart Failure Prediction Dataset
Rows: 918 patients | Columns: 12 | Target: HeartDisease (0 = No, 1 = Yes)
FeatureTypeDescriptionAgeNumericalPatient age in yearsSexCategoricalM = Male, F = FemaleChestPainTypeCategoricalATA, NAP, ASY, TARestingBPNumericalResting blood pressure (mm Hg)CholesterolNumericalSerum cholesterol (mm/dl)FastingBSBinaryFasting blood sugar > 120 mg/dl (1 = True, 0 = False)RestingECGCategoricalResting ECG resultsMaxHRNumericalMaximum heart rate achievedExerciseAnginaCategoricalExercise-induced angina (Y/N)OldpeakNumericalST depression induced by exerciseST_SlopeCategoricalSlope of peak exercise ST segmentHeartDiseaseBinary Target0 = No Disease, 1 = Disease

⚙️ Preprocessing

Categorical columns encoded using LabelEncoder:
Sex, ChestPainType, RestingECG, ExerciseAngina, ST_Slope
No feature scaling applied — not required for Decision Tree and Naïve Bayes
Train/Test split: 80% train / 20% test (random_state=42)
No missing values found in the dataset


🤖 Models
3. Decision Tree Classifier

max_depth=4 to prevent overfitting
Full tree visualization with color-coded nodes
Most important features: ST_Slope and ChestPainType
Hyperparameter tuning with GridSearchCV on max_depth, criterion, min_samples_split, min_samples_leaf

4. Linear Regression

Applied to binary target (treated as continuous 0/1)
Predictions thresholded at 0.5 for class labels
Evaluated with MSE, R², and thresholded accuracy
Included for comparison — not recommended for binary classification

5. Logistic Regression

Proper probabilistic model for binary classification
Uses sigmoid function to output class probabilities
Regularization tuning: L1 (Lasso) vs L2 (Ridge), C values compared
Evaluated with Accuracy, AUC-ROC, Confusion Matrix

6. Naïve Bayes (Gaussian)

Assumes features follow a normal distribution and are independent
Hyperparameter: var_smoothing tuned with GridSearchCV
Fastest model to train
Evaluated with Accuracy, AUC-ROC, Probability Distribution plot


📈 Results
ModelAccuracyPrecisionRecallF1 ScoreAUC-ROCDecision Tree0.86960.89740.88790.89260.9121Linear Regression0.83700.86140.86920.8653—Logistic Regression0.84240.90910.81310.85840.9010Naïve Bayes0.84240.88240.84110.86120.9090
Key Findings

Decision Tree achieved the highest accuracy at 86.96%
Naïve Bayes achieved the highest AUC-ROC at 0.9090 — best at ranking patients by risk
ST_Slope and ChestPainType are the most predictive features
Linear Regression is not suitable for binary classification — included for academic comparison
Logistic Regression is the most appropriate model for clinical use due to calibrated probabilities


🚀 How to Run
1. Clone the repository
bashgit clone https://github.com/<your-username>/heart-disease-supervised-learning.git
cd heart-disease-supervised-learning
2. Install dependencies
bashpip install -r requirements.txt
3. Launch Jupyter Notebook
bashjupyter notebook Heart_Disease_Supervised_Learning.ipynb
4. Run all cells from top to bottom

📦 Requirements
pandas
numpy
matplotlib
scikit-learn
jupyter
Install with:
bashpip install pandas numpy matplotlib scikit-learn jupyter

🗂️ Notebook Structure
CellContent1Imports & Setup2Load & Explore Dataset3Preprocessing — Encode & Split4–6Decision Tree — Train, Plot Tree, Confusion Matrix7–9Linear Regression — Train, Predictions, Coefficients10–12Logistic Regression — Train, ROC, Coefficients13–14Naïve Bayes — Train, ROC15–16Summary — Bar Chart, Combined ROC, Results Table

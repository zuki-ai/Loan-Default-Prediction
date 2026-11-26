START

-- Data Import
IMPORT dataset FROM CSV file

-- Target and Feature Definition
SET target_variable = Status
SET features = ALL COLUMNS EXCEPT target_variable AND ID

-- Data Exploration
CHECK missing values in dataset
CHECK class distribution of Status

-- Data Preprocessing
IF missing values exist THEN
    FILL missing values
ENDIF

ENCODE categorical features in feature_set
NORMALIZE numerical features

-- Feature Selection
SELECT important features from feature_set

-- Dataset Splitting
SPLIT dataset INTO training_set and testing_set

-- Model Initialization
INITIALIZE Logistic_Regression
INITIALIZE Decision_Tree
INITIALIZE Random_Forest
INITIALIZE Support_Vector_Machine

STORE models IN model_list

FOR EACH model IN model_list DO
    TRAIN model USING training_set
    PREDICT results USING testing_set
    COMPUTE Accuracy, Precision, Recall, F1_Score
    STORE evaluation results
ENDFOR

-- Model Evaluation
COMPARE performance OF all models

-- Model Combination
ENSEMBLE all models

-- Performance Comparison
COMPARE performance OF
    Individual best model
    Combined ensemble model

-- Model Selection
SELECT model WITH best Recall and stable overall performance

-- Final Prediction
USE selected model TO predict loan default risk

END


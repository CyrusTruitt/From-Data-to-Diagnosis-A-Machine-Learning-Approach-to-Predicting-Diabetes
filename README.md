# From Data to Diagnosis:
## A Machine Learning Approach to Predicting Diabetes


## What Is Diabetes? 

Diabetes is a chronic medical condition where the body struggles to regulate blood sugar (glucose) levels due to problems with insulin production or usage. There are two main types:

Type 1 Diabetes: An autoimmune condition where the immune system attacks insulin-producing cells in the pancreas, resulting in little to no insulin production. It often develops in childhood or adolescence.

Type 2 Diabetes: The more common form, where the body becomes resistant to insulin or doesn't produce enough of it. Type 2 diabetes typically develops in adults, though it’s becoming more common in younger populations due to lifestyle factors.

Diabetes is significant because uncontrolled blood sugar levels can lead to serious health complications over time, including heart disease, kidney failure, nerve damage, and vision problems. It can also increase the risk of infections and, in severe cases, result in life-threatening conditions like diabetic ketoacidosis (DKA) or hyperosmolar hyperglycemic state (HHS).

## Importance of Predicting Diabetes
- Early Intervention: Identifying those at risk of developing diabetes early allows for preventive measures, such as lifestyle changes or medications, which can delay or prevent the onset of the disease.

- Improved Health Outcomes: Early prediction enables healthcare providers to guide patients in managing their health proactively. By controlling blood sugar levels early, patients can reduce the risk of complications and enjoy a better quality of life.

- Cost-Effective Healthcare: Managing diabetes-related complications can be costly for healthcare systems and individuals. Early prediction and preventive care can significantly reduce these costs by decreasing hospitalizations, procedures, and treatments needed for advanced disease stages.

- Public Health Impact: With the rising prevalence of diabetes worldwide, predicting and preventing diabetes in high-risk populations can have a substantial impact on public health, potentially reducing the overall disease burden and improving population health.

By using machine learning to predict diabetes risk, healthcare professionals can identify individuals at risk more accurately and efficiently than traditional methods, enabling targeted and timely interventions to prevent or delay the disease.

## Project Explanation and Results

This project provides an analysis of various machine learning models used to predict diabetes risk based on a set of health-related features. Here’s a breakdown of what it’s telling us:

- Objective: The study aims to determine which machine learning models can best predict the risk of diabetes, potentially assisting with early intervention and improving patient outcomes.

- Models Evaluated: Several models were tested, including Gradient Boosting Machine (GBM), Random Forest, Logistic Regression, Neural Network, Support Vector Machine (SVM), and Decision Tree. Each model's performance was measured across different metrics: Accuracy, Sensitivity, Specificity, and Area Under the Curve (AUC).

- Key Predictors: The analysis identifies important predictors in determining diabetes risk. Body Mass Index (BMI) stands out as the most influential factor in predicting diabetes, followed by factors such as Cholesterol Check and Heavy Alcohol Consumption. These features, particularly BMI, are highlighted for their significant impact on the model’s predictions.

- Correlation Analysis: A correlation matrix is displayed to show the relationships between features related to diabetes risk. Strong positive correlations, like the one between Physical Health and General Health, indicate that poorer physical health is often associated with worse general health. Some weaker negative correlations are also observed, such as between Physical Activity and Mental Health, hinting that higher physical activity might be beneficial for mental well-being.

- ROC Curves and Model Comparison: The ROC curves compare the performance of each model. The Gradient Boosting Machine, Logistic Regression, and Neural Network models have similar AUC scores (0.83), indicating a strong ability to differentiate between diabetic and non-diabetic cases. The Decision Tree model has the lowest AUC (0.77), suggesting it is less effective for this task.

- Key Health Feature Analysis: The poster explores how specific health features (such as Age, BMI, General Health, and High Blood Pressure) relate to diabetes status. This analysis helps to visualize how these variables interact and potentially contribute to the likelihood of developing diabetes.

- Performance Summary: The Gradient Boosting Machine (GBM) and Random Forest models performed best overall, particularly in AUC scores, which suggests these models are most reliable for predicting diabetes risk. Logistic Regression also provided consistent predictions but had a slightly lower AUC than the ensemble methods. The Decision Tree model’s lower accuracy suggests it might have overfitted the data, and the Neural Network delivered balanced results across all metrics.

This project not only presents a comparative analysis of model effectiveness but also highlights key predictors and health feature relationships, helping readers understand the predictive potential and limitations of each model for diabetes risk estimation.


### Step-by-Step Process for Diabetes Risk Prediction

1.) Loading and Inspecting Data:

- Load necessary libraries such as dplyr and readxl.
- Read the diabetes dataset using read_excel() and inspect it with head(), str(), and summary() to understand its structure and contents.
2.) Handling Missing Values:

- Check for missing values in each column using colSums(is.na(diabetes)).
- Replace missing values in each column with the column's median using mutate(across()).
3.) Converting Categorical Variables to Factors:

- Convert relevant columns (e.g., Sex, HighChol, Smoker) to factor data types, as these represent categorical information.
4.) Standardizing Continuous Variables:

- Standardize continuous variables (e.g., Age, BMI, MentHlth, PhysHlth) to ensure consistent scales, using mutate(across(..., scale)).
5.) Splitting the Data into Training and Testing Sets:

- Use createDataPartition() from the caret package to split the dataset into 70% training and 30% testing sets.
6.) Building and Evaluating Models:

- Logistic Regression: Train a logistic regression model, make predictions, and evaluate it with a confusion matrix.
- Decision Tree: Train a decision tree model, make predictions, and evaluate with a confusion matrix.
- Random Forest: Train a random forest model with 100 trees, make predictions, and evaluate with a confusion matrix.
- G- radient Boosting Machine (GBM): Train a GBM model, make predictions, and evaluate with a confusion matrix.
- Neural Network: Train a neural network model, convert prediction probabilities to class labels, and evaluate with a confusion matrix.
7.) Collecting and Visualizing Model Performance Metrics:

- Create a model_metrics data frame to store metrics (Accuracy, Sensitivity, Specificity, AUC) for each model.
- Use a helper function (get_metrics) to compute and store metrics for each model.
- Visualize model comparisons for Accuracy, Sensitivity, Specificity, and AUC using bar charts with ggplot2.
8.) Plotting ROC Curves:

- Set up a base ROC plot and plot individual ROC curves for each model using roc() from the pROC package.
- Add a legend with AUC values for easy comparison.
![Figure 3](https://github.com/user-attachments/assets/ff69938e-0c9e-4f61-b0d8-791b25b76a94)

9.) Feature Importance Analysis:

- Calculate feature importance for the Random Forest model using importance() and visualize it with a horizontal bar chart in ggplot2.

![Feature Importance for Diabetes Prediction](https://github.com/user-attachments/assets/0102df26-52ab-429f-94f8-1b4fde64b56b)
10.) Exploratory Data Analysis (EDA):

- Distribution of Age: Create a histogram to examine the age distribution.
![Age Distribution of Participants](https://github.com/user-attachments/assets/f4c306fb-19f4-4a1f-92f4-1f82bb65d03a)

- BMI Density by Diabetes Status: Use a density plot to compare BMI distributions between diabetic and non-diabetic individuals.
![BMI Density by Diabetes Status](https://github.com/user-attachments/assets/aea9c376-b831-4c62-bded-298546edf1b8)

- Correlation Heatmap: Calculate and visualize correlations between numeric features using a heatmap.
![Correlation Heatmap of Features](https://github.com/user-attachments/assets/84137064-70ce-484d-87dd-377c847d7ee1)

- Categorical Analysis of Smoking Status: Create a 100% stacked bar plot to analyze the relationship between smoking status and diabetes.
![Proportion of Smoking Status by Diabetes Status](https://github.com/user-attachments/assets/9ec1651e-8ca3-47d2-b0d5-058b19fbc3c8)

11.) Pair Plot for Key Features:

- Use ggpairs() from the GGally package to create a pair plot for key predictors (e.g., Age, BMI, GenHlth) by diabetes status, offering a visual comparison of feature distributions and relationships.


![Pair Plot of Key Health Features by Diabetes Status](https://github.com/user-attachments/assets/6bedcf20-933b-4a69-8f5d-7e8476fc7e0e)

# Final Poster

![Screenshot 2024-11-07 160754](https://github.com/user-attachments/assets/88458819-1cd0-4dd3-86dd-da97439a9c0d)



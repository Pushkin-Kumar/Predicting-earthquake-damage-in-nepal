# 🏚️ Earthquake Damage Prediction

Predicting the severity of earthquake damage to buildings can help prioritize recovery efforts and improve safety measures.  
This project explores machine learning approaches to classify buildings as likely to suffer **severe damage** or not, based on pre-earthquake features.

---

## 📂 Dataset

The dataset contains information about buildings, including:
- Structural characteristics (foundation type, height, age, material, etc.)  
- Pre-earthquake features (before the disaster)  
- Post-earthquake features (used for analysis but removed from the model to avoid data leakage)

The target variable is **`damage_grade`**, which we converted into a **binary target** called `severe_damage`:
- 1 → Severe damage (Grade 4 or above)  
- 0 → Not severe damage (Grade 3 or below)

---

## 🧹 Data Cleaning & Preprocessing

Key preprocessing steps:
1. **Handling missing values**:  
   - Filled missing entries in `damage_grade` using the **mode** of the column.  
2. **Removing post-earthquake features**:  
   - Dropped columns containing `"post_eq"` to avoid data leakage.  
3. **Feature engineering**:  
   - Created a binary target `severe_damage` from `damage_grade`.  
4. **Encoding categorical variables**:  
   - Used `OneHotEncoder` for logistic regression pipelines.  
   - Used `OrdinalEncoder` for tree-based models.  
5. **Train-test split**:  
   - 80% training, 20% testing, with `random_state` for reproducibility.

---

## 🔍 Exploratory Data Analysis

- **Boxplots** and **bar charts** were used to explore features such as building height and foundation type.  
- **Correlation heatmaps** were plotted to check for multicollinearity before using linear models.  
- Pivot tables and horizontal bar charts helped identify categorical features that influence severe damage.  

These analyses guided feature selection and helped understand relationships between building attributes and earthquake damage.

---

## 🤖 Machine Learning Models

### Logistic Regression Pipeline
- **Pipeline components**:  
  1. `OneHotEncoder` – Converts categorical features into numeric format  
  2. `LogisticRegression` – Linear model for binary classification
- Evaluated with training and test accuracy.
- Explored `predict_proba` to understand predicted probabilities.
- Calculated **odds ratios** to interpret feature influence on severe damage.

### Decision Tree Pipeline
- **Pipeline components**:  
  1. `OrdinalEncoder` – Encodes categorical features as ordinal numbers  
  2. `DecisionTreeClassifier` – Non-linear model to capture complex relationships
- Evaluated training and validation accuracy for hyperparameter tuning (`max_depth`).
- Visualized tree depth to interpret model complexity.
- Plotted training vs. validation accuracy across different `max_depth` values to detect overfitting.
- Selected optimal `max_depth` based on validation performance and evaluated the final model on the test set.
- Used `plot_tree` to visualize the decision logic.
- Extracted and visualized **feature importances** (Gini importance) to understand influential building attributes.

---

## 📊 Key Insights

- Taller buildings and certain foundation types are more prone to severe damage.  
- Logistic regression provided interpretable **odds ratios** for each feature.  
- Decision Trees captured non-linear relationships and offered intuitive visualizations of decision paths.  
- Hyperparameter tuning (`max_depth`) is crucial to balance overfitting and underfitting.  
- Feature importance analysis helps prioritize structural characteristics that are critical for earthquake resilience.

---

## 🏁 Conclusion

This project demonstrates the **end-to-end workflow** for predicting severe earthquake damage:  
- Data cleaning and preprocessing  
- Exploratory data analysis  
- Building interpretable machine learning pipelines  
- Hyperparameter tuning and model evaluation  
- Model interpretation via odds ratios and feature importances

By combining linear and tree-based models, we can **predict high-risk buildings** and provide actionable insights for disaster management.

---

## 📈 Technologies & Libraries

- Python 3  
- pandas, numpy, matplotlib, seaborn  
- scikit-learn (LogisticRegression, DecisionTreeClassifier, pipelines)  
- category_encoders (OneHotEncoder, OrdinalEncoder)  

---

## ✨ Author
**Pushkin Kumar**  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/pushkin-kumar)
_Data Analyst | Data Engineer_  
Passionate about building modern data pipelines and predictive models.

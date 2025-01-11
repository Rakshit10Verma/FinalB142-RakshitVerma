# Diabetes Analysis Project

## Overview
This project implements a data processing and analysis pipeline for diabetes prediction using Apache Spark and Hadoop MapReduce. The analysis focuses on a dataset from the National Institute of Diabetes and Digestive and Kidney Diseases (NIDDK), processing medical data to identify patterns and correlations related to diabetes diagnosis.

## Dataset
- Source: NIDDK diabetes database
- Target: Predict diabetes presence in female patients
- Inclusion Criteria:
  - Gender: Female only
  - Age: 21 years or older
- Features:
  - Number of pregnancies
  - Glucose level
  - Blood Pressure
  - Skin Thickness
  - Insulin level
  - BMI (Body Mass Index)
  - DiabetesPedigreeFunction
  - Age
  - Outcome (Target Variable)

## Project Structure
```
├── data/
│   └── diabetes_cleaned.csv
├── src/
│   ├── diabetes_mapper.py
│   ├── diabetes_reducer.py
│   └── spark_analysis.py
```

## Technologies Used
- Python 3.x
- Apache Spark
- Hadoop MapReduce
- PySpark
- Pandas
- Matplotlib
- Seaborn
- NumPy

## Setup and Installation

1. Install PySpark:
```bash
pip install pyspark
```

2. Make the Python scripts executable:
```bash
chmod +x diabetes_mapper.py
chmod +x diabetes_reducer.py
```

3. Upload data to HDFS:
```bash
hdfs dfs -put diabetes_cleaned.csv /user/hadoop/diabetes/
```

## Data Processing Pipeline

### 1. Data Cleaning and Preprocessing
- Missing value imputation using median for numerical columns
- Mode imputation for categorical columns
- Duplicate record removal
- Date/time format standardization

### 2. MapReduce Implementation
- **Mapper**: Processes input data line by line and extracts relevant features
- **Reducer**: Aggregates results and performs category-wise analysis

### 3. Spark Analysis
- Feature engineering using VectorAssembler
- K-means clustering implementation
- Correlation analysis
- Visualization of results using matplotlib and seaborn

## Running the Analysis

1. Execute the Hadoop MapReduce job:
```bash
hadoop jar /path/to/hadoop-streaming.jar \
    -input /user/hadoop/diabetes/diabetes_cleaned.csv \
    -output /user/hadoop/diabetes/output \
    -mapper diabetes_mapper.py \
    -reducer diabetes_reducer.py \
    -file diabetes_mapper.py \
    -file diabetes_reducer.py
```

2. Check the output:
```bash
hdfs dfs -cat /user/hadoop/diabetes/output/part-00000
```

## Results and Analysis
- The project includes visualization of feature relationships through:
  - K-means clustering visualization
  - Correlation matrix heatmap
  - Pairwise feature relationships
- Statistical analysis of key medical indicators
- Identification of potential diabetes risk factors

## Conclusions
The analysis reveals correlations between various health metrics and diabetes outcomes. Key findings include:
- Weak positive correlation between age and blood sugar levels
- Various relationships between medical indicators and diabetes diagnosis
- Clustered patterns in patient data that might indicate risk groups

## Future Improvements
1. Implement more advanced machine learning models
2. Add cross-validation and model evaluation metrics
3. Include more sophisticated feature engineering
4. Expand the analysis to include additional medical indicators

# Explorable Walkability: A Dual Approach of Classification and Regression

## Overview

This project explores **urban walkability** using machine learning through a dual-approach methodology combining both **classification and regression models**. Walkability is a critical urban planning metric that measures how pedestrian-friendly an area is, considering factors like population density, proximity to amenities, street connectivity, and employment accessibility.

By leveraging the EPA SmartLocation Database and geographic data from New Jersey, this project demonstrates how machine learning can predict and classify walkability scores across different urban block groups.

## Project Objectives

1. **Predict Walkability Scores** - Use regression models to estimate continuous walkability values
2. **Classify Walkability Categories** - Categorize areas into walkability levels using classification models
3. **Identify Key Features** - Determine which urban characteristics most influence walkability
4. **Visualize Geographic Patterns** - Create maps showing walkability distribution across New Jersey
5. **Compare Model Performance** - Evaluate multiple algorithms to identify the best predictive approach

## Dataset

### Sources
- **EPA SmartLocation Database (V3, January 2021)**: Contains comprehensive walkability metrics and urban characteristics for block groups across the United States
- **New Jersey Geographic Data**: 
  - County boundaries (GeoJSON format)
  - Block group boundaries (shapefile format from NHGIS)

### Key Features
The dataset includes 117+ features covering:

- **Population & Housing**: Total population, household count, housing units
- **Employment**: Total employment, employment by wage tier (low/medium/high)
- **Auto Ownership**: Distribution of vehicles per household
- **Density Measures**:
  - D1A: Gross population density
  - D1B: Retail employment density
  - D1C: Office employment density
- **Accessibility Indices**:
  - D2A: Jobs per household ratio
  - D2B: Employment mix (retail/office)
  - D2C: Transit mix index
  - D2R: Job/population ratio
  - D3B: Walking distance to nearest retail
  - D4A: Intersection density
  - D5*: Diversity indices
- **Target Variable**: **NatWalkInd** - National Walkability Index (1-20 scale)

### Data Preprocessing
- **Missing Value Treatment**: Iterative imputation using scikit-learn
- **Outlier Handling**: Identified and managed extreme values
- **Feature Scaling**: StandardScaler normalization
- **Class Imbalance**: Addressed through resampling techniques

## Methodology

### Approach 1: Regression Analysis
Predicts continuous walkability scores (1-20 scale)

**Models Implemented:**
- Linear Regression (baseline)
- Decision Tree Regressor
- Gradient Boosting Regressor
- Random Forest Regressor

**Optimization:**
- GridSearchCV for hyperparameter tuning
- K-Fold cross-validation
- Metrics: MAE, MAPE, R² Score, Mean Squared Error

### Approach 2: Classification Analysis
Categorizes areas into walkability classes (e.g., Low, Medium, High)

**Models Implemented:**
- Random Forest Classifier
- Gradient Boosting Classifier

**Optimization:**
- Hyperparameter tuning via GridSearchCV
- Stratified K-Fold cross-validation
- Metrics: Accuracy, Precision, Recall, F1-Score, ROC-AUC

## Technical Stack

### Libraries & Tools
- **Data Processing**: pandas, numpy
- **Geospatial Analysis**: geopandas, folium, shapely
- **Machine Learning**: scikit-learn, scikit-optimize
- **Visualization**: matplotlib, seaborn, plotly, folium maps
- **Optimization**: scikit-optimize (Bayesian optimization)

### Environment
- Python 3.11+
- Jupyter Notebook (Google Colab compatible)
- Required dependencies: See imports in `Final_Project_AG.ipynb`

## Key Findings

### Walkability Patterns in New Jersey
- Geographic variation across 21 counties
- Urban core areas show higher walkability indices
- Suburban regions demonstrate lower walkability scores
- Employment density is a strong predictor of walkability

### Model Performance
- **Best Regression Model**: Gradient Boosting Regressor
  - Excellent prediction accuracy across test sets
  - Strong generalization to unseen data
- **Best Classification Model**: Gradient Boosting Classifier
  - High accuracy in categorizing walkability levels
  - Robust performance across different urban contexts

### Important Features (by importance)
1. D3B - Distance to nearest retail (strong inverse relationship)
2. D2A - Jobs per household ratio
3. D1B - Retail employment density
4. D4A - Intersection density
5. Population density metrics

## File Structure

```
anishbosegupta/Explorable-Walkability/
├── README.md                                    # This file
├── Final_Project_AG.ipynb                       # Main Jupyter notebook with all analyses
├── Final Paper Machine Learning.docx            # Detailed project report
├── EPA_SmartLocationDatabase_V3_Jan_2021_Final.csv  # Raw walkability data
├── NJ_Counties_NGJIN_2021.geojson             # NJ county boundaries
└── nj_blockgroups_nhgis_webm.zip              # NJ block group boundaries
```

## Project Workflow

### 1. **Data Loading & Exploration** (Notebook Cells 1-2)
- Import EPA SmartLocation Database
- Load geographic data (counties, block groups)
- Initial exploratory data analysis (EDA)
- Summary statistics and data distribution analysis

### 2. **Data Cleaning & Preprocessing** (Notebook Cells 3-5)
- Identify missing values
- Handle missing data through iterative imputation
- Remove outliers
- Feature engineering and selection

### 3. **Exploratory Analysis** (Notebook Cells 6-10)
- Visualize walkability distribution
- Create geographic maps
- Analyze feature correlations
- Investigate urban patterns

### 4. **Model Development - Regression** (Notebook Cells 11-15)
- Train multiple regression models
- Perform hyperparameter tuning
- Evaluate and compare models
- Analyze feature importance

### 5. **Model Development - Classification** (Notebook Cells 16-20)
- Train classifiers with walkability categories
- Optimize hyperparameters
- Generate confusion matrices and ROC curves
- Compare classification performance

### 6. **Results & Visualization** (Notebook Cells 21-25)
- Create geographic heatmaps of predictions
- Visualize model predictions vs. actual values
- Generate comparison tables
- Produce interpretable summary visualizations

## Usage

### Running the Project

1. **Clone the repository:**
   ```bash
   git clone https://github.com/anishbosegupta/Explorable-Walkability.git
   cd Explorable-Walkability
   ```

2. **Open in Jupyter/Colab:**
   - Local: `jupyter notebook Final_Project_AG.ipynb`
   - Google Colab: Upload notebook and data files

3. **Install Dependencies:**
   ```bash
   pip install pandas numpy matplotlib seaborn geopandas folium shapely
   pip install scikit-learn scikit-optimize plotly
   ```

4. **Run All Cells:**
   - Execute notebook sequentially for full analysis pipeline
   - Or run specific sections for targeted analysis

### Reproducing Results

- All preprocessing, model training, and evaluation code is contained in the notebook
- Set random seeds for reproducibility (already configured)
- Results should be consistent across runs

## Visualizations

The project generates several key visualizations:

1. **Walkability Heatmaps**: Geographic maps showing walkability indices across NJ
2. **Feature Importance Plots**: Bar charts showing predictive feature rankings
3. **Prediction vs. Actual**: Scatter plots comparing model predictions to true values
4. **Confusion Matrices**: Classification model performance matrices
5. **ROC Curves**: Receiver Operating Characteristic curves for classifiers
6. **Distribution Plots**: Histograms and density plots of walkability scores

## Insights & Implications

### Urban Planning
- Identifies neighborhoods for walkability improvement initiatives
- Highlights infrastructure gaps affecting pedestrian accessibility
- Supports data-driven zoning and development decisions

### Policy Recommendations
- Focus development in high-connectivity areas
- Improve street connectivity in isolated regions
- Enhance transit access to reduce auto-dependency

### Further Research
- Temporal analysis of walkability trends
- Impact of new developments on walkability
- Correlation with public health outcomes (obesity, transit usage)
- Application to other states and urban areas

## Model Comparison Summary

| Model Type | Algorithm | Optimization | Use Case |
|-----------|-----------|--------------|----------|
| Regression | Gradient Boosting | GridSearchCV + Cross-Validation | Continuous walkability score prediction |
| Classification | Gradient Boosting Classifier | Stratified K-Fold CV | Category-based area classification |
| Baseline | Linear/Tree Models | Standard training | Performance comparison |

## Limitations & Future Work

### Current Limitations
- Analysis limited to New Jersey block groups
- Static dataset (January 2021 snapshot)
- Does not account for recent development changes
- Limited to tabular EPA database features

### Future Enhancements
- Incorporate real-time traffic and transit data
- Add satellite imagery for street-level features
- Develop interactive web dashboard for exploration
- Extend analysis to national or multi-state level
- Integrate demographic and health outcome data
- Machine learning model deployment as API

## References

- EPA SmartLocation Database: [https://www.epa.gov/smartgrowth/smart-location-mapping](https://www.epa.gov/smartgrowth/smart-location-mapping)
- National Historical Geographic Information System (NHGIS): [https://www.nhgis.org](https://www.nhgis.org)
- Walkability Research: [Center for Neighborhood Technology](https://www.cnt.org/)
- Scikit-learn Documentation: [https://scikit-learn.org](https://scikit-learn.org)

## Author

**Anish Gupta**

## License

This project is provided for educational and research purposes.

## Contact & Contributions

For questions, suggestions, or contributions to this project, please feel free to open an issue or submit a pull request.

---

**Last Updated**: July 2026  
**Project Status**: Complete Research Project

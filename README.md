# 🏙️ NYC Property Fraud Anomaly Detection  

This project develops an **unsupervised fraud detection framework** for over **1M NYC property tax assessment records**. The goal is to identify **suspicious or anomalous property records** that may indicate fraud, data entry errors, or unfair tax assessments.  

By combining **domain-driven feature engineering**, **dimensionality reduction**, and **anomaly detection algorithms**, the framework provides auditors with a scalable tool to prioritize investigations and improve public trust in property taxation.  

---

## 📌 Project Overview  
The NYC Department of Finance oversees millions of property tax assessments annually. Errors or fraudulent records can lead to unfair taxation and revenue losses.  

This project applies **data science methods** to detect irregularities in property valuations by:  
1. Cleaning and imputing property tax data.  
2. Engineering fraud-sensitive ratios and validation features.  
3. Applying **Principal Component Analysis (PCA)** for dimensionality reduction.  
4. Scoring anomalies using **Minkowski Distance** and **Autoencoder Reconstruction Error**.  
5. Ranking suspicious properties and analyzing case studies.  

---

## 🔍 Methodology  

### 1. Data Preparation  
- Dataset: 1M+ property tax assessment records.  
- Features: valuation metrics, building dimensions, tax classes, exemptions, and geospatial attributes.  
- Cleaning:  
  - Excluded irrelevant property types (e.g., utilities, mixed-unit placeholders).  
  - Imputed missing values using hierarchical logic (TAXCLASS → BORO → BLDGCL).  
  - Removed invalid rows (all-zero valuations).  

### 2. Variable Construction  
- **Value Ratios:** AVTOT/FULLVAL, AVLAND/FULLVAL → detect undervaluation or exemption misuse.  
- **Exemption Flags:** Binary indicators for unusual EXCD1/EXCD2 usage.  
- **Geometry Ratios:** BLDFRONT/LTFRONT, BLDDEPTH/LTDEPTH → catch physical mismatches.  
- **Policy-Based Ratios:** Validate against expected tax policies (e.g., 45% for Class 2).  

### 3. Dimensionality Reduction  
- Applied **PCA** to capture ~80% variance in **5 principal components**.  
- Reduced multicollinearity and enabled distance-based scoring.  

### 4. Anomaly Detection Models  
- **Minkowski Distance:** Multivariate distance in PCA space, flags extreme outliers.  
- **Autoencoder Error:** Neural network reconstruction loss, highlights non-linear irregularities.  
- **Composite Score:** Average of rank-based anomaly scores from both methods for robustness.  

---

## 📊 Results & Case Studies  
- **Top anomalies** included:  
  - Excessive exemptions (>100% of assessed value).  
  - Implausible valuation ratios (e.g., AVTOT/FULLVAL < 30%).  
  - Geometric inconsistencies (e.g., building dimensions exceeding lot size).  
  - Illogical tax liabilities far outside policy norms.  
- **Visualization:**  
  - Heatmaps of z-scores for top 20 anomalies.  
  - Clear variable contributions for interpretability.  

**Examples:**  
- Lot 2143902 (Bronx): Exemptions exceeded assessed value → likely miscoded.  
- Lot 4729180 (Queens): Building frontage larger than lot frontage → physical violation.  
- Lot 1221903 (Manhattan): Land-heavy valuation without exemptions → possible undervaluation.  

---

## 🛠️ Tools & Libraries  
- **Python:** pandas, numpy, matplotlib, seaborn  
- **scikit-learn:** PCA, standardization  
- **TensorFlow/Keras:** Autoencoder  
- **Custom scoring functions:** Minkowski distance, anomaly ranking  
- **Visualization:** heatmaps, anomaly contribution plots  
- **Jupyter Notebook:** reproducible analysis  

---

## 💡 Key Skills & Concepts  
- **Unsupervised Anomaly Detection**  
- **Fraud Analytics & Risk Modeling**  
- **Feature Engineering with Domain Logic**  
- **Dimensionality Reduction (PCA)**  
- **Autoencoders for Anomaly Scoring**  
- **Visualization & Interpretability for Auditors**  

---

## 🚀 Key Takeaways  
- Fraud detection requires **both domain expertise & machine learning**.  
- Combining **distance-based and reconstruction-based methods** improves robustness.  
- Interpretability (heatmaps, ratios) is critical for adoption in auditing workflows.  
- The framework is **scalable, replicable, and adaptable** to new fraud patterns.  

---

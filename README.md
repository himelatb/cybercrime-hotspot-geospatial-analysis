# Hotspots of Cybercrime: Identifying High-Risk Areas through Geospatial Analysis

MDA692 Data Analytics Capstone — Melbourne Institute of Technology
Industry Partner: BRR Technology Solutions

**Team:** Hedayetul Islam, Yaswanth Avula, Gopal Sapkota

## What this project does

An end-to-end geospatial analytics pipeline that turns raw cybersecurity event logs into cybercrime risk intelligence. It enriches attack records with IP geolocation, ASN context, country-level socioeconomic indicators, and raster population density, then applies spatial statistics, clustering, machine learning, and SHAP explainability to identify high-risk areas.

## Tools used

Python, Pandas, NumPy, GeoPandas, Rasterio, PySAL (Getis-Ord Gi*, Moran's I), Scikit-learn, XGBoost, LightGBM, CatBoost, SHAP, NetworkX, Folium, Matplotlib, Seaborn, Power BI.

## Methodology

1. Data cleaning and standardisation of cybersecurity event logs
2. IP geolocation via MaxMind GeoLite2 and ASN enrichment
3. Country socioeconomic and WorldPop raster population enrichment
4. Feature engineering including `final_hotspot_score` and the `High_Risk` target
5. Spatial analysis: DBSCAN, Getis-Ord Gi*, Moran's I, KDE
6. Machine learning: Random Forest, XGBoost, LightGBM, CatBoost, ensemble
7. Explainability: SHAP, correlation heatmap, network graph
8. Power BI dashboards for stakeholder communication

## Key results

| Model | Accuracy |
|---|---|
| **Random Forest** | **0.8524** |
| Ensemble | 0.7347 |
| XGBoost | 0.7170 |
| LightGBM | 0.6761 |
| CatBoost | 0.6709 |

- Random Forest was the best single model at **85.24% accuracy**
- Confusion matrix: 4,089 TN · 3,661 TP · 1,147 FP · 1,651 FN
- Getis-Ord Gi*: 2,201 of 36,200 records (5.55%) were significant hotspots
- Moran's I = 0.00339 (weak global spatial autocorrelation)
- Top SHAP features: `asn_risk_score`, `final_hotspot_score`, `asn_attack_count`, `cluster_risk`, `Anomaly Scores`

## Outputs

- Getis-Ord Gi* hotspot map
- Kernel Density Estimation map
- Folium interactive heat map
- Correlation heatmap
- Network graph of event entities
- SHAP summary plot
- Confusion matrix
- Three Power BI dashboard pages: Global Internet & Economic Review, CyberSecurity Attacks Analysis, Country Deep Dive

## Data sources

- Kaggle Cyber Security Attacks dataset
- MaxMind GeoLite2 (City + ASN)
- World Bank World Development Indicators
- WorldPop raster population data

Licensed and large datasets are not included in this repo. See the sources above to reproduce the pipeline.

## Limitations

IP geolocation is approximate and may reflect ISP infrastructure, VPNs, or cloud hosting regions rather than real attacker locations. Spatial outputs are hotspot screening results, not evidence of criminal activity at specific locations. Country-level indicators provide context, not causal evidence.

## Note

This is an academic capstone project (MDA692, Trimester 1, 2026). It is a working analytical prototype, not a production system.

# MOBILITY FRICTION MAPPING

**Seattle Accessibility Analysis**  
---

## SUMMARY

### The Challenge
Over 81,000 sidewalk accessibility barriers exist across Seattle's 50 neighborhoods, creating "friction" that restricts the independence and dignity of people with mobility challenges. These barriers aren't distributed equally; some neighborhoods face systematic, severe obstacles while others remain relatively accessible.

### The Mobility Friction Index (MFI)
We developed a quantitative measure (0-100 scale) that captures how difficult it is to move through Seattle's neighborhoods by combining:
- **Barrier Density** (30%): Total accessibility obstacles per area
- **Average Severity** (25%): How challenging barriers are to navigate
- **Permanence Ratio** (25%): Proportion of permanent vs. temporary barriers
- **Hotspot Clusters** (20%): Concentration of severe barrier clusters

### Findings

**Critical Inequity Revealed:**
- **Industrial District** has an MFI of 96.5 (Severe Friction) with 11,481 barriers
- **South Lake Union** has an MFI of 4.9 (Low Friction) with only 756 barriers
- **20x gap** between highest and lowest friction neighborhoods

**Priority Intervention Areas Identified:**
1. **Industrial District**: 169 accessibility hotspots, 99.5% permanent barriers
2. **Ravenna**: 30 hotspots, severe clustering in residential zones

**Machine Learning Insights:**
- Developed a 68.9% accurate severity prediction model
- Identified barrier type as the strongest predictor (40% importance)
- Geographic location accounts for 35% of predictive power

**Spatial Analysis:**
- 698 accessibility hotspots identified using clustering algorithms
- Largest hotspot in North Beacon Hill: 5,743 severe permanent barriers
- 99% of all barriers are permanent, indicating systemic design failures

---

## METHODOLOGY

### 1. Data Preparation & Features

**Categorical Encoding:**
- Label encoding for 7 barrier types
- Binary encoding for permanence status
- Neighborhood encoding for 50 areas

**Data Quality:**
- 2,251 missing severity values (2.7%) handled via ML-safe removal
- No missing geographic coordinates
- 99% of barriers classified as permanent

### 2. Severity Prediction using Machine Learning

**Model:**
- **Primary**: Random Forest Classifier (100 trees, max_depth=15)
- **Secondary**: Gradient Boosting Classifier (100 estimators)
- **Features**: 7 engineered spatial and categorical variables
- **Target**: Severity levels (1-5 scale)

**Performance Metrics:**
```
Random Forest Accuracy: 68.9%
Gradient Boosting Accuracy: 66.4%

Classification Report (Random Forest):
              precision    recall  f1-score   support
Severity 1       0.69      0.81      0.74      3,529
Severity 2       0.60      0.52      0.55      2,923
Severity 3       0.67      0.75      0.71      4,642
Severity 4       0.78      0.59      0.68      2,792
Severity 5       0.76      0.72      0.74      2,059

Weighted Avg     0.69      0.69      0.69     15,945
```

**Feature Importance Rankings:**
1. Barrier Type Encoded: 40.0%
2. Latitude: 19.1%
3. Longitude: 16.1%
4. Neighborhood Avg Severity: 8.8%
5. Barrier Density: 8.7%
6. Permanent Barrier %: 6.9%
7. Is Permanent: 0.4%

**Key Insights:**
- **Barrier type matters most**: CurbRamp and NoCurbRamp issues tend to be more severe
- **Geography is destiny**: 35% of predictive power comes from location alone
- **Neighborhood context significant**: Areas with high average severity predict individual barrier severity
- **Density reveals neglect**: High barrier density correlates with higher individual severities

### 3. Spatial Clustering: Accessibility Hotspots

**Algorithm**: DBSCAN (Density-Based Spatial Clustering)
- **Focus**: Severe (≥3) and permanent barriers only
- **Parameters**: 
  - epsilon = 0.001 degrees (~100 meters at Seattle latitude)
  - min_samples = 5 barriers per cluster
- **Input**: 46,923 severe permanent barriers

**Results:**
- **698 hotspot clusters** identified
- **1,493 isolated barriers** (noise points)
- Largest cluster: **5,743 barriers** in North Beacon Hill

**Top 10 Accessibility Hotspots:**

| Cluster | Barrier Count | Avg Severity | Neighborhood |
|---------|---------------|--------------|--------------|
| 3 | 5,743 | 3.42 | North Beacon Hill |
| 29 | 3,995 | 3.53 | Ravenna |
| 150 | 1,991 | 3.18 | Industrial District |
| 7 | 1,976 | 3.24 | Fremont |
| 274 | 1,944 | 3.31 | East Queen Anne |
| 14 | 1,843 | 3.39 | Whittier Heights |
| 2 | 1,409 | 3.28 | Minor |
| 43 | 933 | 3.51 | Ravenna |
| 148 | 874 | 3.15 | Industrial District |
| 462 | 783 | 3.44 | Wallingford |

### 4. Mobility Friction Index (MFI)

**Calculation Formula:**
```
MFI = (0.30 × norm_barrier_density) + 
      (0.25 × norm_avg_severity) + 
      (0.25 × norm_permanence_ratio) + 
      (0.20 × norm_hotspot_count)
```
Scaled to 0-100 range

**Component Normalization:**
- All components scaled using Min-Max normalization (0-1)
- Weighted combination reflects relative importance
- Final score categorized into 4 friction levels

**MFI Categories:**
- **Low Friction** (0-25): 5 neighborhoods
- **Moderate Friction** (25-50): 37 neighborhoods
- **High Friction** (50-75): 7 neighborhoods
- **Severe Friction** (75-100): 1 neighborhood

**Statistical Distribution:**
- Mean MFI: 40.7
- Median MFI: 41.3
- Std Dev: 14.2
- Range: 4.9 (South Lake Union) to 96.5 (Industrial District)

---

## KEY FINDINGS

### Finding 1: Severe Geographic Inequity
**Industrial District faces 20× more friction than South Lake Union**

| Neighborhood | MFI | Total Barriers | Avg Severity | Permanent % | Hotspots |
|--------------|-----|----------------|--------------|-------------|----------|
| Industrial District | 96.5 | 11,481 | 3.29 | 99.5% | 169 |
| South Lake Union | 4.9 | 756 | 2.63 | 92.3% | 0 |

**Interpretation**: This isn't random variation; it reveals systematic under-investment in accessibility infrastructure in industrial and working-class neighborhoods.

### Finding 2: Permanence Indicates Design Failure
**99% of barriers are permanent structural issues, not temporary obstacles**

- Only 771 barriers (0.9%) are temporary
- Permanent barriers require capital investment to fix
- This data shows accessibility wasn't designed in; it must be retrofitted

### Finding 3: Barrier Type Predicts Severity
**Different barrier types have distinct severity profiles**

Average Severity by Type:
1. NoSidewalk: 3.29
2. NoCurbRamp: 3.14
3. Obstacle: 3.01
4. SurfaceProblem: 2.97
5. CurbRamp: 2.76
6. Other: 2.60
7. Occlusion: 2.32

**Interpretation**: Complete absence of sidewalks (NoSidewalk) and missing curb ramps are the most severe accessibility barriers.

### Finding 4: Clustering Reveals Systemic Patterns
**Accessibility problems cluster, suggesting historic neglect zones**

- Top cluster has 5,743 barriers in concentrated area
- 698 distinct problematic zones identified
- Clusters align with industrial/commercial corridors and older residential areas

### Finding 5: Machine Learning Reveals Hidden Patterns
**68.9% accuracy in predicting severity from context**

- Model successfully identifies severity patterns
- Geographic features (lat/lon) contribute 35% of predictive power
- Barrier type alone predicts 40% of severity variation
- Enables proactive identification of high-risk areas

---

## PRIORITY INTERVENTION AREAS

### Criteria for Priority Classification:
1. MFI ≥ 60 (High to Severe Friction)
2. Permanent Barrier Ratio ≥ 80%
3. Multiple Accessibility Hotspots (≥2 clusters)

### Priority Neighborhoods (Immediate Action Required):

#### 1. Industrial District
- **MFI**: 96.5 (Severe Friction)
- **Total Barriers**: 11,481
- **Hotspot Clusters**: 169
- **Permanent Ratio**: 99.5%
- **Avg Severity**: 3.29

#### 2. Ravenna
- **MFI**: 65.6 (High Friction)
- **Total Barriers**: 5,282
- **Hotspot Clusters**: 30
- **Permanent Ratio**: 99.6%
- **Avg Severity**: 3.42

### Secondary Priority Areas (High Friction):
3. Whittier Heights (MFI: 59.2)
4. Mount Baker (MFI: 57.7)
5. Wallingford (MFI: 57.4)
6. View Ridge (MFI: 56.3)
7. Roosevelt (MFI: 52.2)

---

## CONCLUSION

This analysis reveals that **accessibility barriers in Seattle are not randomly distributed**; they cluster in specific neighborhoods, creating zones of "severe mobility friction" that systematically exclude people with disabilities from full participation in urban life.

The **Mobility Friction Index** provides city leaders with a quantitative, actionable tool to:
1. **Identify** the most urgent intervention areas
2. **Prioritize** limited accessibility improvement budgets
3. **Measure** progress toward equitable urban design
4. **Hold accountable** those responsible for accessible infrastructure

Our analysis shows that **Industrial District and Ravenna require immediate attention**, with MFI scores indicating severe and high friction respectively. The concentration of permanent barriers (99%+) in these areas demonstrates that accessibility wasn't designed into the built environment—it must be retrofitted at significant cost.

**The path forward is clear**: Use data-driven prioritization, invest in the neighborhoods with highest friction, and commit to measuring progress annually. Mobility is a civil right—this analysis provides the roadmap to making Seattle truly accessible for all.

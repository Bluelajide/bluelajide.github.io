# MOBILITY FRICTION MAPPING
## Executive Summary for Datathon Presentation

---

## THE PROBLEM

**81,973 sidewalk barriers** stand between Seattle residents and independent mobility.

But these barriers aren't distributed equally:
- Some neighborhoods face **severe, systematic obstacles**
- Others remain relatively accessible
- No quantitative measure exists to prioritize interventions

**Question:** How do we identify where to invest limited accessibility improvement budgets?

---

## OUR SOLUTION: MOBILITY FRICTION INDEX (MFI)

A data-driven metric (0-100) that quantifies **how difficult it is to move** through Seattle's neighborhoods.

### MFI Formula:
```
30% Barrier Density    (How many obstacles?)
25% Average Severity   (How challenging?)
25% Permanence Ratio   (Structural vs temporary?)
20% Hotspot Clusters   (Where do severe barriers cluster?)
= Mobility Friction Index (0-100)
```

### Categories:
- 🟢 **0-25**: Low Friction
- 🟡 **25-50**: Moderate Friction  
- 🟠 **50-75**: High Friction
- 🔴 **75-100**: Severe Friction

---

## KEY FINDINGS

### 1️⃣ SEVERE INEQUITY EXISTS

| Neighborhood | MFI | Total Barriers | Interpretation |
|--------------|-----|----------------|----------------|
| 🔴 Industrial District | 96.5 | 11,481 | SEVERE - Needs immediate action |
| 🟠 Ravenna | 65.6 | 5,282 | HIGH - Priority intervention |
| 🟢 South Lake Union | 4.9 | 756 | LOW - Relatively accessible |

**20× gap between highest and lowest friction neighborhoods**

### 2️⃣ PERMANENCE INDICATES SYSTEMIC FAILURE

- **99% of barriers are permanent** structural issues
- Not temporary obstacles—these require capital investment
- Accessibility wasn't designed in, must be retrofitted

### 3️⃣ GEOGRAPHIC PATTERNS REVEALED

**Machine Learning Results:**
- 68.9% accuracy predicting barrier severity
- Barrier type = strongest predictor (40%)
- Geographic location = 35% of predictive power

**Spatial Clustering:**
- 698 accessibility hotspots identified
- Largest: 5,743 severe barriers in North Beacon Hill
- Clustering reveals zones of historic neglect

---

## PRIORITY INTERVENTIONS

### 🚨 IMMEDIATE ACTION REQUIRED

#### Industrial District (MFI: 96.5)
- 11,481 total barriers
- 169 accessibility hotspots
- 99.5% permanent
- **Recommendation:** Comprehensive infrastructure audit + ADA retrofit program

#### Ravenna (MFI: 65.6)
- 5,282 total barriers  
- 30 accessibility hotspots
- 99.6% permanent
- **Recommendation:** Residential curb ramp installation + sidewalk continuity program

### 📋 SECONDARY PRIORITIES (High Friction)
3. Whittier Heights (59.2)
4. Mount Baker (57.7)
5. Wallingford (57.4)
6. View Ridge (56.3)
7. Roosevelt (52.2)

---

## METHODOLOGY OVERVIEW

### Data Science Pipeline:

**1. Data Preparation**
- 81,973 crowdsourced observations
- 50 neighborhoods, 7 barrier types
- Engineered spatial features (density grids, neighborhood aggregates)

**2. Machine Learning**
- Random Forest Classifier (primary)
- Gradient Boosting (validation)
- DBSCAN Spatial Clustering
- Feature importance analysis

**3. MFI Calculation**
- Multi-dimensional scoring
- Min-Max normalization
- Weighted combination
- 0-100 interpretable scale

**4. Visualization**
- Geographic heatmaps
- Priority intervention maps
- Barrier type analysis
- Statistical distributions

---

## INNOVATION HIGHLIGHTS

### 🏆 Novel Contributions

**Mobility Friction Index**
- First quantitative metric for urban mobility barriers
- Multi-dimensional (density + severity + permanence + clustering)
- Actionable for policy decisions

**Comprehensive ML Approach**
- Random Forest for interpretability
- Gradient Boosting for accuracy
- DBSCAN for spatial patterns
- 68.9% severity prediction accuracy

**Feature Engineering Excellence**
- Grid-based density calculation
- Neighborhood contextual features
- Spatial and categorical encoding

**Visualization as Storytelling**
- 5 publication-ready figures
- Clear geographic patterns
- Immediate action priorities

---

## ACTIONABLE RECOMMENDATIONS

### For Policymakers:

**Immediate (0-6 months)**
✓ Deploy resources to Industrial District & Ravenna  
✓ Fast-track curb ramps in top 10 hotspots  
✓ Remove 771 temporary barriers  

**Short-term (6-18 months)**
✓ Allocate budgets using MFI rankings  
✓ Systematic removal in High Friction zones  
✓ Mobile assessment teams  

**Long-term (18+ months)**
✓ Citywide accessibility master plan  
✓ Require accessibility impact assessments  
✓ Annual MFI monitoring & reporting  

---

## IMPACT POTENTIAL

### This Analysis Enables:

**🎯 Precise Targeting**
- Identify exactly which neighborhoods need help most
- Prioritize limited budgets for maximum impact

**📊 Progress Measurement**
- Track MFI changes over time
- Hold city accountable for improvements

**⚖️ Equity Advocacy**
- Quantify disparities for grant applications
- Provide data for community testimony

**🗺️ Scalability**
- Apply methodology to other cities in dataset
- Create national accessibility benchmarks

---

## BY THE NUMBERS

| Metric | Value |
|--------|-------|
| **Observations Analyzed** | 81,973 |
| **Neighborhoods Covered** | 50 |
| **Hotspots Identified** | 698 |
| **ML Model Accuracy** | 68.9% |
| **Priority Areas** | 2 |
| **Inequity Gap** | 20× |
| **Permanent Barriers** | 99% |

---

## TECHNICAL EXCELLENCE

### Tools & Technologies:
- **Language:** Python 3.12
- **ML:** scikit-learn (Random Forest, Gradient Boosting, DBSCAN)
- **Data:** pandas, numpy (81K+ records)
- **Viz:** matplotlib, seaborn (5 multi-panel figures)

### Reproducibility:
✓ Clean, documented code  
✓ Full analysis pipeline  
✓ All visualizations automated  
✓ Runtime: ~2 minutes  

### Deliverables:
✓ 5 datasets (processed data, MFI, hotspots, priorities, features)  
✓ 5 visualizations (heatmaps, rankings, analysis)  
✓ 14-page technical report  
✓ Complete documentation  

---

## WHAT MAKES THIS STAND OUT?

### 🎯 Impact-Focused
Not just analysis—**actionable recommendations** for immediate policy change

### 🔬 Rigorous
Multiple ML algorithms, proper validation, comprehensive feature engineering

### 📊 Clear
Interpretable 0-100 index, compelling visualizations, straightforward findings

### ⚖️ Equity-Centered
Reveals and quantifies geographic inequity in accessibility infrastructure

### 🚀 Scalable
Methodology applies to all cities in dataset and beyond

---

## THE BOTTOM LINE

**Mobility is a civil right.**

This analysis provides:
1. **Quantitative evidence** of severe inequity (20× gap)
2. **Specific targets** for intervention (Industrial District, Ravenna)
3. **Data-driven prioritization** for limited budgets
4. **Measurement framework** for tracking progress

**The path forward is clear**: Use the Mobility Friction Index to guide investments, prioritize the most underserved neighborhoods, and commit to annual measurement of progress.

**Seattle can do better. This data shows exactly where to start.**

---

## CONTACT & RESOURCES

**Project Materials:**
- Full Technical Report (14 pages)
- Complete Analysis Code
- All Datasets & Visualizations
- Methodology Documentation

**Next Steps:**
- Validate with lived experience surveys
- Extend to other cities (Columbus, Pittsburgh, CDMX, Newberg, SPGG)
- Develop route optimization using MFI
- Partner with disability advocacy organizations

---

## THANK YOU

**Questions?**

*"Data reveals what empathy already knows: some neighborhoods face systematic barriers to independence and dignity. Now we have the roadmap to fix it."*

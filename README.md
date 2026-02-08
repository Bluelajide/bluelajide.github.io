# Mobility Friction Mapping: Seattle Accessibility Analysis

## Overview

This project analyzes 81,973 crowdsourced sidewalk accessibility observations across Seattle to reveal **geographic inequities in urban mobility** and provide **data-driven recommendations** for improving accessibility infrastructure.

### Mobility Friction Index (MFI)

We developed a novel 0-100 metric that quantifies how difficult it is to move through Seattle's neighborhoods by combining:
- Barrier Density (30%)
- Average Severity (25%)  
- Permanence Ratio (25%)
- Hotspot Clusters (20%)

## Findings

### Severe Inequity Revealed
- **20× gap** between highest (Industrial District: 96.5) and lowest (South Lake Union: 4.9) friction neighborhoods
- **99% of barriers are permanent**, indicating systemic design failures
- **698 accessibility hotspots** identified with severe barrier clustering
- **2 neighborhoods require immediate intervention**: Industrial District and Ravenna

### Machine Learning Success
- **68.9% accuracy** in predicting barrier severity
- **Barrier type** is the strongest predictor (40% feature importance)
- **Geographic location** accounts for 35% of predictive power
- Model enables proactive identification of high-risk areas

## 📊 Deliverables

### Outputs
1. **processed_accessibility_data.csv** - Clean dataset with engineered features
2. **mobility_friction_index.csv** - MFI scores for all 50 neighborhoods
3. **accessibility_hotspots.csv** - 698 cluster locations with severity data
4. **priority_intervention_areas.csv** - Top 2 neighborhoods requiring immediate action
5. **model_feature_importance.csv** - ML model insights

### Visualizations
1. **seattle_accessibility_heatmap.png** - 4-panel geographic analysis
2. **mobility_friction_index_analysis.png** - MFI rankings and distribution
3. **barrier_type_analysis.png** - Barrier type composition and severity
4. **ml_model_insights.png** - Feature importance and model interpretation
5. **priority_intervention_map.png** - Geographic prioritization for action

### Documentation
- **PROJECT_REPORT.md** - Technical Report on Analysis
- **README.md** - This file

## 📊 Dataset Summary

**Source:** Seattle Accessibility Dataset

| Metric | Value |
|--------|-------|
| Total Observations | 81,973 |
| Neighborhoods | 50 |
| Barrier Types | 7 |
| Severe Barriers (≥3) | 47,466 |
| Permanent Barriers | 81,202 (99%) |
| Temporary Barriers | 771 (1%) |

**Barrier Type Distribution:**
1. CurbRamp: 27,175 (33%)
2. NoSidewalk: 19,133 (23%)
3. NoCurbRamp: 16,947 (21%)
4. SurfaceProblem: 12,681 (15%)
5. Obstacle: 5,693 (7%)
6. Occlusion: 253 (<1%)
7. Other: 91 (<1%)


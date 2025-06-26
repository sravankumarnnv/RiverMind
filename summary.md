Dataset Overview
The dataset contains a large collection of river-related measurements organized into four main categories:. Rainfall
. Turbidity
. Water Course Discharge
. Water Course Level
Total size:
10,802 CSV les containing approximately 50.5 million data rows
Data collected from 5,678 unique monitoring stations
Time span of approximately 15 years (December 2009 to June 2025)
Data Structure
Each category follows a consistent structure with four columns:. Timestamp (UTC): Date and time of measurement. Measurement Value: In appropriate unit for each category. Quality Code: Indicator of data reliability (10=best quality, -1=missing). Interpolation Type: Method used to interpret between measurement points
Metadata Files
Each data category includes a Metadata_Summary.csv le containing:
Owner information (primarily Icon Water Limited)
Station codes and IDs
Station names (short and long)
Geographic coordinates (latitude/longitude)
Measurement parameter
Date ranges for each station's data collection
Data Categories in Detail
1. Rainfall Data
2,243 les with 9.3 million rows
2,233 unique stations monitored
Page 2 of 19
Measurement unit: millimeters (mm)
Date range: 2009-12-31 to 2024-12-30 (5,478 days)
Typical le name pattern: w00002_41001701_Rainfall.csv
Readings typically recorded once daily at 14:00 UTC
Value statistics:
Minimum: -60.500 mm (likely measurement error)
Maximum: 178,540,641.600 mm (extreme outlier)
Average: 86.605 mm
Quality codes:
Best quality (10): 47.5%
Unknown quality (140): 12.6%
Estimated values (110): 9.2%
Missing values (-1): 6.0%
Interpolation method: Exclusively uses type 703
2. Turbidity Data
506 les with 6.7 million rows
505 unique stations monitored
Measurement unit: Nephelometric Turbidity Units (NTU)
Date range: 2009-12-31 to 2025-06-10 (5,640 days)
Typical le name pattern: w00002_41001701_Turbidity.csv
Readings typically recorded at 5-minute intervals
Value statistics:
Minimum: -214,748,364.800 NTU (extreme outlier)
Maximum: 1,000,000.000 NTU (extreme outlier)
Average: -4,355.840 NTU (skewed by outliers)
Quality codes:
Best quality (10): 79.7%
Unknown quality (140): 9.2%
Missing values (-1): 5.5%
Compromised (90): 2.9%
Interpolation methods:
Type 102 (linear interpolation): 83.1%
Type 603: 16.9%
3. Water Course Discharge Data
3,703 les with 16.3 million rows
3,647 unique stations monitored
Measurement unit: cubic meters per second (cumec)
Date range: 2009-12-31 to 2024-12-30 (5,478 days)
Typical le name pattern: w00002_41001701_WaterCourseDischarge.csv
Readings typically recorded daily
Value statistics:
Minimum: -2,330,208.133 cumec (extreme outlier)
Maximum: 140,561.238 cumec (extreme outlier)
Average: 10.584 cumec
Quality codes:
Page 3 of 19
Best quality (10): 41.7%
Unknown quality (140): 27.9%
Estimated values (110): 10.6%
Compromised (90): 9.5%
Interpolation method: Exclusively uses type 603
4. Water Course Level Data
4,350 les with 18.1 million rows
4,296 unique stations monitored
Measurement unit: meters (m)
Date range: 2009-12-31 to 2024-12-30 (5,478 days)
Typical le name pattern: w00002_41001701_WaterCourseLevel.csv
Value statistics:
Minimum: -91,301.727 m (extreme outlier)
Maximum: 1.25×10¹⁵ m (extreme outlier)
Average: 73,182,198.806 m (severely skewed by outliers)
Quality codes:
Best quality (10): 72.0%
Unknown quality (140): 12.6%
Compromised (90): 6.1%
Missing values (-1): 5.6%
Interpolation method: Exclusively uses type 603
Quality Code System
All data categories use a standardized quality code system:
10: Quality A - Best available data given technology and monitoring objectives
90: Quality B - Data compromised in its ability to represent the parameter
110: Quality C - Estimated data
140: Quality E - Unknown reliability
210: Quality F - Not release quality or contains missing data
-1: Missing data
Data Quality Issues
. Extreme outliers: All categories show unrealistic minimum/maximum values. Missing data: Between 5-6% of all readings across categories. Data quality variance: Best available quality (code 10) ranges from 41.7% to 79.7% depending on category
Key Observations
. The dataset represents a comprehensive long-term monitoring effort spanning 15+ years.. The high number of stations (5,678) provides excellent geographic coverage.. Despite some quality issues, most data (41.7-79.7%) is classied as high quality (code 10).. The presence of multiple measurement types enables multi-factor analysis of river behavior.
Page 4 of 19
. Each measurement category uses different recording frequencies:
Rainfall: Daily
Turbidity: 5-minute intervals
Water Course Discharge: Daily
Water Course Level: Daily
This dataset appears to be valuable for hydrological analysis, climate studies, and river safety applications, though data
cleaning to address outliers would be recommended before detailed analysis.
River Risk Assessment: Formula and ML Workow
Risk Score Formula Approaches
1. Composite Risk Index (Research-Backed)
Based on hydrological risk assessment literature, a commonly used approach is:
Risk Score = W₁×(Discharge_Risk) + W₂×(Level_Risk) + W₃×(Turbidity_Risk) + W₄×(Rainfall_Risk) 
Where each component is normalized (0-1) and weights (W) sum to 1.
2. Multi-Criteria Decision Analysis (MCDA)
Research from "Flash Flood Risk Assessment" (Kazakis et al., 2015) suggests:
3. Research-Backed Weights
According to "Flood Risk Assessment Using Multi-Criteria Analysis" (Fernández & Lutz, 2010):
# Individual risk components (0-10 scale) def calculate_component_risks(discharge, level, turbidity, rainfall):     # Discharge Risk (based on flow capacity)     discharge_risk = min(10, (discharge / design_capacity) * 10)          # Water Level Risk (flood threshold based)     level_risk = min(10, max(0, (level - safe_level) / (flood_level - safe_level) * 10))
         # Turbidity Risk (water quality impact)     turbidity_risk = min(10, (turbidity / 100) * 10)  # >100 NTU = high risk          # Rainfall Risk (intensity-based)     rainfall_risk = min(10, (rainfall / daily_threshold) * 10)          return discharge_risk, level_risk, turbidity_risk, rainfall_risk # Composite Risk Score risk_score = (0.35 * discharge_risk + 0.30 * level_risk +                0.20 * turbidity_risk + 0.15 * rainfall_risk) 

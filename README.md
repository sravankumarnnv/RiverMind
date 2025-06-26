# 🌊 RiverMind AI: River Safety Risk Prediction System

![Python](https://img.shields.io/badge/python-v3.8+-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)
![XGBoost](https://img.shields.io/badge/XGBoost-Latest-green.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

## 🎯 Project Overview

**RiverMind AI** is an advanced machine learning system that predicts river safety risks and flood conditions using 15+ years of Australian hydrological data. The system combines deep learning and explainable AI to provide real-time safety assessments and recommendations.

### 🏆 Key Achievements
- **94.2% R² accuracy** with XGBoost model
- **98.21% classification accuracy** for risk categories
- **50.5 million data points** from 5,678 monitoring stations
- **Real-time predictions** with interactive dashboard

## 🚀 Features

### 🧠 AI Models
- **LSTM Neural Network**: Temporal pattern recognition for time series forecasting
- **XGBoost**: High-accuracy risk classification with explainable features
- **Ensemble System**: Combines both models for robust predictions

### 📊 Data Processing
- **Multi-parameter Analysis**: Rainfall, Turbidity, Water Course Discharge, Water Course Level
- **Advanced Feature Engineering**: 18+ engineered features including temporal, statistical, and interaction terms
- **Quality Assessment**: Automated data cleaning and outlier detection

### 🎮 Interactive Interface
- **River Name Search**: Enter any Australian river name for instant analysis
- **Risk Assessment**: Clear Low/Moderate/High risk categorization
- **Safety Recommendations**: Actionable guidance based on current conditions
- **Visualization Dashboard**: 4-panel analysis with trends and parameters

## 📁 Project Structure

```
RiverMind/
├── RiverMind_AI_Implementation.ipynb  # Main implementation notebook
├── models/                            # Trained ML models (excluded from git)
├── results/                          # Analysis results (excluded from git)
├── plots/                           # Generated visualizations (excluded from git)
├── river_data/                      # Raw hydrological data (excluded from git)
├── station_profiles/               # Station metadata (excluded from git)
├── .gitignore                     # Git ignore configuration
└── README.md                     # This file
```

## 🛠️ Installation & Setup

### Prerequisites
- Python 3.8+
- 8GB+ RAM recommended
- GPU optional (for LSTM training)

### Install Dependencies
```bash
pip install pandas numpy matplotlib seaborn plotly
pip install tensorflow keras scikit-learn xgboost
pip install shap optuna folium geopandas
pip install statsmodels jupyter tqdm
```

### Quick Start
1. Clone the repository:
```bash
git clone https://github.com/yourusername/RiverMind.git
cd RiverMind
```

2. Open the main notebook:
```bash
jupyter notebook RiverMind_AI_Implementation.ipynb
```

3. Run the interactive demo:
```python
# In the notebook, execute:
simple_river_demo()
```

## 🎮 Usage Examples

### Interactive River Analysis
```python
# Analyze any Australian river
result = analyze_river_by_name("Brisbane River")
print(f"Risk Level: {result['risk_category']}")
print(f"Risk Score: {result['risk_score']:.3f}")
```

### Batch Station Analysis
```python
# Search stations by location
stations = station_manager.search_stations_by_location(-27.4698, 153.0251, radius_km=50)
for station in stations:
    analysis = analyze_station(station['station_id'])
```

## 📊 Model Performance

| Model | R² Score | Classification Accuracy | Use Case |
|-------|----------|------------------------|----------|
| XGBoost | 94.2% | 98.21% | Primary prediction engine |
| LSTM | Temporal | 85.3% | Time series forecasting |
| Ensemble | 94.8% | 98.5% | Production system |

## 🔬 Technical Methodology

### Data Sources
- **Bureau of Meteorology (Australia)**: 15+ years of hydrological data
- **5,678 monitoring stations**: Comprehensive geographic coverage
- **4 key parameters**: Rainfall, Turbidity, Discharge, Water Level

### Feature Engineering
- **Temporal Features**: Seasonal patterns, cyclical encoding
- **Statistical Features**: Rolling windows, percentiles, z-scores
- **Interaction Features**: Parameter ratios and combinations
- **Quality Metrics**: Data confidence and interpolation tracking

### Risk Assessment Framework
- **Low Risk** (0.0-0.3): Safe for normal activities
- **Moderate Risk** (0.3-0.7): Exercise caution
- **High Risk** (0.7-1.0): Avoid water activities

## 🛡️ Safety & Limitations

### ⚠️ Important Disclaimers
- This system provides **risk assessments**, not definitive safety guarantees
- Always check **current local conditions** before water activities
- **Emergency situations**: Contact local emergency services immediately
- **Model limitations**: Performance may vary in extreme weather events

### Data Requirements
- Requires recent station data for accurate predictions
- Performance dependent on station data quality
- Geographic coverage limited to Australian monitoring network

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for:
- Model improvements
- Additional data sources
- UI/UX enhancements
- Bug fixes and optimizations

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Australian Bureau of Meteorology** for comprehensive hydrological data
- **XGBoost and TensorFlow communities** for excellent ML frameworks
- **SHAP library** for explainable AI capabilities
- **Plotly and Matplotlib** for visualization tools

## 📞 Contact

For questions, suggestions, or collaboration opportunities, please open an issue on GitHub.

---

**⚠️ Note**: This repository excludes large data files (`river_data/`, `station_profiles/`, `models/`) to maintain reasonable repository size. Contact the maintainer for access to the complete dataset.

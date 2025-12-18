# NYC Taxi Trip Duration Prediction

A machine learning project to predict taxi trip duration in New York City using Ridge Regression with advanced feature engineering.

## 🚕 Project Overview

This project analyzes NYC taxi trip data to predict trip duration using various features including:
- Geographic coordinates (pickup/dropoff locations)
- Time-based features (hour, day of week, month)
- Distance calculations using Haversine formula
- Traffic patterns and proxy features

## 📊 Dataset

The dataset contains NYC taxi trip information with the following features:
- `id`: Unique identifier for each trip
- `vendor_id`: Taxi vendor (1 or 2)
- `pickup_datetime`: When the trip started
- `passenger_count`: Number of passengers
- `pickup_longitude`, `pickup_latitude`: Pickup coordinates
- `dropoff_longitude`, `dropoff_latitude`: Dropoff coordinates
- `store_and_fwd_flag`: Whether trip data was stored and forwarded
- `trip_duration`: Target variable (trip duration in seconds)

## 🔧 Features Engineering

### Distance Features
- **Haversine Distance**: Calculates the great circle distance between pickup and dropoff points
- **Euclidean Distance**: Alternative distance calculation method

### Time Features
- **Hour**: Hour of the day (0-23)
- **Day of Week**: Day of the week (0-6)
- **Month**: Month of the year (1-12)
- **Weekend Indicator**: Binary flag for weekend trips

### Traffic Features
- **Traffic Level**: Categorized traffic intensity based on average speed proxy
- **Average Speed Proxy**: Distance divided by hour-based factor

### Geographic Features
- **Manhattan Zones**: Binary indicators for pickup/dropoff in Manhattan area

## 🏗️ Model Architecture

- **Algorithm**: Ridge Regression with polynomial features
- **Polynomial Degree**: 4th degree polynomial expansion
- **Regularization**: Alpha = 1.0
- **Scaling**: MinMaxScaler for feature normalization

## 📈 Results

The model shows significant improvement with proper feature engineering:

```
===== Ridge Regression Evaluation =====
Train R²: [Improved from 0.05]
Validation R²: [Improved from 0.037]
Test R²: [Improved from 0.036]
```

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```

### Usage
```bash
python test.py
```

### File Structure
```
project-nyc-taxi-trip-duration/
├── test.py                 # Main model training script
├── split/                  # Data splits
│   ├── train.csv
│   ├── val.csv
│   └── test.csv
├── code_warmstart.py       # Initial code exploration
├── *.md                   # Documentation files
└── README.md              # This file
```

## 📝 Key Improvements Made

1. **Distance Calculation**: Added Haversine distance as the primary feature
2. **Time Features**: Extracted meaningful time-based features from datetime
3. **Polynomial Features**: Applied 4th-degree polynomial expansion
4. **Traffic Modeling**: Created proxy features for traffic patterns
5. **Geographic Zoning**: Added Manhattan area indicators
6. **Outlier Removal**: Applied IQR-based outlier detection on log-transformed target

## 🔍 Data Preprocessing

- **Log Transformation**: Applied `log1p()` to trip duration for better distribution
- **Outlier Removal**: Removed outliers using IQR method on training set only
- **Feature Scaling**: Applied MinMaxScaler for consistent feature ranges
- **Categorical Encoding**: Converted categorical variables to binary indicators

## 📊 Performance Analysis

The model performance improved significantly by:
- Adding distance as the primary predictor (highest correlation with trip duration)
- Including time-based features for traffic patterns
- Using polynomial features to capture non-linear relationships
- Proper scaling and preprocessing

## 🤝 Contributing

Feel free to contribute to this project by:
1. Forking the repository
2. Creating feature branches
3. Submitting pull requests
4. Reporting issues

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 👨‍💻 Author

**Haitham Ahmed**
- GitHub: [@haitham404](https://github.com/haitham404)

## 🙏 Acknowledgments

- NYC Taxi & Limousine Commission for the dataset
- scikit-learn community for the excellent machine learning library
- Python data science ecosystem contributors
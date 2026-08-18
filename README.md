# Traffic Management System Using Machine Learning

🚦 Traffic Management System Using Machine Learning
A machine-learning-based traffic prediction system that predicts the number of vehicles at a road junction using historical traffic patterns. The system uses Random Forest Regression along with time-based and historical traffic features to estimate traffic volume and classify the predicted traffic condition as Low, Medium, or High.

📌 Project Overview
Traffic congestion is a common problem in urban areas. Predicting traffic volume in advance can help traffic-management authorities make better decisions regarding signal timing and junction prioritization.

This project analyzes historical traffic data and uses a Random Forest Regressor to predict the expected number of vehicles at a junction.

The predicted traffic volume is then converted into a traffic level:

Low Traffic
Medium Traffic
High Traffic

A rule-based recommendation layer provides a corresponding traffic-management suggestion.

🎯 Objectives
Predict the number of vehicles at a junction.
Analyze traffic patterns according to time and junction.
Use historical traffic information for prediction.
Classify predicted traffic into Low, Medium, and High levels.
Provide simple traffic-management recommendations.
Develop an interactive interface for entering traffic information and viewing predictions.

📊 Dataset
The project uses the Traffic Prediction Dataset by fedesoriano from Kaggle.
Dataset Features
Feature	Description
DateTime	Date and time of the traffic observation
Junction	Junction identifier
Vehicles	Number of vehicles recorded
ID	Unique record identifier

The dataset contains 48,120 records from four junctions.

Kaggle Dataset
Traffic Prediction Dataset – Kaggle

🧠 Machine Learning Approach
The project uses Random Forest Regression to predict traffic volume.
Target Variable
Vehicles
Features Used

The following features are created from the original dataset:

Junction
Hour
Day
Month
Year
Weekday
Lag_1
Lag_24
Rolling_Mean_3
Feature Engineering

The DateTime column is transformed into:

Hour
Day
Month
Year
Weekday

Historical traffic features are also created:

Lag_1 — traffic from the previous hour
Lag_24 — traffic from approximately the same hour on the previous day
Rolling_Mean_3 — average traffic from the previous three observations
These features help the model learn recent and historical traffic patterns.

🔄 Project Workflow
Kaggle Traffic Dataset
        ↓
Data Loading
        ↓
Data Cleaning
        ↓
DateTime Feature Extraction
        ↓
Historical Feature Engineering
        ↓
Exploratory Data Analysis
        ↓
Feature Selection
        ↓
Train-Test Split
        ↓
Random Forest Regression
        ↓
Traffic Volume Prediction
        ↓
Low / Medium / High Classification
        ↓
Traffic Management Recommendation
        ↓
Web Interface

📈 Exploratory Data Analysis
The project analyzes traffic patterns based on:
Junction
Hour of the day
Day of the week
Historical traffic
Key observations
Junction 1 has the highest average traffic among the four junctions.
Traffic volume varies significantly throughout the day.
The busiest average hour in the analyzed dataset was around 7 PM.
Traffic volume is generally higher on weekdays than on weekends.

🤖 Model
Algorithm
Random Forest Regressor
Random Forest was selected because it can model nonlinear relationships between traffic-related features and vehicle volume and works well with structured/tabular data.

Model Configuration
Algorithm: Random Forest Regressor
Number of Trees: 100
Random State: 42

📊 Model Performance
The trained model achieved the following results on the test data:
Metric	Result
MAE	2.4059
RMSE	3.6710
R² Score	0.9680
Interpretation
MAE = 2.41 means the predicted vehicle count differs from the actual value by approximately 2.4 vehicles on average.
RMSE = 3.67 indicates relatively low prediction error.
R² = 0.968 indicates that the model explains approximately 96.8% of the variation in the target variable on this test split.

Note: The R² score should not be described as "96.8% accuracy." R² and classification accuracy are different metrics.

🔍 Feature Importance
The Random Forest model identified the following feature importance:
Feature	Importance
Lag_1	0.940651
Hour	0.015233
Lag_24	0.014955
Rolling_Mean_3	0.012003
Day	0.005378
Weekday	0.004510
Month	0.004125
Junction	0.002148
Year	0.000997

Lag_1 is the most influential feature, showing that recent traffic volume is strongly associated with the predicted traffic volume.

🚦 Traffic Classification
The predicted vehicle count is converted into traffic categories using thresholds derived from the traffic-volume distribution.

Predicted Vehicles
        ↓
  Traffic Thresholds
        ↓
 ┌──────┼──────┐
 ↓      ↓      ↓
Low   Medium   High
🚥 Traffic Management Recommendation

A rule-based layer converts the traffic level into a simple recommendation.

Example:

Low Traffic
→ Maintain normal signal timing

Medium Traffic
→ Moderately increase green-light duration

High Traffic
→ Increase green-light duration and prioritize the junction

The traffic recommendation layer is rule-based logic, while the traffic-volume prediction itself is performed using Machine Learning.

💻 Technologies Used
Programming Language
Python
Machine Learning
Scikit-learn
Random Forest Regression
Data Processing
Pandas
NumPy
Data Visualization
Matplotlib
Frontend
HTML
CSS
JavaScript
Web Framework
Flask
Development Environment
Google Colab
📁 Project Structure
Traffic-Management-System/
│
├── index.html
├── app.py
├── traffic_random_forest.pkl
├── traffic_prediction.ipynb
├── README.md
└── requirements.txt

The exact files may vary depending on how the project is organized in the GitHub repository.

▶️ How to Run
1. Clone the repository
git clone https://github.com/Prathiksha-66/Traffic-Management-System.git
2. Install dependencies
pip install pandas numpy matplotlib scikit-learn flask joblib
3. Run the Flask application
python app.py
4. Open the application

Open the local URL shown by Flask, usually:
http://127.0.0.1:5000

🖥️ Application Output
The web interface allows users to enter traffic-related information such as:
Junction
Hour
Day
Month
Year
Weekday
Previous-hour traffic
Previous-day traffic
Recent traffic average

The system then displays:
Predicted Vehicle Count
Traffic Level
Traffic Management Recommendation

🚀 Future Enhancements
Connect the frontend directly to the trained Random Forest model through Flask.
Add real-time traffic data using sensors or APIs.
Integrate CCTV-based vehicle detection using YOLO/OpenCV.
Develop adaptive traffic signal control.
Add live traffic dashboards and charts.
Deploy the application to a cloud platform.
Compare Random Forest with XGBoost, Gradient Boosting, and LSTM models.
Use chronological time-series validation for more realistic future forecasting.

👩‍💻 Author
Prathiksha Acharya
Computer Science and Engineering Student

GitHub: Prathiksha-66

📄 License
This project is developed for educational and academic purposes.

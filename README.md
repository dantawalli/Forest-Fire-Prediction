# Forest Fire Predictor 🔥🌲

This project is a **Forest Fire Prediction** web application built using **Flask** and a **Machine Learning** model, which is deployed via a simple and user-friendly interface. The application predicts the likelihood of forest fires based on environmental features, such as temperature, humidity, wind speed, and others.

The prediction is powered by a **Ridge Regression** model, which was trained on historical forest fire data. The app also uses a **Standard Scaler** to ensure the input features are appropriately scaled before prediction.

## Table of Contents
- [Features](#features)
- [Project Overview](#project-overview)
- [Installation](#installation)
- [Usage](#usage)
- [Model](#model)
- [API Endpoints](#api-endpoints)
- [Contributing](#contributing)
- [License](#license)

## Features
- **Ridge Regression Model**: Predicts forest fire risks based on weather and environmental factors.
- **Flask Web Framework**: User-friendly interface for submitting data and receiving predictions.
- **Real-time Prediction**: Input environmental data such as temperature, wind speed, and relative humidity to receive real-time fire risk predictions.
- **Scalable Codebase**: Expandable with additional features or alternative models for better prediction accuracy.

## Project Overview
The **Forest Fire Predictor** is designed to provide an early warning system by predicting the risk of forest fires. It takes into account various environmental factors, scales the data appropriately using a pre-trained **StandardScaler**, and then predicts the likelihood of a forest fire using a **Ridge Regression** model.

This application can be useful for fire departments, environmental agencies, and forest management systems to monitor fire risks based on real-time data.

## Installation

### Prerequisites
- **Python 3.x**
- **Flask**
- **scikit-learn**
- **Pandas**
- **NumPy**

### Steps to Run Locally

1. **Clone the Repository**
   ```bash
   git clone https://github.com/dantawalli/Forest-Fire-Prediction.git
   cd Forest-Fire-Prediction
   ```

2. **Create a Virtual Environment**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # For Windows: venv\Scripts\activate
   ```

3. **Install the Required Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Download or Add Pre-trained Model Files**
   Ensure that you have the following pre-trained model files in the `models/` directory:
   - `ridge.pkl`: The Ridge Regressor model.
   - `scaler.pkl`: The Standard Scaler for preprocessing input features.

5. **Run the Flask Application**
   ```bash
   export FLASK_APP=app.py  # For Windows: set FLASK_APP=app.py
   flask run
   ```

6. **Access the Application**
   Go to `http://127.0.0.1:5000/` in your web browser to access the application.

## Usage

### User Interface
The web application provides a form for inputting environmental data. Upon submission, the app scales the data using a pre-trained **Standard Scaler** and predicts the forest fire risk using a **Ridge Regression** model.

### Input Features:
1. **Temperature**: The ambient temperature in Celsius.
2. **RH**: Relative Humidity as a percentage.
3. **Ws**: Wind speed in km/h.
4. **Rain**: Rainfall in mm.
5. **FFMC**: Fine Fuel Moisture Code (a fire index).
6. **DMC**: Duff Moisture Code (a fire index).
7. **ISI**: Initial Spread Index.
8. **Classes**: Fire danger classification.
9. **Region**: Numerical code for the geographic region.

### Output
The output is a prediction of the forest fire risk, displayed on a results page.

### Example Usage:
1. Input the values for temperature, humidity, wind speed, etc.
2. Click the **Submit** button.
3. The result (fire risk prediction) will be displayed on the page.

### REST API (Optional)
The application also provides an API endpoint (`/predictdata`) for submitting data and receiving predictions in real time.

#### Example Request:
```bash
POST /predictdata
Content-Type: application/x-www-form-urlencoded

{
  "Temperature": 30,
  "RH": 35,
  "Ws": 15,
  "Rain": 0,
  "FFMC": 85,
  "DMC": 40,
  "ISI": 5,
  "Classes": 1,
  "Region": 3
}
```

#### Example Response:
```json
{
  "fire_risk": 0.543  # (or some other prediction score)
}
```

## Model
The **Ridge Regression** model used in this project was trained using a dataset of historical forest fire data. The input data is first scaled using a **Standard Scaler** before being passed into the model.

### Model Training
1. **Ridge Regression**: Chosen for its ability to handle multicollinearity in the dataset and provide more stable predictions.
2. **Feature Scaling**: Preprocessed using a **Standard Scaler** to normalize all input features.
3. **Model Performance**: The Ridge Regression model achieves an accuracy of X% on the test dataset (you can modify this part based on your model's performance).

If you'd like to modify or retrain the model, refer to the Jupyter notebook `train_model.ipynb` in the `model/` directory.

## API Endpoints

| Method | Endpoint         | Description                            |
|--------|------------------|----------------------------------------|
| GET    | `/`              | Displays the homepage                  |
| POST   | `/predictdata`   | Accepts form data and returns a prediction  |

## Contributing
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -am 'Add some feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Open a pull request.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

# DPS-AI-Model


## **SARIMA-Based Forecasting API**

This project is a Flask-based API that provides predictions using time-series forecasting models. It allows users to input a specific year and month and returns the predicted value for that period. 

---

## **Features**
- Implements **SARIMA**, **Prophet**, and a **Hybrid model** (combining both SARIMA and Prophet) for forecasting.
- Provides a RESTful API to interact with the forecasting system.
- Error metrics for each model are stored in respective folders as `.txt` files, along with their corresponding plots.
- **SARIMA** was found to perform the best with minor parameter tuning.

---

## **Dataset**

The dataset used for training and testing the models is available at the following link:

[Monatszahlen Verkehrsunfälle Dataset](https://opendata.muenchen.de/en/dataset/monatszahlen-verkehrsunfaelle/resource/40094bd6-f82d-4979-949b-26c8dc00b9a7)

### **Preprocessing Steps**
1. Filtered data for:
   - `AUSPRAEGUNG = 'insgesamt'`
   - `MONATSZAHL = 'Alkoholunfälle'`
2. Removed rows with `MONAT = 'Summe'`.
3. Ensured valid numeric values in the `MONAT` column.
4. Converted the `MONAT` column to a datetime format and set it as the index.

---

## **Installation**

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/medss19/DPS-AI-Model
   cd DPS-AI-Model
   ```

2. **Set Up Virtual Environment (Optional but Recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate  # For Linux/Mac
   venv\Scripts\activate     # For Windows
   ```

3. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Prepare Dataset:**
   - Place the dataset (`subset.pkl`) in the `datasets/` directory.

5. **Run the API:**
   ```bash
   python app.py
   ```

   The API will be accessible at `http://127.0.0.1:5000`.

---

## **API Endpoints**

### **POST /predict**

**Description:** Accepts a JSON payload with the year and month and returns the prediction.

#### **Request Example:**
```json
{
  "year": 2020,
  "month": 10
}
```

#### **Response Example:**
```json
{
  "prediction": 39.022958706306206
}
```

---

## **Model Comparison**

Three models were evaluated: **SARIMA**, **Prophet**, and a **Hybrid model** (combination of SARIMA and Prophet). The error metrics for each model are as follows:

### **SARIMA:**
- Mean Absolute Error (MAE): **8.33**
- Mean Squared Error (MSE): **80.14**
- Root Mean Squared Error (RMSE): **8.95**
- Mean Absolute Percentage Error (MAPE): **35.30%**

### **Prophet:**
- Mean Absolute Error (MAE): **9.43**
- Root Mean Squared Error (RMSE): **11.05**

### **Hybrid Model:**
- Mean Absolute Error (MAE): **8.42**
- Root Mean Squared Error (RMSE): **9.17**

**Conclusion:** SARIMA performed the best among the three models with minimal parameter tuning.

### **Error Metrics and Plots**
- Each model’s error metrics are stored in their respective folders as `.txt` files.
- Visual plots showcasing the performance of the models are also included in the same folders.

---

## **Project Structure**
```
DPS-AI-Model/
│
├── app.py                 # Flask API
├── Sarima/
│   ├── sarima.py          # SARIMA model training and prediction logic
│
├── Prophet/
│   ├── prophet_model.py   # Prophet model training and prediction logic
│
├── Hybrid/
│   ├── hybrid_model.py    # Hybrid model combining SARIMA and Prophet
│
├── datasets/
│   └── subset.pkl         # Dataset for training and testing
│
├── requirements.txt       # Project dependencies
└── README.md              # Project documentation
```

---

## **How It Works**
1. The dataset is preprocessed and fed into the SARIMA, Prophet, and Hybrid models.
2. Optimized parameters for the SARIMA model are identified through a grid search.
3. Forecasts are generated based on user-provided year and month inputs.

---

## **Technologies Used**
- **Python**: Core programming language.
- **Flask**: API development.
- **SARIMAX (Statsmodels)**: Time-series forecasting.
- **Prophet**: Facebook Prophet for forecasting.
- **Pandas**: Data manipulation and preprocessing.
- **NumPy**: Numerical computations.
- **Matplotlib**: Visualization.

---

## **Future Improvements**
- Add support for dynamic dataset uploads.
- Explore additional models like ARIMA and LSTM.
- Include endpoints for batch predictions.
- Improve the hybrid model with advanced integration techniques.
- Add a front-end dashboard for better visualization.

---

## **Contributing**
Contributions are welcome! Please fork the repository and submit a pull request for any enhancements.

---


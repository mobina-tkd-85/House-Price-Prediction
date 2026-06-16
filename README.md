# 🏡 House Price Prediction with Machine Learning

## About the Project

This project builds a robust machine learning model to estimate housing prices using a modern, feature-rich dataset from Kaggle. The model leverages the powerful **CatBoostRegressor** algorithm, combined with thorough data preprocessing, exploratory analysis, and hyperparameter tuning. The final model is deployed via a Flask web application, making it easy for users to input property features and receive instant price predictions.

Unlike older implementations that rely on the deprecated Boston Housing dataset, this project uses an up‑to‑date Kaggle dataset — the **House Prices: Advanced Regression Techniques** dataset — which includes more relevant features and better reflects current real‑estate dynamics. The project is a fork of an existing repository, but I have significantly modified the data pipeline, feature engineering, and model configuration to suit this new dataset.

![Prediction Interface](https://github.com/KalyanMurapaka45/House-Price-Prediction/blob/main/Output/Screenshot%202023-05-16%20041823.png)

---

### Built With

- **Flask** – web framework for deployment  
- **pandas** & **numpy** – data manipulation  
- **matplotlib** – visualization  
- **scikit-learn** – preprocessing & metrics  
- **catboost** – gradient boosting engine  
- **gunicorn** – production WSGI server  

---

## Getting Started

Follow these steps to set up the project locally.

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/House-Price-Prediction.git
   cd House-Price-Prediction
   ```

2. **Install required libraries**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the Jupyter notebook** (optional)
   - Open and execute `HousePricePrediction.ipynb` to train the model.
   - This will generate the pickle files (`housepred.pkl` and `scaler.pkl`) needed for deployment.

4. **Launch the Flask app**
   ```bash
   python app.py
   ```
   The app will be available at `http://127.0.0.1:5000`.

---

## Dataset Description

I have replaced the outdated Boston Housing dataset with the **Kaggle House Prices** dataset, which contains 79 explanatory variables describing (almost) every aspect of residential homes in Ames, Iowa. This dataset is widely used for regression competitions and provides a much richer learning experience.

### Key Features (subset used in this project)

| Feature             | Description                                                      |
|---------------------|------------------------------------------------------------------|
| **bedrooms**        | Number of bedrooms above grade                                   |
| **bathrooms**       | Number of bathrooms (full + half)                                |
| **sqft_living**     | Living area in square feet                                       |
| **sqft_lot**        | Lot area in square feet                                          |
| **floors**          | Number of floors (e.g., 1.0, 1.5, 2.0)                          |
| **condition**       | Overall condition of the house (1–5)                            |
| **grade**           | Overall grade given to the housing unit (1–13)                  |
| **sqft_above**      | Square footage of the house above ground                        |
| **yr_built**        | Year the house was built                                         |
| **zipcode**         | Postal code / area code                                          |
| **lat**             | Latitude coordinate                                              |
| **long**            | Longitude coordinate                                             |
| **sqft_living15**   | Living area of the 15 nearest neighbors (avg)                   |
| **sqft_lot15**      | Lot area of the 15 nearest neighbors (avg)                      |

> **Target variable**: `price` – the sale price of the house in USD.

The dataset is sourced from Kaggle's House Prices competition. I have preprocessed it by handling missing values, encoding categorical variables, and scaling numerical features to ensure optimal model performance.

---

## Data Preprocessing

- **Handling missing values**: Imputation using median/mode or domain-specific defaults.
- **Feature encoding**: One‑hot encoding for categorical variables.
- **Standardization**: Numerical features are scaled using `StandardScaler` to bring them to a similar magnitude.
- **Train‑test split**: 80% training, 20% testing (stratified where applicable).

All preprocessing steps are stored in a `scaler.pkl` file to apply the same transformations during inference.

---

## Model Training & Evaluation

The core algorithm is **CatBoostRegressor**, chosen for its ability to handle categorical features natively and its robust performance with minimal tuning.

- **Hyperparameter tuning**: Performed using `RandomizedSearchCV` with 5‑fold cross‑validation to find the best combination of learning rate, depth, and regularization parameters.
- **Evaluation metric**: R‑squared (coefficient of determination) on the test set.
- **Final model**: Saved as `housepred.pkl` for deployment.

---

## Deployment

The Flask web application (`app.py`) loads the trained model and scaler, exposes a user‑friendly HTML interface, and returns predictions in real time. Users can input the 14 key features (as listed above) and receive an estimated price instantly.

The application is container‑ready and can be deployed on platforms like Heroku, AWS, or any standard Python‑hosting service using Gunicorn.

---

## Contributing

Contributions are welcome! If you have suggestions for improvements, please fork the repository and create a pull request. You can also open an issue with the "enhancement" tag.

1. Fork the Project  
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)  
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)  
4. Push to the Branch (`git push origin feature/AmazingFeature`)  
5. Open a Pull Request  

Don't forget to give the project a ⭐ — it helps others discover it!

---

## License

Distributed under the GNU General Public License v3.0. See `LICENSE.txt` for more information.

---

## Acknowledgements

- This project was inspired by the Kaggle competition *House Prices: Advanced Regression Techniques*.
- Special thanks to the open‑source Python ecosystem — pandas, scikit‑learn, CatBoost, and Flask — for making this work possible.
- The original repository by KalyanMurapaka45 served as a foundation; I have since adapted it to use a modern dataset and enhanced the preprocessing pipeline.


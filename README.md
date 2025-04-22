# Hotel Booking Cancellation Prediction

Goal: Predict whether a hotel booking will be canceled based on customer and booking features.

## Dataset
- Source: [Kaggle](https://www.kaggle.com/datasets/ahsan81/hotel-reservations-classification-dataset)
- Size: ~30k records, 18 columns

## Tools Used
- Python (pandas, scikit-learn, matplotlib, seaborn)
- Jupyter Notebook

## Key Features
- `booking_status` (target)
- `no_of_adults`, `lead_time`, `room_type_reserved`, etc.

## Models
- Logistic Regression
- Decision Tree
- Random Forest

## Results
- Best model: Random Forest, 88% accuracy
- Feature importance: Lead time, room type, and number of previous cancellations were top predictors

## Next Steps
- Deploy as a web app with Streamlit
- Try hyperparameter tuning

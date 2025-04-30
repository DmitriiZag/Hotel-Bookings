# Hotel Booking Cancellation Prediction

Predict whether a hotel booking will be canceled based on customer behavior and reservation details.

---

## 📂 Dataset

- **Source:** [Kaggle](https://www.kaggle.com/datasets/ahsan81/hotel-reservations-classification-dataset)
- **Size:** ~36,000 rows, 19 features
- **Target Variable:** `booking_status` (Canceled / Not Canceled)

---

## 📘 Data Dictionary (Selected Features)

| Feature | Description |
|--------|-------------|
| `booking_ID` | Unique identifier for each booking |
| `no_of_adults` | Number of adults |
| `no_of_children` | Number of children |
| `no_of_weekend_nights` | Weekend nights booked |
| `no_of_week_nights` | Weekday nights booked |
| `type_of_meal_plan` | Meal plan selected |
| `required_car_parking_space` | Binary flag for parking space |
| `room_type_reserved` | Encoded room type |
| `lead_time` | Days between booking and arrival |
| `arrival_year/month/date` | Date of arrival |
| `market_segment_type` | Source of booking |
| `repeated_guest` | Whether the guest is returning |
| `no_of_previous_cancellations` | Prior cancellations by the guest |
| `avg_price_per_room` | Price per night in euros |
| `no_of_special_requests` | Special requests count |
| `booking_status` | Target label: Canceled or Not Canceled |

---

## 🧰 Tools & Technologies

- **Language:** Python
- **Libraries:** `pandas`, `scikit-learn`, `matplotlib`, `seaborn`, `scipy`
- **Environment:** Jupyter Notebook

---

## ⚙️ Preprocessing & Exploration

- Right-skewed variables normalized using square root transformation + z-score scaling
- One-hot encoding applied to categorical variables
- Outliers retained to preserve important behaviors
- Class imbalance identified (fewer canceled bookings)

---

## 🔍 Key Observations

- Average booking lead time: ~57 days
- Peak booking season: Summer months
- Most stays are short (1 night), common for business or local travel
- Booking behaviors vary — e.g., long lead times or high special requests = higher cancel likelihood

---

## 🤖 Models Evaluated

| Model               | Accuracy | AUC   | Precision (Canceled) | Recall (Canceled) | Kappa | Balanced Accuracy |
|--------------------|----------|-------|-----------------------|--------------------|-------|--------------------|
| Logistic Regression| 84%      | 0.83  | 0.76                  | 0.70               | 0.59  | 77.8%              |
| Decision Tree       | 78.4%    | 0.81  | 0.72                  | 0.65               | 0.53  | 75.6%              |
| **kNN (Best)**     | **84.8%**| **0.90** | **0.79**              | **0.73**           | **0.65** | **81.9%**        |
| Random Forest       | 88%      | 0.87  | 0.81                  | 0.75               | 0.69  | 83.7%              |

> 🔥 **Best overall model:** k-Nearest Neighbors (kNN)  
> ✅ Best AUC and balance between precision and recall  
> 📌 Top predictors: `lead_time`, `room_type_reserved`, `no_of_previous_cancellations`

---

## 📈 Visuals & Evaluation

- Confusion matrices and ROC curves for all models
- PCA visualization of cluster separability
- KMeans and Hierarchical clustering as unsupervised benchmarks

---

## 📊 Evaluation Summary

An **AUC of 0.901** from the kNN model indicates excellent ability to distinguish between canceled and non-canceled bookings. This means there’s a 90.1% chance the model ranks a randomly selected canceled booking higher than a non-canceled one.

- **Precision (0.7923):** When the model predicts a cancellation, it's correct ~79% of the time — crucial when false positives are costly.
- **Recall (0.7330):** The model correctly identifies ~73% of all actual cancellations — important when false negatives are costly.
- **Kappa (0.65):** Stronger agreement than chance, showing reliable classification beyond class imbalance.

Compared to the Decision Tree:
- The kNN model performs significantly better in terms of **accuracy**, **AUC**, **specificity**, and **balanced accuracy**.
- Its **specificity of 90.5%** means it's very strong at detecting non-canceled bookings.
- The **Decision Tree** had lower balanced accuracy and more bias toward the majority class.

---

## 💡 Final Insights

This project highlights the power of machine learning to improve operational efficiency in hospitality. The kNN model offers an excellent trade-off between precision and recall, making it ideal for proactive cancellation risk management.

Booking lead time, room type, and past cancellation behavior are critical signals. Understanding and acting on these signals can help hotels reduce losses, optimize revenue, and tailor their marketing strategies around real customer behavior.

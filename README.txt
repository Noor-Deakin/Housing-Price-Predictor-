Melbourne Housing Price Predictor
Regression pipeline to predict residential property prices across three Melbourne suburbs — Point Cook, 
Williams Landing and Tarneit. Includes manual data collection, EDA, model comparison and a live Gradio web app.

Overview
Predicts sold property prices (AUD) using features available at the time of listing. Data was manually collected from realestate.com.au rather than using a pre-existing dataset, making this a real end-to-end ML project.

Dataset
-Source: Manually scraped from [realestate.com.au](https://www.realestate.com.au) (Sold listings)
-Size:151 properties — minimum 50 per suburb
-Features: Property type, bedrooms, bathrooms, land size, car spaces, distance to CBD, schools within 1km, study room, 
sale date
-Target: Sold price (AUD)

What the Pipeline Does

- Cleaned and standardised raw listing data (price strings, date parsing, land size imputation)
- One-hot encoded suburb and property type
- Engineered features: sold month/year, schools nearby, distance to CBD
- Visualised price distributions, suburb comparisons, correlation heatmap and price trends over time
- Trained and compared three models using 5-fold cross validation

---

Results

| Model | MAE | RMSE | R² |
|---|---|---|---|
| Linear Regression | $78,055 | $129,638 | 0.49 |
| XGBoost | $53,637 | $76,170 | 0.87 |
| Random Forest | $48,703 | $71,903 | 0.88 |

Random Forest was the best performing model and was used for deployment.


LLM Benchmark
ChatGPT was tested on one held-out fold (30 properties) as a benchmark comparison. While it produced strong numbers (R² = 0.99), this was attributed to its pre-existing knowledge of Melbourne's property market rather than learning from the dataset — making it unsuitable for transparent, scalable prediction.

Web App
A Gradio web app allows users to input property details and receive an instant price prediction. Inputs include suburb, property type, bedrooms, bathrooms, land size, car spaces, schools nearby and sale date.

Tech Stack
Python, Pandas, Scikit-learn, XGBoost, Gradio, Matplotlib, Seaborn, Jupyter

Author
Gurnoor Singh — Deakin University, Bachelor of Computer Science

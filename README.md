# Video Game Sales Prediction using Machine Learning

A college project that predicts the global sales of video games using
Linear Regression, Decision Tree and Random Forest.

## Dataset
Video Game Sales dataset (`vgsales.csv`). Sales are in millions of copies.

## What this project does
- Cleans the dataset and explores it with graphs (EDA)
- Trains 3 regression models using the same 80/20 split
- Compares models using MAE, MSE, RMSE and R2
- Checks consistency with 5-fold cross-validation
- Tunes Decision Tree and Random Forest using GridSearchCV (3-fold)
- Converts sales into Low (<1M) and High (>=1M) to build confusion matrices
- Saves the best model

## Features and target
- Input features: Platform, Genre, Year, Publisher
- Target: Global_Sales

## How to run
1. Open `notebooks/video_game_sales_prediction.ipynb` in Google Colab
2. Upload `vgsales.csv` when asked
3. Run all cells from top to bottom

To run locally, install the libraries first: `pip install -r requirements.txt`

## Folder structure
- `data/` - original and cleaned dataset
- `docs/` - project guide PDF
- `notebooks/` - Colab notebook
- `images/` - EDA graphs
- `results/` - metrics tables and confusion matrices
- `models/` - saved final model
- `requirements.txt` - Python libraries needed

## Results

### Regression metrics

| Model | MAE | MSE | RMSE | R2 |
|---|---|---|---|---|
| Linear Regression | 0.5661 | 3.9168 | 1.9791 | 0.0833 |
| Decision Tree | 0.5863 | 4.7211 | 2.1728 | -0.1050 |
| Random Forest | 0.5529 | 4.2369 | 2.0584 | 0.0083 |
| Decision Tree (Tuned) | 0.5388 | 3.8530 | 1.9629 | 0.0982 |
| Random Forest (Tuned) | 0.5267 | 3.8611 | 1.9650 | 0.0963 |

### Confusion matrix metrics (Low < 1M, High >= 1M)

| Model | Accuracy | Precision (High) | Recall (High) | F1 (High) |
|---|---|---|---|---|
| Linear Regression | 0.8536 | 0.3747 | 0.3610 | 0.3677 |
| Decision Tree | 0.8487 | 0.3641 | 0.3792 | 0.3715 |
| Random Forest | 0.8533 | 0.3848 | 0.4078 | 0.3960 |
| Decision Tree (Tuned) | 0.8567 | 0.3985 | 0.4234 | 0.4106 |
| Random Forest (Tuned) | 0.8641 | 0.4226 | 0.4182 | 0.4204 |

### Final model
Decision Tree (Tuned) was selected because it has the lowest RMSE (1.9629) and the highest R2 (0.0982).

Random Forest (Tuned) has the lowest MAE (0.5267) and the best accuracy (0.8641), and its RMSE and R2 are very close.

### Limitations
The R2 scores are low (around 0.1), so the models explain only a small part of the variation in sales. This is expected because only Platform, Genre, Year and Publisher are used, and most games have low sales while a few sell very high. Adding more features or transforming the sales values could improve the results.

## Author
Subhajit Mukherjee, BCA
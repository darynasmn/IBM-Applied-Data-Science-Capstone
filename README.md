# SpaceX Falcon 9 First Stage Landing Prediction

**IBM Applied Data Science Capstone — Final Project**

Author: [darynasmn](https://github.com/darynasmn)

---

## Overview

SpaceX advertises Falcon 9 rocket launches on its website with a cost of **62 million dollars**, while other providers cost upward of **165 million dollars** per launch. Much of the savings comes from the fact that SpaceX can reuse the first stage.

Therefore, if we can determine whether the first stage will land successfully, we can estimate the cost of a launch. This information can be used by an alternate company that wants to bid against SpaceX for a rocket launch.

This project uses public data and machine learning to predict whether the Falcon 9 first stage will land successfully. It walks through the full data science lifecycle: **data collection → data wrangling → exploratory data analysis (visual & SQL) → interactive visual analytics (map & dashboard) → predictive modeling**.

---

## Repository Structure

| File | Description |
|---|---|
| `1. jupyter-labs-spacex-data-collection-api.ipynb` | Collects launch data from the SpaceX REST API (`v4/launches/past`) |
| `2. jupyter-labs-webscraping.ipynb` | Scrapes the Falcon 9 & Falcon Heavy launch tables from Wikipedia with BeautifulSoup |
| `3. labs-jupyter-spacex-Data wrangling.ipynb` | Cleans the data and engineers the binary landing outcome label (`Class`) |
| `4. jupyter-labs-eda-sql-coursera_sqllite.ipynb` | Exploratory data analysis using SQL queries against a SQLite database |
| `5. edadataviz.ipynb` | Exploratory data analysis using Matplotlib / Seaborn visualizations |
| `6. lab_jupyter_launch_site_location.ipynb` | Interactive Folium map of launch sites, outcomes, and proximities |
| `7. SpaceX_Machine_Learning_Prediction_Part_5.ipynb` | Builds, tunes, and evaluates four classification models |
| `spacex-dash-app.py` | Interactive Plotly Dash dashboard for launch records |
| `spacex_dash_app_screenshot.png` | Screenshot of the running dashboard |
| `spacex_launch_geo.csv` | Launch records with site coordinates (used for the map & EDA) |
| `spacex_web_scraped.csv` | Raw launch data scraped from Wikipedia |
| `my_data1.db` | SQLite database used for the SQL-based EDA notebook |

---

## Methodology

1. **Data Collection** — Combined data from the SpaceX REST API (booster, payload, launch site, core details) with historical launch records scraped from Wikipedia.
2. **Data Wrangling** — Cleaned missing values, standardized categorical fields, and engineered a binary `Class` label (`1` = successful landing, `0` = failed landing).
3. **Exploratory Data Analysis** — Explored relationships between flight number, payload mass, orbit type, launch site, and landing outcome using both Python visualizations and SQL queries.
4. **Interactive Visual Analytics** — Built a Folium map to visualize launch site locations and proximity to coastlines/railways, and a Plotly Dash dashboard to filter launches by site and payload range.
5. **Predictive Analysis** — Trained and tuned four classifiers (Logistic Regression, SVM, Decision Tree, KNN) with `GridSearchCV`, then compared them on a held-out test set.

---

## Key Results

- **Best model:** Decision Tree Classifier — **94.4% test accuracy**
- Logistic Regression, SVM, and KNN each reached **83.3%** test accuracy
- **KSC LC-39A** is the strongest launch site (~77% success rate)
- Landing success rate rose steadily from **0% (2010–2013)** to a peak of **~78% (2017)**
- Lighter payloads and certain orbits (e.g., HEO, LEO) are associated with higher landing success

---

## Tech Stack

- **Python:** Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn
- **SQL:** SQLite, ipython-sql
- **Web Scraping:** BeautifulSoup, Requests
- **Visualization:** Folium (interactive maps), Plotly Dash (interactive dashboard)
- **Machine Learning:** Logistic Regression, SVM, Decision Tree, K-Nearest Neighbors, GridSearchCV

---

## How to Run the Dashboard

```bash
pip install dash pandas plotly
python spacex-dash-app.py
```

Then open the address shown in the terminal (default: `http://127.0.0.1:8050`).

---

## Project Report

The full project report and presentation slides are included as part of the IBM Applied Data Science Capstone submission.

## License

This project was created for educational purposes as part of the IBM Applied Data Science Capstone on Coursera.

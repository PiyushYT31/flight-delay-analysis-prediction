# Flight Delay Analysis and Prediction

A 1–2 day aviation machine-learning mini-project. It analyzes historical U.S. flights and predicts whether arrival delay is **15 minutes or more**.

## Dataset
Use the U.S. Bureau of Transportation Statistics (BTS) On-Time Performance data:
https://www.transtats.bts.gov/ONTIME/

Download one month of On-Time Performance data as a CSV and save it as `data/flight_data.csv`. The portal's download workflow may change; select the On-Time Performance table and a month. Start with one month to keep runtime manageable.

The target is `DELAYED_15 = 1` when `ARR_DELAY >= 15`; otherwise it is 0. Actual arrival delay and actual departure delay are not model features, avoiding target leakage.

## Algorithms
- Logistic Regression: supervised classification
- K-Nearest Neighbors (KNN): supervised classification
- Support Vector Machine (SVM, RBF kernel): supervised classification
- K-Means: unsupervised clustering, evaluated separately

These are from the algorithm list for this project. Regression algorithms are not needed for this classification-focused version. HMM Forward–Backward and Viterbi are sequence algorithms and are not needed for the baseline.

## Run the notebook
1. Install Python 3.10 or newer.
2. Extract the project folder.
3. Optional: create a virtual environment:
   ```bash
   python -m venv .venv
   ```
   Windows:
   ```bash
   .venv\Scripts\activate
   ```
   macOS/Linux:
   ```bash
   source .venv/bin/activate
   ```
4. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
5. Place the BTS CSV at `data/flight_data.csv`.
6. Launch Jupyter:
   ```bash
   jupyter notebook
   ```
7. Open `notebooks/flight_delay_analysis_prediction.ipynb` and run all cells in order.

## Evaluation
The classifiers are compared using accuracy, precision, recall, F1 score, and ROC-AUC. K-Means is assessed separately using a silhouette score and delay rates per cluster. Do not compare a clustering silhouette score directly to classification metrics.

## GitHub upload
Create a new GitHub repository, e.g. `flight-delay-analysis-prediction`. In a terminal opened in the extracted project directory, run:
```bash
git init
git add README.md requirements.txt .gitignore notebooks data results
git commit -m "Add flight delay prediction mini project"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/flight-delay-analysis-prediction.git
git push -u origin main
```
Replace `YOUR-USERNAME` with your GitHub username. If GitHub asks you to authenticate, use its supported sign-in flow. Never commit credentials.

The `.gitignore` excludes local CSV files and generated result CSVs to avoid accidentally uploading large raw data. The notebook itself and instructions should be committed. Before submission, run the notebook top to bottom and replace the conclusion placeholders with actual results. Do not invent scores.

## Repository layout
```text
flight-delay-analysis-prediction/
├── data/
│   └── .gitkeep
├── notebooks/
│   └── flight_delay_analysis_prediction.ipynb
├── results/
│   └── .gitkeep
├── requirements.txt
├── .gitignore
└── README.md
```

## Limitations
- One month may not represent seasonal variation.
- Weather and live air-traffic/operational conditions are not included.
- The model is educational and should not be used for real-world operational decisions.

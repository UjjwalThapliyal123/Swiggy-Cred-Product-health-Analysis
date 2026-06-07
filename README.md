## Swiggy & CRED — Product Health Monitor

When did users start getting unhappy — and what were they complaining about?

A full product analytics pipeline built on 25,000+ real Google Play Store reviews, using statistical and NLP techniques to detect structural shifts in user sentiment for two major Indian consumer apps.

🔍 The Question
Swiggy's app rating dropped 1.83 stars around a specific date. CRED's ratings stayed flat. Why? And what can the difference tell us about product culture?
This notebook answers that using real data — no simulations, no synthetic datasets.

📈 Key Findings
MetricSwiggyCREDAvg Rating~3.33Higher, more stableChangepoints DetectedYes — April 22, 2026None (stable)Rating Drop1.83 stars (statistically significant)—Effect Size (Cohen's d)Large—Review Response Rate~100%35.4%Rating DistributionJ-shaped (polarised)Skewed positive
Top post-drop complaint keywords for Swiggy (TF-IDF): cancel · worst experience · order
The surprising insight: Swiggy responds to nearly every review. CRED responds to barely a third. Swiggy's ratings are volatile — but they're listening.

🛠️ Tech Stack
LibraryPurposegoogle-play-scraperScrape 25,000+ reviews per appNLTK (VADER)Sentiment scoring (−1 to +1 compound score)rupturesPELT changepoint detection on rolling avg ratingsscipyMann-Whitney U test for statistical significancescikit-learnTF-IDF keyword extraction from 1–2 star reviewsstatsmodelsPower analysis & sample size calculationmatplotlib / seabornAll visualisations

Scrape reviews (25k each)
        ↓
Filter to common date range
        ↓
VADER sentiment scoring
        ↓
7-day rolling average ratings
        ↓
PELT changepoint detection
        ↓
Mann-Whitney U + Cohen's d (statistical validation)
        ↓
TF-IDF keyword analysis (before vs after changepoint)
        ↓
Power analysis & experiment design
        ↓
Product health comparison dashboard


📊 Visualisations
The notebook produces 6 charts saved as .png files:

day1_rating_over_time.png — 7-day rolling avg ratings for both apps
day2_changepoints_swiggy.png — PELT changepoint detection (Swiggy)
day2_changepoints_cred.png — PELT changepoint detection (CRED)
day4_keywords_swiggy.png — TF-IDF complaints before vs after changepoint
day4_keywords_cred.png — TF-IDF complaints for CRED
day6_comparison.png — Side-by-side product health metrics


📌 Limitations & Biases

Self-selection bias — users with strong opinions (love/hate) are overrepresented
Anonymization — all usernames are "A Google user"; deduplication uses reviewId
Language/region scope — English-language reviews from India only (lang='en', country='in')
Google Play ToS — scraping is for educational purposes only; commercial use may violate ToS
CRED penalty setting — penalty=10 is intentional; CRED's stability means a strict threshold avoids false positives. The insight IS the stability.





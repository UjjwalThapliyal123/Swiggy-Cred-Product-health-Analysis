## Swiggy & CRED — Product Health Monitor

**When did users start getting unhappy — and what were they complaining about?**

A full product analytics pipeline built on 25,000+ real Google Play Store reviews, using statistical and NLP techniques to detect structural shifts in user sentiment for two major Indian consumer apps.

**🔍 The Question**
Swiggy's app rating dropped 1.83 stars around a specific date. CRED's ratings stayed flat. Why? And what can the difference tell us about product culture?
This notebook answers that using real data — no simulations, no synthetic datasets.

**📈 Key Findings**


**🛠️ Tech Stack**
1. google-play-scraper -  Scrape 25,000+ revie
2. NLTK (VADER) - Sentiment scoring (−1 to +1 compound score)
3. ruptures - PELT changepoint detection on rolling avg ratings
4. scipy - Mann-Whitney U test for statistical significance
5. scikit-learn - TF-IDF keyword extraction from 1–2 star reviews
6. statsmodels - Power analysis & sample size calculation
7. matplotlib / seabornAll visualisations

**Analysis Pipeline**

<img width="412" height="408" alt="image" src="https://github.com/user-attachments/assets/2b3860b9-5e31-4988-a3a1-91eb8b5a6e18" />



**📊 Visualisations**

The notebook produces 6 charts saved as .png files:

day1_rating_over_time.png — 7-day rolling avg ratings for both apps

day2_changepoints_swiggy.png — PELT changepoint detection (Swiggy)

day2_changepoints_cred.png — PELT changepoint detection (CRED)

day4_keywords_swiggy.png — TF-IDF complaints before vs after changepoint

day4_keywords_cred.png — TF-IDF complaints for CRED

day6_comparison.png — Side-by-side product health metrics


**📌 Limitations & Biases**

1. Self-selection bias — users with strong opinions (love/hate) are overrepresented

2. Anonymization — all usernames are "A Google user"; deduplication uses reviewId

3. Language/region scope — English-language reviews from India only (lang='en', country='in')

4. Google Play ToS — scraping is for educational purposes only; commercial use may violate ToS

5. CRED penalty setting — penalty=10 is intentional; CRED's stability means a strict threshold avoids false positives. The insight IS the stability.





# 🎵 Spotify Most Streamed Songs of 2023 — Analysis

An exploratory data analysis of Spotify's most-streamed songs of 2023, built to understand what actually drives a track's popularity — is it the artist, the release timing, the "vibe" of the song, or something else entirely?

## Why this project

I wanted a dataset that was fun to poke at but still meaty enough to practice real EDA workflows on — cleaning messy columns, engineering new features, and asking questions that actually have answers hiding in the data. Music streaming data turned out to be perfect for that: everyone has an intuition about what makes a song a hit, and this was a chance to check those intuitions against the numbers.

## Dataset

[Most Streamed Spotify Songs 2023](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023) (Kaggle), pulled in directly via `kagglehub`. It contains 900+ tracks with metadata (artist, release date, playlist/chart appearances) alongside Spotify's audio features (danceability, energy, valence, acousticness, and more).

## What's been done so far

**Data cleaning**
- Combined `released_day`, `released_month`, and `released_year` into a single `released_date` column
- Fixed the `streams` column, which loaded as text (with at least one corrupted row) — coerced it to numeric and cast it to `int64` so it's actually usable for math
- Checked the dataset shape and missing-value counts column by column before touching anything

**Feature engineering & "Spotify Wrapped"-style insights**
Rather than just describing the data, I engineered a few features to answer specific questions:
- **Top songs & artist of the year** — which tracks and artists racked up the most streams in 2023
- **Best collab of 2023** — filtering to multi-artist tracks (`artist_count >= 2`) and ranking by streams
- **Party score** — a combined `danceability_% + energy_%` metric to surface genuine dance-party tracks (both features above 85)
- **Workout favorites** — high-energy tracks (`energy_% > 90`)
- **Most romantic songs** — high valence, low energy, to capture the mellower, feel-good end of the spectrum

**Monthly trends**
- Release volume by month, and whether release timing correlates with total or average streams
- Side-by-side comparison of *number of releases* vs. *average streams per release*, month by month, to see whether flooding a month with releases actually pays off in streams

## Repository structure
```text
spotify-analysis/
├── spotify-2023.csv
├── spotify_analysis.py
└── README.md
```

## 🗂️ Project Roadmap

### ✅ Phase 1 — Exploratory Data Analysis (EDA)
- [x] Dataset overview
- [x] Data cleaning
- [x] Feature engineering
- [x] Spotify Wrapped-style insights
- [x] Monthly trend visualizations
- [ ] Artist-level analysis
- [ ] Audio feature analysis (danceability, energy, valence, acousticness, etc. in depth)

---

### ⏳ Phase 2 — Statistical Analysis
- [ ] Correlation analysis between streams and audio features
- [ ] Hypothesis testing
- [ ] Outlier detection
- [ ] Feature relationship analysis

---

### ⏳ Phase 3 — Machine Learning
- [ ] K-Means clustering (grouping songs by audio "vibe")
- [ ] Stream prediction (Random Forest / XGBoost)
- [ ] Feature importance analysis
- [ ] Song recommendation system

---

## Tech stack
`Python` · `pandas` · `matplotlib` · `seaborn` · `kagglehub`

## Inspiration

This project took a lot of inspiration from [Spotify-Music-Data-Analysis](https://github.com/bioinformaticsgx/Spotify-Music-Data-Analysis) — especially the way it layers visualizations to actually answer a question rather than just show a chart. Aiming for that same "insight-first" approach here, once I get further into the correlation and modeling phases.

## Future improvements
- Add correlation heatmaps and richer visualizations for audio features
- Dig into artist-level trends (one-hit wonders vs. consistent chart presence)
- Summarize key findings into a proper "insights" section
- Build out the clustering/prediction work outlined in Phase 3

## Project status

🚧 In progress — EDA and feature engineering are mostly done; statistical analysis and modeling are up next.

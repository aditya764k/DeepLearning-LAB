# 📝 College Submission Details

## Project: End-to-End Movie Recommendation System

---

### 🏫 Institute Information

| Field | Details |
|---|---|
| **Institute** | DKTE Society's Textile and Engineering Institute, Ichalkaranji |
| **Department** | Computer Engineering |
| **Course** | Deep Learning Lab |
| **Academic Year** | 2025 – 2026 |
| **Semester** | VI (Third Year – Sem II) |

---

### 👤 Student Details

| Field | Details |
|---|---|
| **Student Name** | Aditya Shintre |
| **Roll Number** | 23uam127 |
| **Division** | B div |
| **Batch** | Ty AIML |


---



## 🎯 Problem Statement

Design and implement an **End-to-End Movie Recommendation System** that:
1. Uses **Content-Based Filtering** to recommend similar movies based on metadata features (genres, cast, keywords, director).
2. Applies **Natural Language Processing (NLP)** and a trained ML classifier to perform sentiment analysis on live IMDB user reviews.
3. Integrates with the **TMDB (The Movie Database) API** to fetch real-time movie metadata (posters, ratings, cast bios, runtime).
4. Exposes the system as a **production-ready Flask web application** with a clean, user-friendly interface.
5. Follows **MLOps best practices** using DVC for data & model versioning and Docker for containerized deployment.

---

## 🧠 Learning Outcomes Addressed

| # | Learning Outcome |
|---|---|
| LO1 | Apply machine learning algorithms (cosine similarity, TF-IDF) to build a recommendation system |
| LO2 | Implement NLP preprocessing and text classification for sentiment analysis |
| LO3 | Integrate trained ML models into a web framework (Flask) for real-world deployment |
| LO4 | Use data versioning tools (DVC) to manage datasets and ML experiments reproducibly |
| LO5 | Containerize a machine learning application using Docker |
| LO6 | Perform Exploratory Data Analysis (EDA) and derive insights from large movie datasets |

---

## 🧪 Experiments Performed

### Experiment 1 — Exploratory Data Analysis (EDA)
- **Notebook**: `NoteBook_Experiments/Exploratory Data Analysis.ipynb`
- **Objective**: Analyze the TMDB 5000 dataset to understand distributions, missing values, feature correlations, and top genres/directors.
- **Tools**: Pandas, Matplotlib, Seaborn

### Experiment 2 — Movie Recommendation System (Content-Based Filtering)
- **Notebook**: `NoteBook_Experiments/Movie Recommendation System.ipynb`
- **Objective**: Build the core recommendation engine using CountVectorizer and cosine similarity on combined movie metadata features.
- **Output**: Saved `main_data.csv` (preprocessed), recommendation function

### Experiment 3 — Sentiment Analysis on Reviews
- **Notebook**: `NoteBook_Experiments/Sentimental Analysis on Reviews.ipynb`
- **Objective**: Train an NLP classifier to label IMDB reviews as *Good* or *Bad*.
- **Tools**: NLTK, Scikit-learn
- **Output**: `nlp_model.pkl`, `tranform.pkl`

---

## ⚙️ Technical Specifications

| Component | Technology |
|---|---|
| Backend Framework | Flask (Python 3.8) |
| ML Library | Scikit-learn 1.2.2 |
| NLP | NLTK, TF-IDF Vectorizer |
| Data Processing | Pandas, NumPy, SciPy |
| Web Scraping | BeautifulSoup4 + lxml |
| API Integration | tmdbv3api (TMDB API) |
| Frontend | HTML5, CSS3, JavaScript, Bootstrap |
| Containerization | Docker |
| Data Versioning | DVC (Data Version Control) |
| Version Control | Git / GitHub |

---



## 📂 Submission Checklist

- [x] Source code (`app.py`, `static/`, `templates/`)
- [x] Jupyter Notebooks (EDA, Recommendation, Sentiment Analysis)
- [x] Trained Model Artifacts (`nlp_model.pkl`, `tranform.pkl`, `main_data.csv`)
- [x] `requirements.txt` (all dependencies listed)
- [x] `Dockerfile` (containerization ready)
- [x] `README.md` (updated with full project documentation)
- [x] `SUBMISSION.md` (this file)
- [x] DVC configuration (`.dvc/` directory)
- [x] `LICENSE` (GNU GPL v3.0)

---

## 🖼️ Screenshots

> *(Add screenshots of the running application here for the submission report)*

1. **Home Page** — Search bar with movie auto-complete
2. **Recommendation Page** — Movie details, cast, top 10 recommendations
3. **Sentiment Analysis Section** — IMDB reviews classified as Good/Bad


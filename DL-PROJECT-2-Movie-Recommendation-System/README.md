# 🎬 End-to-End Movie Recommendation System

<div align="center">

![Python](https://img.shields.io/badge/Python-3.8-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-2.x-000000?style=for-the-badge&logo=flask&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.2.2-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-NLP-85C1E9?style=for-the-badge)
![Docker](https://img.shields.io/badge/Docker-Ready-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![DVC](https://img.shields.io/badge/DVC-Data%20Versioning-945DD6?style=for-the-badge)

**An intelligent, full-stack movie recommendation web application that combines Content-Based Filtering with NLP-driven Sentiment Analysis to deliver personalized movie suggestions.**

</div>

---

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Key Features](#-key-features)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Machine Learning Models](#-machine-learning-models)
- [Installation & Setup](#-installation--setup)
- [Usage](#-usage)
- [Dataset](#-dataset)
- [Results & Performance](#-results--performance)
- [License](#-license)

---

## 📖 About the Project

This project is a **Deep Learning Lab Assignment** developed as part of the **Third Year B.E. (Computer Engineering)** curriculum. It demonstrates the end-to-end lifecycle of a machine learning product — from data preprocessing and model training to deployment as a production-ready web application.

The system recommends movies based on **content similarity** (genres, cast, keywords, crew, and overview) and analyses IMDB user reviews using **Natural Language Processing (NLP)** to classify them as *Good* or *Bad* sentiment — giving the user a complete 360° view of any movie.

### 🎯 Objectives
- Build a content-based movie recommendation engine using cosine similarity.
- Perform sentiment analysis on IMDB reviews using an NLP classification model.
- Integrate real-time movie metadata (posters, cast, details) via the **TMDB API**.
- Deploy the application as a **Dockerized Flask web service**.
- Apply **DVC (Data Version Control)** for reproducible ML pipelines.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🔍 **Smart Search** | Auto-complete search bar powered by movie title dataset |
| 🎭 **Movie Details** | Fetches real-time poster, overview, genres, ratings & runtime from TMDB API |
| 🤝 **Recommendations** | Top 10 similar movies using TF-IDF vectors & cosine similarity |
| 🎬 **Cast Information** | Detailed cast profiles, biographies, birthdays & characters |
| 💬 **Sentiment Analysis** | Web-scrapes IMDB reviews and classifies each as Good/Bad using ML |
| 🐳 **Dockerized** | Fully containerized application for consistent deployment |
| 📊 **DVC Pipelines** | Data and model versioning with DVC for reproducibility |

---

## 🏗 System Architecture

```
User Input (Movie Name)
        │
        ▼
┌──────────────────┐      ┌──────────────────────┐
│   Flask Backend   │◄────►│     TMDB API          │
│   (app.py)        │      │  (Movie Metadata)     │
└────────┬─────────┘      └──────────────────────┘
         │
    ┌────┴────────────────────┐
    │                         │
    ▼                         ▼
┌───────────────┐     ┌───────────────────────┐
│ Content-Based │     │   Sentiment Analysis  │
│  Recommender  │     │   (NLP Model)         │
│               │     │                       │
│ CountVectorizer│    │  TF-IDF Vectorizer    │
│ + Cosine Sim  │     │  + Naive Bayes / SVM  │
└───────────────┘     └───────────────────────┘
         │                         │
         └────────────┬────────────┘
                      ▼
              ┌───────────────┐
              │  HTML Output  │
              │  (Jinja2)     │
              └───────────────┘
```

---

## 🛠 Tech Stack

### Backend
- **Python 3.8** — Core programming language
- **Flask** — Lightweight WSGI web framework
- **Scikit-learn 1.2.2** — ML algorithms (CountVectorizer, Cosine Similarity, Classifiers)
- **NLTK** — Natural Language Processing toolkit
- **Pandas / NumPy** — Data manipulation and numerical computing
- **BeautifulSoup4 + lxml** — Web scraping IMDB reviews
- **tmdbv3api** — Wrapper for The Movie Database API

### Frontend
- **HTML5 / CSS3 / JavaScript** — UI templates with Jinja2
- **Bootstrap** — Responsive design components

### MLOps & DevOps
- **DVC** — Data Version Control for dataset and model tracking
- **Docker** — Containerization for consistent deployment
- **Git** — Version control

### Data
- **TMDB 5000 Movies Dataset** — Source for movie metadata (movies.csv)
- **IMDB Reviews** — Live web-scraped user reviews for sentiment analysis

---

## 📁 Project Structure

```
End-to-End-Movie-Recommendation-System/
│
├── 📂 Artifacts/                    # Trained model artifacts
│   ├── __init__.py
│   ├── main_data.csv                # Preprocessed movie dataset
│   ├── movies.csv                   # Raw TMDB movie dataset
│   ├── nlp_model.pkl                # Trained sentiment analysis model
│   ├── reviews.txt                  # Raw IMDB reviews corpus
│   └── tranform.pkl                 # Fitted TF-IDF vectorizer
│
├── 📂 NoteBook_Experiments/         # Jupyter notebooks for EDA & model training
│   ├── Exploratory Data Analysis.ipynb
│   ├── Movie Recommendation System.ipynb
│   └── Sentimental Analysis on Reviews.ipynb
│
├── 📂 templates/                    # Jinja2 HTML templates
│   ├── home.html                    # Landing page with search
│   ├── index.html                   # Base template
│   └── recommend.html               # Movie detail + recommendation page
│
├── 📂 static/                       # Static frontend assets
│   ├── style.css                    # Application stylesheet
│   ├── recommend.js                 # AJAX + TMDB API logic
│   └── autocomplete.js              # Search auto-complete logic
│
├── 📂 .dvc/                         # DVC configuration
│
├── app.py                           # Main Flask application entry point
├── template.py                      # Project structure generator script
├── requirements.txt                 # Python dependencies
├── Dockerfile                       # Docker container definition
├── .dvcignore                       # DVC ignore rules
├── .gitignore                       # Git ignore rules
└── README.md                        # Project documentation
```

---

## 🤖 Machine Learning Models

### 1. Content-Based Recommendation Engine

- **Technique**: Bag-of-Words with `CountVectorizer` → Cosine Similarity Matrix
- **Input Features**: `genres`, `keywords`, `tagline`, `cast`, `director`
- **How It Works**:
  1. Combine all features into a single text `comb` column per movie.
  2. Transform with `CountVectorizer` to get a term-frequency matrix.
  3. Compute pairwise **cosine similarity** across all movies.
  4. For a query movie, retrieve the top 10 most similar movies.

### 2. Sentiment Analysis (NLP Classifier)

- **Technique**: TF-IDF Vectorization + trained Classifier (e.g., Naive Bayes / SVM)
- **Input**: Raw IMDB review text
- **Output**: `Good` 👍 or `Bad` 👎 sentiment label
- **Pipeline**:
  1. Scrape live reviews from IMDB for the selected movie.
  2. Vectorize each review using the fitted `tranform.pkl` vectorizer.
  3. Predict sentiment using `nlp_model.pkl`.
  4. Display results alongside reviews on the recommendation page.

---

## ⚙ Installation & Setup

### Prerequisites
- Python 3.8+
- pip / conda
- Docker (optional)
- TMDB API Key ([Get one here](https://www.themoviedb.org/settings/api))

---



## 🚀 Usage

1. **Search** for a movie by typing in the search bar (auto-complete enabled).
2. Click **"Get Recommendations"** to fetch movie details and similar movies.
3. Scroll down to view:
   - Movie details (poster, genres, rating, runtime)
   - Top 10 recommended movies
   - Cast information with bios
   - IMDB user reviews with Good/Bad sentiment labels

---

## 📊 Dataset

| Dataset | Source | Records |
|---|---|---|
| TMDB 5000 Movies | [Kaggle](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata) | ~5,000 movies |
| IMDB Reviews | Live web scraping | Dynamic |
| Preprocessed `main_data.csv` | Feature-engineered from TMDB | ~5,000 rows |

---

## 📈 Results & Performance

| Model | Task | Metric | Score |
|---|---|---|---|
| Cosine Similarity | Movie Recommendation | Relevance (manual) | ✅ High |
| NLP Classifier | Sentiment Analysis | Accuracy | ~90%+ |

> The recommendation quality is evaluated qualitatively by domain relevance (genre, director, cast overlap), while the sentiment classifier is evaluated on accuracy of review classification.

---

## 📄 License

Distributed under the **GNU General Public License v3.0**.  
See [`LICENSE`](LICENSE) for full details.

---

## 🙏 Acknowledgements

- [TMDB API](https://www.themoviedb.org/) — for real-time movie data
- [Kaggle - TMDB 5000 Movie Dataset](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata) — training data
- [Scikit-learn](https://scikit-learn.org/) — ML framework
- [Flask](https://flask.palletsprojects.com/) — web framework
- [DVC](https://dvc.org/) — MLOps and data versioning

---

<div align="center">
<b>Developed as part of Deep Learning Lab | B.Tech Artificial Intelligence and Machine Learning| Academic Year 2025–26</b>
</div>

# 🎬 Movie Recommendation System

A Content-Based Movie Recommendation Engine built using Python, Scikit-Learn, and the TMDB 5000 Movies Dataset. The system calculates content similarity across movie metadata (genres, keywords, cast, crew, and overviews) using vectorization and cosine similarity.

---

## 📌 Features

* **Exploratory Data Analysis (EDA):** Visualizations covering movie vote distribution, top genres, and popularity vs. vote average colored by budget.
* **Data Cleaning & Feature Extraction:** Safe parsing of JSON/literal metadata to extract directors, top 3 actors, genres, and keywords.
* **Metadata Soup Creation:** Combines text features into a unified document string to build high-accuracy similarity embeddings.
* **Cosine Similarity Engine:** Text vectorization via `CountVectorizer` paired with cosine similarity calculation to rank movie recommendations.
* **Reusable Class & API Pattern:** Encapsulated in a `MovieRecommender` class with a mock API response pattern suitable for web integration (e.g., Flask or FastAPI).

---

## 🛠️ Tech Stack & Dependencies

* **Language:** Python 3.x
* **Data Handling:** Pandas, NumPy
* **Machine Learning:** Scikit-Learn
* **Visualization:** Matplotlib, Seaborn

---

## 📁 Dataset

The project uses the **TMDB 5000 Movie Dataset**:
* `tmdb_5000_movies.csv`
* `tmdb_5000_credits.csv`

> **Note:** Ensure both CSV files are placed in the root/working directory before running the script or notebook.

---

## 🚀 How It Works

1. **Preprocessing:** Merges movies and credits datasets on the movie `id`.
2. **Metadata Sanitization:** Strips spaces from names/keywords (e.g., `Sam Worthington` $\rightarrow$ `samworthington`) to avoid duplicate tag collisions.
3. **Soup Generation:** Combines sanitized genres, keywords, cast, director, and overview into a single text representation per movie.
4. **Similarity Scoring:**
   ```python
   count = CountVectorizer(stop_words='english')
   count_matrix = count.fit_transform(df['soup'])
   cosine_sim = cosine_similarity(count_matrix, count_matrix)

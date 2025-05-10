# 📰 Content-Based News Recommendation System (MIND Dataset)

This project implements a **content-based news recommendation system** using the [Microsoft MIND Dataset](https://msnews.github.io/). It ranks and recommends news articles to users based on the textual similarity of articles they’ve explicitly read.

---

## 📁 Project Structure

| Notebook | Purpose |
|----------|---------|
| `01_load_data.ipynb` | Load and clean news and behavior data; extract TF-IDF text features from article titles and abstracts. |
| `02_user_profile_construction.ipynb`
| `03_content_similarity.ipynb` | Compute article-to-article similarity using TF-IDF and cosine similarity. |
| `04_ranking_and_recommendation.ipynb` | Build user profiles from reading history and rank news recommendations. |

---

## 🧠 Methodology

### ✅ 1. **Dataset**
- Uses the **MINDsmall_train** subset of the Microsoft News Dataset.
- Files:
  - `news.tsv`: Contains article metadata, title, abstract, and entities.
  - `behaviors.tsv`: User interactions (clicked news history).

### ✅ 2. **Text Feature Extraction**
- Combines article **title** and **abstract**.
- Uses `TfidfVectorizer` to extract text features (max 5000 terms).

### ✅ 3. **User Profile Construction**
- For each user, we compute the **average TF-IDF vector** of articles they have explicitly read (`History` field in behaviors.tsv).

### ✅ 4. **Similarity & Recommendation**
- Calculates **cosine similarity** between the user profile vector and all candidate news articles.
- Ranks and returns the top-N most relevant articles.

---

## 📌 Example Recommendation

```python
# Recommend top 5 articles for user 'U1001'
recommendations = recommend_for_user('U1001', user_profiles, tfidf_matrix, news_df, top_k=5)
display_recommendations(recommendations)

## Book Recommender System
A collaborative filtering based book recommnder built using python and cosine similarity, designed to suggest personalized titles based on user preference and rating patterns.

## Project Overview

This project leverages a large-scale dataset of over 1 million book ratings, 270K+ books, and 278K+ users to build a recommendation engine that filters for high-quality interactions and generates top-N suggestions using cosine similarity.

## Key Features

-  Data Filtering: Focused on users with >200 ratings and books with >50 ratings to ensure meaningful recommendations.
-  Cosine Similarity: Computes similarity scores between books based on user rating vectors.
-  Popularity Insights: Extracts average ratings and number of ratings to highlight highly rated and frequently reviewed books.
-  Pivot Table Optimization: Transforms rating data into a matrix format for efficient similarity computation.

## Tech Stack

- Python
- Pandas
- NumPy
- scikit-learn
- Jupyter Notebook

## Dataset Details

- Books.csv: Contains metadata like title, author, publisher, and image URLs.
- Users.csv: Includes user demographics such as location and age.
- Ratings.csv: Holds user-book rating interactions.

## How It Works

1. Merge Datasets: Combine ratings with book metadata.
2. Filter Active Users & Popular Books: Retain users with >200 ratings and books with >50 ratings.
3. Create Pivot Table: Generate a user-item matrix with ratings.
4. Compute Similarity: Use cosine similarity to find similar books.
5. Recommend: Return top 5 similar books for any given title.

## Sample Recommendation Function

```python
def recommend(book_name):
    index = np.where(pt.index == book_name)[0][0]
    similar_items = sorted(list(enumerate(similarity_score[index])), key=lambda x: x[1], reverse=True)[1:6]
    return [pt.index[i[0]] for i in similar_items]

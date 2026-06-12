# Netflix Recommendation System

## Project Overview

This project develops and evaluates recommendation systems using a subset of the Netflix Prize Dataset. The goal is to improve content discovery by learning user preferences from historical user-movie interactions and generating personalized movie recommendations.

Two recommendation approaches were implemented and compared:

* Item-Based Collaborative Filtering (Item-CF)
* Singular Value Decomposition (SVD)

The models were evaluated using both rating prediction and recommendation ranking metrics to understand the trade-offs between prediction accuracy and recommendation quality.

---

## Objectives

The recommendation system is designed to:

* Learn user preferences from historical ratings
* Predict ratings for unseen movies
* Generate personalized movie recommendations
* Identify similarities between movies
* Improve content discovery through relevant recommendations

---

## Dataset

The project uses a processed subset of the Netflix Prize Dataset.

### Dataset Characteristics

* Users: 404,555
* Movies: 1,000
* Ratings: 5,010,199
* Sparsity: 98.76%

The dataset is highly sparse, which reflects real-world recommendation system challenges.

---

## Exploratory Data Analysis (EDA)

The following analyses were performed:

### User Activity Patterns

* Most users provide very few ratings.
* A small number of highly active users contribute a large portion of interactions.

### Content Popularity Trends

* Movie popularity follows a long-tail distribution.
* A small number of movies receive the majority of ratings.

### Rating Distribution

* Ratings are concentrated around lower values.
* Most ratings fall between 1 and 3.

### Data Sparsity

* The user-item matrix is extremely sparse (98.76%).
* Most user-movie interactions are missing.

### Key Insights

* Collaborative filtering is suitable due to the large interaction history.
* Sparsity presents a challenge for recommendation quality.
* Popularity bias is likely to occur.
* Cold-start users are difficult to recommend for effectively.

---

## Recommendation Models

### 1. Item-Based Collaborative Filtering

Item-Based Collaborative Filtering recommends movies based on similarity between items.

#### Methodology

1. Construct a user-movie rating matrix.
2. Compute cosine similarity between movies.
3. Predict ratings using weighted ratings of similar movies.
4. Recommend movies with the highest predicted ratings.

#### Advantages

* Easy to interpret.
* Produces strong recommendation rankings.
* Effective for content discovery.

#### Limitations

* Similarity computation becomes expensive as the dataset grows.
* Sensitive to sparsity.

---

### 2. Singular Value Decomposition (SVD)

SVD is a matrix factorization technique that learns latent representations of users and movies.

#### Methodology

1. Factorize the user-item interaction matrix.
2. Learn latent user and movie factors.
3. Predict unseen ratings using latent factor interactions.
4. Recommend highest-scoring unseen movies.

#### Advantages

* Scalable.
* Strong rating prediction performance.
* Captures hidden user-item relationships.

#### Limitations

* Less interpretable.
* Ranking quality may not match rating prediction quality.

---

## Evaluation Methodology

### Train-Test Split

* 80% Training Data
* 20% Test Data

### Relevant Movie Definition

For MAP@10 evaluation:

A movie is considered relevant if:

Rating ≥ 4

### Evaluation Metrics

#### RMSE (Root Mean Squared Error)

Measures rating prediction accuracy.

#### MAP@10 (Mean Average Precision @ 10)

Measures recommendation ranking quality.

---

## Results

| Metric                 | Item-Based CF | SVD      |
| ---------------------- | ------------- | -------- |
| RMSE                   | 1.0013        | 0.9712   |
| MAP@10                 | 0.0038        | 0.0000   |
| Training Time          | Fast          | 7.76 sec |
| Recommendation Ranking | Better        | Poor     |
| Scalability            | Moderate      | Better   |

---

## Key Findings

* SVD achieved the best rating prediction accuracy.
* Item-Based Collaborative Filtering achieved significantly better recommendation ranking performance.
* Accurate rating prediction does not necessarily imply better recommendations.
* MAP@10 and RMSE capture different aspects of recommendation quality.

For content discovery applications, Item-Based Collaborative Filtering proved to be the more effective approach.

---

## Failure Cases

### Cold-Start Users

Users with very few ratings provide insufficient information for reliable personalization. Recommendations become less personalized and tend to rely on popular content.

### Popularity Bias

Frequently rated movies can dominate recommendation lists, reducing exposure to niche content.

### SVD Ranking Failure

Although SVD achieved strong RMSE performance, relevant movies often failed to appear in the Top-10 recommendation list, resulting in poor MAP@10 performance.

---

## Future Improvements

Potential improvements include:

* User-Based Collaborative Filtering
* Hybrid Recommendation Systems
* Neural Collaborative Filtering
* Metadata-Based Recommendations
* Hyperparameter Optimization
* Diversity-Aware Recommendation Strategies

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* Surprise
* Matplotlib
* Seaborn
* Jupyter Notebook

---

## Installation

Clone the repository and install dependencies:

```bash
pip install -r requirements.txt
```

## Running the Project

Run the notebooks in the following order:

1. Data_Sampling.ipynb
2. EDA_Analysis.ipynb
3. Item_Based_CF_fixed.ipynb
4. SVD_Model.ipynb
5. Model_Comparison.ipynb
```

## Repository Structure

```text
Netflix-Recommendation-System/
│
├── Data_Sampling.ipynb
├── EDA_Analysis.ipynb
├── Item_Based_CF_fixed.ipynb
├── SVD_Model.ipynb
├── Model_Comparison.ipynb
│
├── data/
│
└── README.md
```

---

## Conclusion

This project demonstrates the development and evaluation of recommendation systems using the Netflix Prize Dataset. While SVD achieved slightly better rating prediction accuracy, Item-Based Collaborative Filtering produced significantly better recommendation rankings and was therefore selected as the preferred approach for personalized content discovery.

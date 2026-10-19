# Large-Scale Personalized Recommendation Engine

## 1. Project Overview

This project develops a personalized movie recommendation prototype using the MovieLens 25M dataset. It recommends movies to users based on historical ratings, item similarity, and predicted user preferences.

## 2. Architecture Diagram
'''mermaid
flowchart TD
    A["MovieLens 25M Dataset"] --> B["Data Cleaning"]
    B --> C["Time-Based Train/Test Split"]
    C --> D["Popularity Baseline"]
    C --> E["User-Item Interaction Matrix"]
    E --> F["TruncatedSVD Embeddings"]
    F --> G["FAISS Similarity Search"]
    G --> H["Candidate Movie Retrieval"]
    H --> I["HistGradientBoosting Ranking Model"]
    D --> J["Model Evaluation"]
    I --> J
    J --> K["Recall@10 and NDCG@10"]
    I --> L["Ranked Movie Recommendations CSV"]
    K --> M["Evaluation Results CSV"]
    L --> N["GitHub Project Outputs"]
    M --> N
    '''
## 3. Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- TruncatedSVD
- FAISS
- MovieLens 25M dataset
- Jupyter Notebook / Google Colab

## 4. Data Processing

The MovieLens dataset is cleaned and prepared for analysis. Missing values and data quality issues are checked. Ratings are split into training and testing sets based on time to evaluate recommendations on later interactions.

## 5. Recommendation Pipeline

### Popularity Baseline

A popularity-based approach identifies frequently rated movies and provides a baseline for comparison.

### Personalized Retrieval

A user-item interaction matrix is created. TruncatedSVD generates lower-dimensional embeddings, and FAISS is used to retrieve similar movie candidates.

### Ranking Model

A HistGradientBoostingRegressor predicts movie ratings using features such as user interactions, movie interactions, average movie rating, genre count, user index, and movie index.

### Evaluation

The prototype uses Recall@10 and NDCG@10 for recommendation evaluation. RMSE is also calculated for the rating prediction model.

## 6. Preliminary Evaluation Results

| Metric | Popularity Baseline | Personalized Model |
|---|---:|---:|
| Recall@10 | 0.0422 | 0.0449 |
| NDCG@10 | 0.2484 | 0.2566 |

The personalized model shows slightly higher preliminary metric values. These results should be treated as preliminary until both approaches are verified on the same test users and evaluation procedure.

The ranking model achieved an RMSE of approximately 1.0201 on the reported evaluation set.

## 7. Output Files

- model_comparison.csv — preliminary model evaluation metrics.
- personalized_recommendations.csv — personalized recommendation results.
- ranked_recommendations.csv — ranked movie recommendations and predicted ratings.
- Large Scale Personalized Recommendation Engine 1.ipynb — project notebook.

## 8. Current Limitations

This repository contains a working prototype. The following internship requirements are not yet implemented or verified:

- Apache Spark processing.
- TensorFlow Recommenders two-tower retrieval.
- A deep ranking model such as DCN or Wide & Deep.
- Redis caching.
- Triton Inference Server deployment.
- Airflow-based scheduled retraining.
- Online A/B testing and CTR measurement.

## 9. Future Improvements

- Implement scalable data processing with Apache Spark.
- Train a two-tower retrieval model with TensorFlow Recommenders.
- Implement a deep ranking model.
- Add cold-start recommendations and Redis caching.
- Deploy the inference pipeline using Triton.
- Automate retraining with Airflow.
- Conduct an online A/B test and measure CTR.
- Compare models using a consistent evaluation methodology.

## 10. Conclusion

This prototype demonstrates a movie recommendation pipeline using data preparation, matrix factorization, FAISS-based retrieval, a ranking model, and preliminary evaluation. The repository provides a foundation for future development toward a scalable recommendation system.

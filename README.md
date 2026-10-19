
# Large-Scale Personalized Recommendation Engine

## Project Overview
This project builds a movie recommendation prototype
using the MovieLens 25M dataset.

## Technologies Used
- Python
- Pandas and NumPy
- Scikit-learn
- TruncatedSVD
- FAISS
- Google Colab

## Architecture
1. Load and clean movie ratings data.
2. Split the data by timestamp into training and testing sets.
3. Build a popularity-based recommendation baseline.
4. Generate user and movie embeddings with TruncatedSVD.
5. Retrieve similar movie candidates using FAISS.
6. Train a ranking model using engineered features.
7. Generate ranked movie recommendations.
8. Evaluate and compare recommendation metrics.

## Preliminary Evaluation Results

| Model | Recall@10 | NDCG@10 |
|---|---:|---:|
| Popularity Baseline | 0.0422 | 0.2484 |
| Personalized Retrieval + Ranking | 0.0449 | 0.2566 |

These results are preliminary. A fair comparison requires
evaluating both models on the same users using identical
candidate-generation and evaluation rules.

## Limitations
- Uses TruncatedSVD rather than TensorFlow Recommenders.
- Uses a baseline ranking model rather than a DCN model.
- Redis caching, Triton serving, Airflow retraining and
  online A/B testing are not implemented in this prototype.

## Future Improvements
- Add a content-based cold-start fallback.
- Implement a stronger two-stage retrieval and ranking model.
- Add serving, caching and retraining infrastructure.
- Conduct a controlled A/B test.

## Output Files
- model_comparison.csv
- personalized_recommendations.csv
- ranked_recommendations.csv
##How to Run
1.Open the project notebook in Google Colab.
2.Download the MovieLens 25M dataset from the official GroupLens website (https://grouplens.org/datasets/movielens/25m/).
3.Upload the dataset to Google Colab or configure the notebook to access it.
4.Run the notebook cells in order, from top to bottom.
5.Review the evaluation metrics and generated CSV output files.
Note: The notebook may require additional Python libraries and dataset paths to be configured before running.

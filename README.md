## Scalable Food & Diet Recommendation System
## 1. Executive Summary
This project delivers a fully containerized, end-to-end Food and Diet Recommendation System leveraging modern web technologies and machine learning. Designed with scalability and personalization in mind, the system uses FastAPI for backend API development, Streamlit for an interactive frontend, and integrates a full DevOps/MLOps pipeline powered by Docker, Kubernetes, Jenkins, and MLFlow.

## 2. Purpose and Scope
The system is engineered to assist users in generating personalized dietary recommendations based on nutritional metrics, ingredient preferences, and dietary restrictions. It aims to address shortcomings in generic diet applications by introducing:

Dynamic personalization via ML models (KNN, SVD)

Feedback integration for continuous model optimization

Cloud-native deployment supporting CI/CD and real-time inference

## 3. System Architecture
▸ Frontend: Streamlit
Captures user inputs such as calorie limits, allergies, and ingredient preferences.

Displays personalized meal plans with nutrition breakdowns.

Enables feedback submission (e.g., star ratings) for model refinement.

▸ Backend: FastAPI
Exposes RESTful endpoints for prediction and health checks.

Serves trained ML models as a lightweight, low-latency API.

Acts as the interface between the frontend and the ML engine.

▸ ML Recommendation Engine
Implements collaborative filtering (KNN, SVD) and NLP preprocessing.

Pulls user-specified ingredients and nutritional vectors to deliver meal suggestions.

Uses feedback data to trigger retraining and enhance relevance.

▸ Database: Structured CSV Repository
Recipes tagged with full nutritional information and preparation steps.

Queried dynamically to generate recommendations based on vector similarity.

## 4. API Design Snapshot
POST /predict/

Payload:
{
  "nutrition_input": [calories, fat, sugar, protein, ...],
  "ingredients": ["chicken", "spinach"],
  "params": {
    "n_neighbors": 5,
    "return_distance": false
  }
}

## Response:
{
  "output": [
    {
      "Name": "Grilled Chicken Salad",
      "Calories": 320,
      "RecipeInstructions": [...],
      ...
    }
  ]
}

## 5. Deployment and Monitoring
Docker-based microservices deployed across Kubernetes clusters for horizontal scalability.

Streamlit and FastAPI containers run independently for modular updates.

Performance is monitored via Prometheus and Grafana, with logs aggregated through ELK stack.

ML models retrained based on feedback thresholds via MLFlow triggers.



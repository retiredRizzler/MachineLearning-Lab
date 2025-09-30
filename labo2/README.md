# Laboratory 2 - Machine Learning

This project uses the K-means algorithm for unsupervised clustering, as well as its improved version K-means++. Analyses are performed on four different datasets: Iris, Breast Cancer, Wine, and Mall Customers.

## Project Structure

The project is organized into three main folders, corresponding to the different weeks of the laboratory:

```
labo2/
├── semaine_3/
│   ├── iris_clustering.py
│   ├── breast_cancer_clustering.py
│   ├── wine_clustering.py
│   ├── mall_customers_clustering.py
│   └── README.md 
│
├── semaine_4/
│   ├── iris_semaine4.py
│   ├── breast_cancer_semaine4.py
│   ├── wine_semaine4.py
│   ├── mall_customers_semaine4.py
│   └── README.md 
│
└── semaine_5/
    ├── iris_semaine5.py
    ├── breast_cancer_semaine5.py
    ├── wine_semaine5.py
    ├── mall_customers_semaine5.py
    └── README.md 
```

## Weekly Content

### Week 3

Implementation of the basic K-means algorithm and comparison with the scikit-learn version. Tests performed with different predefined K values (K=2 and K=3 or K=5 for Mall Customers). Performance evaluation using Adjusted Rand Index (ARI) and inertia.

### Week 4

Determination of the optimal number of clusters K using the elbow method and the silhouette method. Detailed analysis of results for each dataset and comparison with the actual number of classes when known.

### Week 5

Comparison between standard K-means algorithm and K-means++. Analysis of differences in terms of performance (ARI, inertia, silhouette), convergence (number of iterations), and stability (variance of results with different initializations).

## Main Results

### Week 3 - Basic K-means

- **Iris**: K=3 gives the best results (ARI=0.62), corresponding to the 3 species
- **Breast Cancer**: K=2 is optimal (ARI=0.68), corresponding to malignant/benign diagnoses
- **Wine**: K=3 is optimal (ARI=0.90), corresponding to the 3 wine types
- **Mall Customers**: K=5 gives significantly better inertia than K=3

### Week 4 - Determining the Optimal Number of Clusters

- **Iris**: elbow method → K=3, silhouette method → K=2
- **Breast Cancer**: Both methods suggest K=2
- **Wine**: Both methods suggest K=3
- **Mall Customers**: elbow method → K=5, silhouette method → K=6

### Week 5 - K-means vs K-means++

- **Iris**: K-means++ converges faster but shows lower stability
- **Breast Cancer**: Similar performance, slight convergence improvement with K-means++
- **Wine**: K-means++ offers remarkable stability (20-150 times more stable)
- **Mall Customers**: K-means++ produces more compact clusters with better silhouette scores

## Setup and Execution

To facilitate execution and avoid installation issues, we recommend using Google Colab:

1. Access [Google Colab](https://colab.research.google.com/)
2. Create a new notebook
3. Upload the Python files into the notebook corresponding to the week you wish to execute
4. Run each script (Ctrl + Enter) to see the analysis results

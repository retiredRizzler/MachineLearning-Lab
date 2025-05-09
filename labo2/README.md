# Laboratoire 2 - Machine Learning

Ce projet utilise l'algorithme K-means pour le clustering non-supervisé, ainsi que sa version améliorée K-means++. Les analyses sont effectuées sur quatre datasets différents: Iris, Breast Cancer, Wine et Mall Customers.

## Structure du Projet

Le projet est organisé en trois dossiers principaux, correspondant aux différentes semaines du laboratoire:

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
    ├── iris_kmeans_pp.py
    ├── breast_cancer_kmeans_pp.py
    ├── wine_kmeans_pp.py
    ├── mall_customers_kmeans_pp.py
    └── README.md 
```

## Contenu des Semaines

### Semaine 3
Implémentation de l'algorithme K-means de base et comparaison avec la version de scikit-learn. Tests effectués avec différentes valeurs de K prédéfinies (K=2 et K=3 ou K=5 pour Mall Customers). Évaluation des performances via l'Adjusted Rand Index (ARI) et l'inertie.

### Semaine 4
Détermination du nombre optimal de clusters K en utilisant la méthode du coude et la méthode de la silhouette. Analyse détaillée des résultats pour chaque dataset et comparaison avec le nombre réel de classes lorsque connu.

### Semaine 5
Comparaison entre l'algorithme K-means standard et K-means++. Analyse des différences en termes de performance (ARI, inertie, silhouette), convergence (nombre d'itérations) et stabilité (variance des résultats avec différentes initialisations).

## Principaux Résultats

### Semaine 3 - K-means de Base
- **Iris**: K=3 donne les meilleurs résultats (ARI=0.62), correspondant aux 3 espèces
- **Breast Cancer**: K=2 est optimal (ARI=0.68), correspondant aux diagnostics malin/bénin
- **Wine**: K=3 est optimal (ARI=0.90), correspondant aux 3 types de vins
- **Mall Customers**: K=5 donne une inertie nettement meilleure que K=3

### Semaine 4 - Détermination du Nombre Optimal de Clusters
- **Iris**: méthode du coude → K=3, méthode de silhouette → K=2
- **Breast Cancer**: Les deux méthodes suggèrent K=2
- **Wine**: Les deux méthodes suggèrent K=3
- **Mall Customers**: méthode du coude → K=5, méthode de silhouette → K=6

### Semaine 5 - K-means vs K-means++
- **Iris**: K-means++ converge plus rapidement mais montre une stabilité inférieure
- **Breast Cancer**: Performances similaires, légère amélioration de convergence avec K-means++
- **Wine**: K-means++ offre une stabilité remarquable (20-150 fois plus stable)
- **Mall Customers**: K-means++ donne des clusters plus compacts avec une meilleure silhouette

## Configuration et Exécution

Pour faciliter l'exécution et éviter les problèmes d'installation, nous recommandons d'utiliser Google Colab:

1. Accédez à [Google Colab](https://colab.research.google.com/)
2. Créez un nouveau notebook
3. Téléchargez les fichiers Python dans le notebook correspondant à la semaine que vous souhaitez exécuter
4. Lancez chaque script (Ctrl + Enter) pour voir les résultats de l'analyse

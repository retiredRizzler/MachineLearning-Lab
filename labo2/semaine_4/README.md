# Rapport de la Semaine 4 - K-means et Détermination du Nombre de Clusters

## Introduction

Implémentation de deux méthodes pour déterminer le nombre optimal de clusters K :
- **Méthode du coude** : Analyse visuelle du graphique (voir code)
- **Méthode de la silhouette** : Recherche du K maximisant le score de silhouette moyen

## Tableau récapitulatif des résultats

| Dataset | K optimal (coude) | K optimal (silhouette) | K réel | Meilleure métrique ARI | Meilleure métrique Silhouette | Meilleure métrique Inertie |
|---------|-------------------|------------------------|--------|------------------------|-------------------------------|----------------------------|
| Iris | 3 | 2 | 3 | K=3 (0.62) | K=2 (0.58) | K=3 | 
| Breast Cancer | 2 | 2 | 2 | K=2 (0.68) | K=2 (0.34) | K=3 |
| Wine | 3 | 3 | 3 | K=3 (0.90) | K=3 (0.28) | K=3 |
| Mall Customers | 5 | 6 | N/A | N/A | K=6 (0.42) | K=6 |

## Analyse par dataset

### Dataset Iris

```
Résumé des résultats:
   K                  Impl       ARI     Inertia  Silhouette
0  3         Notre K-means  0.592333  140.032753    0.463042
1  3  Scikit-learn K-means  0.620135  139.820496    0.459948
2  2         Notre K-means  0.568116  222.361705    0.581750
3  2  Scikit-learn K-means  0.568116  222.361705    0.581750
```

**Observations**:
- Les métriques ne concordent pas sur le meilleur K
- La méthode du coude identifie K=3 (nombre réel d'espèces)
- La silhouette suggère K=2, probablement car les classes Versicolor et Virginica se chevauchent
- Notre implémentation donne des résultats comparables à scikit-learn
- Pour K=2, les deux implémentations donnent exactement les mêmes résultats

### Dataset Breast Cancer

```
Résumé des résultats:
   K                  Impl       ARI       Inertia  Silhouette
0  2         Notre K-means  0.676505  11595.683313    0.344734
1  2  Scikit-learn K-means  0.653625  11595.526607    0.343382
2  3         Notre K-means  0.510671  10061.797818    0.314384
3  3  Scikit-learn K-means  0.510671  10061.797818    0.314384
```

**Observations**:
- Les méthodes du coude et de la silhouette identifient toutes deux K=2 (nombre réel de classes)
- Notre implémentation obtient un meilleur ARI que scikit-learn pour K=2
- L'inertie suggère K=3, mais l'ARI et la silhouette confirment que K=2 est meilleur
- Le score de silhouette n'est pas très élevé (0.34), suggérant un certain chevauchement entre tumeurs malignes et bénignes

### Dataset Wine

```
Résumé des résultats:
   K                  Impl       ARI      Inertia  Silhouette
0  3         Notre K-means  0.897495  1277.928489    0.284859
1  3  Scikit-learn K-means  0.897495  1277.928489    0.284859
2  2         Notre K-means  0.388724  1659.007967    0.268313
3  2  Scikit-learn K-means  0.374314  1658.758852    0.259317
```

**Observations**:
- Toutes les métriques concordent sur K=3 (nombre réel de cépages)
- Excellent ARI de 0.90 pour K=3, indiquant un très bon clustering
- Les deux implémentations donnent exactement les mêmes résultats pour K=3
- Pour K=2, notre implémentation obtient de meilleurs scores sur toutes les métriques
- Score de silhouette modeste (0.28), suggérant une certaine proximité entre les types de vins

### Dataset Mall Customers

```
Résumé des résultats:
   K                  Impl     Inertia  Silhouette
0  6         Notre K-means  139.714290    0.424064
1  6  Scikit-learn K-means  139.567300    0.422582
2  5         Notre K-means  173.405443    0.409395
3  5  Scikit-learn K-means  173.373720    0.409290
```

**Observations**:
- La méthode du coude suggère K=5 et la silhouette suggère K=6
- Les deux métriques d'évaluation (inertie et silhouette) indiquent que K=6 est meilleur
- Notre implémentation obtient un score de silhouette légèrement meilleur que scikit-learn
- L'absence de classes rend l'évaluation plus subjective



## Conclusion et observations générales

1. La méthode du coude et la silhouette concordent pour Breast Cancer (K=2) et Wine (K=3), mais pas pour Iris et Mall Customers.

2. Pour les datasets Iris, Wine et Breast Cancer, connaître le nombre réel de classes aide à valider les méthodes.

3. La méthode de la silhouette favorise parfois des valeurs de K plus petites quand les classes se chevauchent (cas d'Iris).

4. Notre algorithme est performant et donne des résultats proches ou parfois meilleurs que scikit-learn.

5. Pour Mall Customers, sans connaitre le nombre réel de classes, il est difficile d'attribuer un seule nombre optimal de cluster.

Ces résultats confirment l'importance de combiner plusieurs méthodes pour déterminer le nombre optimal de clusters, et de valider avec une connaissance préalable du domaine quand c'est possible.
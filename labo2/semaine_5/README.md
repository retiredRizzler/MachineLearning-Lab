# Rapport de la Semaine 5 - K-means vs K-means++

## Introduction

Cette semaine, nous avons comparé l'algorithme K-means standard (initialisation aléatoire) avec sa version améliorée K-means++ (initialisation optimisée) sur les mêmes datasets que la semaine précédente. L'objectif était d'évaluer si K-means++ apporte des améliorations significatives en termes de:
- Performance (ARI, inertie, silhouette)
- Convergence (nombre d'itérations)
- Stabilité (plusieurs résultats avec différentes initialisations)

## Tableau récapitulatif des résultats

| Dataset | K optimal | K-means Standard (inertie) | K-means++ (inertie) | K-means Standard (silhouette) | K-means++ (silhouette) | Itérations Standard | Itérations K-means++ |
|---------|-----------|----------------------------|---------------------|-------------------------------|------------------------|---------------------|----------------------|
| Iris | 3 | 140.17 | 150.28 | 0.460 | 0.463 | 5.8 | 4.2 |
| Breast Cancer | 2 | 11595.62 | 11595.78 | 0.344 | 0.344 | 7.8 | 7.0 |
| Wine | 3 | 1347.71 | 1278.34 | 0.274 | 0.285 | 6.8 | 5.6 |
| Mall Customers | 6 | 158.43 | 150.23 | 0.371 | 0.401 | 8.0 | 8.2 |

## Analyse par dataset

### Dataset Iris

```
Analyse de la convergence:
Nombre d'itérations pour K-means standard: 5
Nombre d'itérations pour K-means++: 4
Différence: 1 itérations

Comparaison de la stabilité (écart-types):
     Métrique  Écart-type K-means  Écart-type K-means++  Ratio de stabilité
0         ARI            0.025437              0.087248            3.429916
1     Inertie            0.419115             22.783178           54.360228
2  Silhouette            0.003230              0.009413            2.914599
3  Iterations            1.788854              0.836660            0.467707
```

**Observations**:
- K-means++ converge légèrement plus rapidement (1 itération de moins)
- Curieusement, K-means++ montre une plus grande variabilité pour ARI, inertie et silhouette
- Le seul avantage en stabilité concerne le nombre d'itérations, où K-means++ est plus stable
- K-means standard semble plus adapté à ce dataset, ce qui est surprenant

### Dataset Breast Cancer

```
Analyse de la convergence:
Nombre d'itérations pour K-means standard: 8
Nombre d'itérations pour K-means++: 7
Différence: 1 itérations

Comparaison de la stabilité (écart-types):
     Métrique  Écart-type K-means  Écart-type K-means++  Ratio de stabilité
0         ARI            0.012532              0.010222            0.815671
1     Inertie            0.085831              0.310521            3.617803
2  Silhouette            0.000741              0.001009            1.361734
3  Iterations            2.167948              3.082207            1.421716
```

**Observations**:
- K-means++ converge légèrement plus rapidement (1 itération de moins)
- K-means++ est plus stable pour l'ARI (ratio < 1)
- K-means standard est plus stable pour l'inertie, la silhouette et le nombre d'itérations
- Les deux méthodes aboutissent à la même distribution des diagnostics dans les clusters
- Les différences de performance sont minimes sur ce dataset binaire

### Dataset Wine

```
Analyse de la convergence:
Nombre d'itérations pour K-means standard: 7
Nombre d'itérations pour K-means++: 7
Différence: 0 itérations

Comparaison de la stabilité (écart-types):
     Métrique  Écart-type K-means  Écart-type K-means++  Ratio de stabilité
0         ARI            0.225815              0.007645            0.033856
1     Inertie          150.755175              0.911271            0.006045
2  Silhouette            0.022812              0.000196            0.008580
3  Iterations            1.303840              1.816590            1.393261
```

**Observations**:
- Pas de différence dans le nombre d'itérations pour la convergence
- K-means++ montre une stabilité remarquable pour l'ARI, l'inertie et la silhouette
- Les ratios très faibles (< 0.05) indiquent que K-means++ est ~20-150 fois plus stable
- K-means standard montre une légère meilleure stabilité pour le nombre d'itérations
- K-means++ est clairement supérieur pour ce dataset avec 13 caractéristiques

### Dataset Mall Customers

```
Analyse de la convergence:
Nombre d'itérations pour K-means standard: 10
Nombre d'itérations pour K-means++: 13
Différence: -3 itérations

Comparaison de la stabilité (écart-types):
     Métrique  Écart-type K-means  Écart-type K-means++  Ratio de stabilité
0     Inertie           11.281878             10.192501            0.903440
1  Silhouette            0.035510              0.017598            0.495581
2  Iterations            2.000000              3.271085            1.635543
```

**Observations**:
- K-means++ nécessite plus d'itérations pour converger (+3)
- K-means++ est plus stable pour l'inertie et surtout pour la silhouette (ratio ~0.5)
- K-means standard est plus stable pour le nombre d'itérations
- K-means++ obtient une meilleure inertie (150.23 vs 158.43) et silhouette (0.401 vs 0.371)

## Conclusion et observations générales

1. **Performance**:
   - K-means++ surpasse K-means standard pour Wine et Mall Customers
   - Les performances sont comparables pour Breast Cancer
   - K-means standard semble légèrement meilleur pour Iris

2. **Convergence**:
   - K-means++ converge généralement plus rapidement (sauf pour Mall Customers)
   - L'avantage en termes d'itérations est généralement faible (0-1 itération)

3. **Stabilité**:
   - K-means++ montre une stabilité exceptionnelle pour Wine
   - K-means++ est également plus stable pour Mall Customers
   - Les résultats sont mitigés pour Breast Cancer
   - K-means++ est étonnamment moins stable pour Iris

4. **Relation avec la complexité du dataset**:
   - L'avantage de K-means++ semble augmenter avec la dimensionnalité (nombre de caractéristiques)
   - Wine (13 caractéristiques) montre le plus grand bénéfice
   - Mall Customers (3 caractéristiques) montre un bénéfice modéré
   - Breast Cancer (30 caractéristiques) montre un bénéfice limité, probablement en raison de sa nature binaire

5. **Recommandations**:
   - Pour des datasets complexes ou de haute dimension: privilégier K-means++
   - Pour des datasets simples ou de faible dimension: K-means standard peut suffire
   
En conclusion, K-means++ apporte généralement une amélioration, mais varie selon la nature et la complexité du dataset. Il semble particulièrement utile pour les datasets à classes multiples avec un nombre élevé de caractéristiques.
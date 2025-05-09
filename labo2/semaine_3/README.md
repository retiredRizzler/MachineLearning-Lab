# Rapport de la Semaine 3 - Comparaison entre Kmeans Scikit-learn et notre Kmeans

## Tableau Récapitulatif de l'Analyse des Résultats (Semaine 3)

| Dataset | Valeur de K | Implémentation | ARI | Inertie | Commentaires |
|---------|-------------|----------------|-----|---------|--------------|
| **Iris** | K=2 | Notre K-means | 0.5681 | 222.36 | Les deux implémentations donnent des résultats identiques |
|  | K=2 | Scikit-learn | 0.5681 | 222.36 |  |
|  | K=3 | Notre K-means | 0.5923 | 140.03 | Scikit-learn légèrement meilleur en ARI |
|  | K=3 | Scikit-learn | 0.6201 | 139.82 | **Meilleur choix (K=3)**, correspond aux 3 espèces d'iris |
| **Breast Cancer** | K=2 | Notre K-means | 0.6765 | 11595.68 | Notre implémentation meilleure en ARI |
|  | K=2 | Scikit-learn | 0.6536 | 11595.53 | **Meilleur choix (K=2)**, correspond aux 2 types de cancer (malin ou bénin) |
|  | K=3 | Notre K-means | 0.5107 | 10061.80 | Les deux implémentations donnent des résultats identiques |
|  | K=3 | Scikit-learn | 0.5107 | 10061.80 |  |
| **Wine** | K=2 | Notre K-means | 0.3887 | 1659.01 | Notre implémentation légèrement meilleure en ARI |
|  | K=2 | Scikit-learn | 0.3743 | 1658.76 |  |
|  | K=3 | Notre K-means | 0.8975 | 1277.93 | Les deux implémentations donnent des résultats identiques |
|  | K=3 | Scikit-learn | 0.8975 | 1277.93 | **Meilleur choix (K=3)**, correspond aux 3 types de vins |
| **Mall Customers** | K=3 | Notre K-means | - | 301.91 | Valeurs manquantes imputées dans Age et Annual Income |
|  | K=3 | Scikit-learn | - | 301.91 | Les deux implémentations donnent des résultats identiques |
|  | K=5 | Notre K-means | - | 173.41 | Inertie fortement réduite par rapport à K=3 |
|  | K=5 | Scikit-learn | - | 173.37 | **Meilleur choix (K=5)** selon l'inertie |

**Observations globales:**
- Notre implémentation est très comparable à celle de scikit-learn
- Pour les datasets avec classes connues, le meilleur K correspond au nombre réel de classes
- Pour Mall Customers, K=5 semble être un choix plus approprié que K=3 d'après l'inertie, mais cette conclusion est basée uniquement sur l'inertie car nous n'avons pas de labels pour calculer l'ARI
- L'introduction et l'imputation de valeurs manquantes dans Mall Customers n'a pas empêché l'algorithme de fonctionner correctement
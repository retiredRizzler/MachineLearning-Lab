# Laboratoire Pacman - Agents Rationnels

## Vue d'ensemble
Ce laboratoire consiste en l'implémentation de différents types d'agents rationnels pour le jeu Pacman. Ces agents utilisent des algorithmes d'intelligence artificielle pour naviguer efficacement dans le labyrinthe, éviter les fantômes et manger toutes les gommes.

## Agents implémentés

### ReflexAgent
Un agent qui évalue chaque action possible en fonction de l'état du jeu résultant. Cette évaluation prend en compte:
- La proximité des fantômes (punition pour être trop proche)
- La proximité de la nourriture (récompense pour être proche)
- Les récompenses pour manger de la nourriture
- Un traitement spécial pour les fantômes effrayés

### MinimaxAgent
Un agent qui utilise l'algorithme Minimax pour anticiper plusieurs coups à l'avance, en supposant que les fantômes cherchent à minimiser son score. L'agent:
- Explore les actions possibles jusqu'à une profondeur définie
- Suppose que les fantômes agissent de manière optimale contre lui
- Choisit l'action qui maximise son score minimum possible

### AlphaBetaAgent
Une amélioration de l'agent Minimax qui utilise l'élagage alpha-bêta pour optimiser la recherche:
- Réduit considérablement le temps de calcul
- Permet d'explorer des profondeurs plus importantes
- Conserve le même comportement que Minimax

### ExpectimaxAgent
Un agent qui suppose que les fantômes se déplacent aléatoirement plutôt que de manière optimale:
- Calcule l'espérance mathématique (moyenne) des scores pour les actions des fantômes
- Est moins pessimiste que Minimax face à des adversaires non optimaux
- Prend plus de risques quand cela est avantageux

### Fonction d'évaluation améliorée
Une fonction d'évaluation avancée qui considère plusieurs facteurs:
- Distance à la nourriture la plus proche
- Nombre de gommes restantes
- Position des fantômes (normaux et effrayés)
- Présence et proximité des capsules

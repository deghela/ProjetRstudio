
# Documentation - Tester le positionnement des dames sur un échiquier en R

## Introduction
Cette documentation explique comment écrire un script en langage R pour tester le positionnement de plusieurs dames sur un échiquier sans qu'elles se mangent mutuellement. Le problème des huit dames est un problème classique en informatique et en mathématiques.

## Prérequis
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Une installation de R sur votre système.
- Des connaissances de base en programmation en R.

## Objectif
L'objectif de ce script est de déterminer toutes les combinaisons possibles pour placer plusieurs dames sur un échiquier de manière à ce qu'elles ne menacent pas mutuellement.

## Étapes
Nous allons suivre les étapes suivantes pour résoudre le problème des dames :
1. Création d'un échiquier virtuel en R.
2. Génération de toutes les combinaisons possibles de placement de dames.
3. Vérification de chaque combinaison pour s'assurer qu'aucune dame ne menace les autres.
4. Affichage des solutions valides.

## Code en R
Voici un exemple de code en R pour résoudre le problème des huit dames :

```R
Mon code ici...
```
## Développement
1. La fonction trouver_solutions(x, y)
Cette fonction principale tente de trouver toutes les configurations possibles pour placer 10 dames sur un échiquier de taille x lignes et y colonnes sans qu'elles ne se menacent mutuellement.
Elle initialise une matrice cases_menacees pour compter le nombre de fois où chaque case est menacée par une dame.
Elle appelle la fonction interne placer_dames pour placer les dames sur l'échiquier.

2. est_valide(placement, colonne, ligne) :
Cette fonction interne vérifie si une dame peut être placée dans une certaine colonne/ligne sans se menacer mutuellement avec d'autres dames déjà placées.
Elle vérifie les règles des échecs pour déterminer si le placement est valide en évitant les menaces diagonales, verticales et horizontales.

3.fonction placer_dames(placement, colonne) :
Cette fonction est récursive et essaie de placer les 10 dames en itérant sur chaque colonne.
Si une solution est trouvée (lorsque colonne > x), elle met à jour la matrice cases_menacees pour indiquer les cases menacées par chaque dame placée.
Elle utilise la récursivité pour explorer toutes les combinaisons possibles de placements valides.

4. resultats <- trouver_solutions(10, 10):
Appelle la fonction principale trouver_solutions avec des dimensions de 10x10 pour tenter de résoudre le problème des 10 dames sur un échiquier 10x10.

5. La fonction renvoie le nombre de solutions trouvées et la liste complète des solutions.

Visualisation avec ggplot2 :
Une fois les solutions calculées, le code utilise ggplot2 pour créer une heatmap (geom_tile()) basée sur la matrice cases_menacees. Cette heatmap représente visuellement les cases les plus touchées par les dames.Ces fonctions et le code global visent à trouver toutes les configurations possibles pour placer 10 dames sur un échiquier 10x10 sans qu'elles ne se menacent mutuellement, tout en visualisant les zones où les dames menacent d'autres cases.



6. Ensuite, le code utilise le package "tidyverse" pour créer un heatmap (carte thermique) qui représente les solutions possibles. Il crée un dataframe à partir des solutions, compte combien de fois chaque position est occupée, puis crée un heatmap en utilisant "ggplot2".
## Exécution
1. Lancer R Studio
2. Créer un nouveau fichier 
3. Copier/Coller sur le fichier 
4. A la ligne 40 donner une valeur à x et à y dans pour tester tester les solutions suivant la taille de l'échiquier qui vous convient e.g: trouver_solutions(10,10) pour une grille de 10 fois 10 
5. En haut à droite de la page, cliquez sur 'Run' pour déboguer le programme
Expliquez comment exécuter votre script en R pour tester le positionnement des dames.

## Résultats
Résultat de l'exécution pour une grille de 10 fois 10



...

[[722]]
 [1] 9 7 4 1 3 0 6 8 2 5

[[723]]
 [1] 9 7 4 1 3 0 6 8 5 2

[[724]]
 [1] 9 7 4 2 0 5 1 8 6 3

 Le total des combinaisons possibles est de 724

## Conclusion
Le code fourni tente de résoudre le problème complexe des 10 dames sur un échiquier de taille 10x10. Il utilise une approche récursive pour trouver toutes les configurations possibles où les 10 dames peuvent être placées sans se menacer mutuellement. Cependant, ce problème est extrêmement complexe, ce qui rend la recherche de toutes les solutions pratiquement impossible en raison du grand nombre de combinaisons à explorer. La visualisation proposée à l'aide de ggplot2 pour créer une heatmap des cases menacées par les dames offre un moyen graphique de comprendre les zones d'impact des dames sur l'échiquier.
En conclusion, le problème des 10 dames sur un échiquier de taille 10x10 est extrêmement difficile à résoudre complètement de manière exhaustive, et des méthodes plus avancées seraient nécessaires pour obtenir des solutions ou des aperçus significatifs. 
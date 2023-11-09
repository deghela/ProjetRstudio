
# Documentation - Tester le positionnement des dames sur un échiquier en R

## Introduction
Cette documentation explique comment écrire un script en langage R pour tester le positionnement de plusieurs dames sur un échiquier sans qu'elles se mangent mutuellement. Le problème des huit dames est un problème classique en informatique et en mathématiques.

## Prérequis
- Avant de commencer, assurez-vous d'avoir les éléments suivants :
Téléchargement de R : Accédez au site officiel de R (https://www.r-project.org/) et choisissez la version correspondant à votre système d'exploitation (Windows, macOS, Linux). Suivez les instructions pour télécharger et installer R.
IDE R : Bien que l'utilisation de R puisse se faire dans un éditeur de texte, il est souvent plus convivial d'utiliser un environnement de développement intégré (IDE) comme RStudio (https://www.rstudio.com/products/rstudio/download/) qui offre des fonctionnalités supplémentaires et facilite l'écriture de code R.
- Quelques packages à installer :
- Tidyverse : Un ensemble de packages pour la science des données, incluant ggplot2 pour la visualisation et dplyr pour la manipulation de données. ```install.packages("tidyverse")```
- ggplot2 : Pour créer des graphiques et des visualisations.
```install.packages("ggplot2")```
-   Pour manipuler les données de manière efficace.```install.packages("dplyr")```

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
```
## Développement
1. La fonction trouver_solutions(x, y)
 est la fonction principale. Elle prend deux arguments, x et y, qui représentent le nombre de lignes et de colonnes de l'échiquier respectivement.
La fonction initialise deux variables : solutions pour compter le nombre total de solutions et all_solutions, une liste pour stocker les positions des dames pour chaque solution. exple de fonction:
```R
trouver_solutions <- function(x, y) {
  solutions <- 0
  all_solutions <- list()
  
  est_valide <- function(placement, colonne, ligne) {
    i <- 1
    while (i < colonne) {
      if (placement[i] == ligne || 
          placement[i] - i == ligne - colonne || 
          placement[i] + i == ligne + colonne ||
          abs(placement[i] - ligne) == abs(i - colonne)) { # Menace diagonale
        return(FALSE)
      }
      i <- i + 1
    }
    return(TRUE)
  }
```

2. La fonction est_valide 
vérifie si une dame peut être placée dans une certaine colonne et ligne sans menacer les autres dames en se basant sur les règles des échecs. Elle prend en entrée le placement actuel, la colonne et la ligne que l'on souhaite vérifier.

3. fonction placer_dames
est une fonction récursive qui essaie de placer les dames sur l'échiquier. Si une solution est trouvée (toutes les dames placées sans se menacer mutuellement), elle est ajoutée à all_solutions.
exple :
```R

  placer_dames <- function(placement, colonne = 1) {
    if (colonne > x) {
      solutions <<- solutions + 1
      all_solutions[[solutions]] <<- placement
    } else {
      ligne <- 1
      while (ligne <= y) {
        if (est_valide(placement, colonne, ligne)) {
          placement[colonne] <- ligne
          placer_dames(placement, colonne + 1)
        }
        ligne <- ligne + 1
      }
    }
  }

```
   Création de la heatmap
Une fois toutes les solutions obtenues, un nouveau tableau "heatmap_data" est créé pour stocker le nombre d'occurrences de chaque case touchée par les dames.
Le tableau "heatmap_data" est rempli en parcourant les positions des dames pour chaque solution.
Ensuite, ce tableau est mis au format approprié ("melted") pour être utilisé avec "ggplot2".
Enfin, "ggplot" crée une heatmap où la couleur de chaque case représente le nombre de dames qui la touchent.
exple de cr&ation de heatmap:
```R
heatmap_data <- matrix(0, nrow = 7, ncol = 17)
i <- 1
max_iterations <- 1000  # Limite le nombre d'itérations

while (i <= length(resultats) && i <= max_iterations) {
  positions <- resultats[[i]]
  j <- 1
  while (j <= length(positions)) {
    heatmap_data[j, positions[j]] <- heatmap_data[j, positions[j]] + 1
    j <- j + 1
  }
  i <- i + 1
}
```

Visualisation avec ggplot2 :
Une fois les solutions calculées, le code utilise ggplot2 pour créer une heatmap (geom_tile()) basée sur la matrice cases_menacees. Cette heatmap représente visuellement les cases les plus touchées par les dames.Ces fonctions et le code global visent à trouver toutes les configurations possibles pour placer 10 dames sur un échiquier 10x10 sans qu'elles ne se menacent mutuellement, tout en visualisant les zones où les dames menacent d'autres cases.

La fonction trouver_solutions cherche à résoudre le problème des dames placées sur un échiquier sans se menacer mutuellement. Une fois les solutions trouvées, le code crée une heatmap pour visualiser quelles cases sont les plus touchées par les dames dans ces solutions.

4. Ensuite, le code utilise le package "tidyverse" pour créer un heatmap (carte thermique) qui représente les solutions possibles. Il crée un dataframe à partir des solutions, compte combien de fois chaque position est occupée, puis crée un heatmap en utilisant "ggplot2".
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
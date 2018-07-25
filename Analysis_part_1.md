Le package datasets contient plusieurs dataset

    data(package="datasets")
    data(trees)

Nous allons nous intéresser au dataset "Trees"

    ##   Girth Height Volume
    ## 1   8.3     70   10.3
    ## 2   8.6     65   10.3
    ## 3   8.8     63   10.2
    ## 4  10.5     72   16.4
    ## 5  10.7     81   18.8
    ## 6  10.8     83   19.7

    ##    Girth Height Volume
    ## 26  17.3     81   55.4
    ## 27  17.5     82   55.7
    ## 28  17.9     80   58.3
    ## 29  18.0     80   51.5
    ## 30  18.0     80   51.0
    ## 31  20.6     87   77.0

    ## [1] "Girth"  "Height" "Volume"

On a un dataset qui explique l'évolution d'un arbre Voici les 3
variables que nous allons étudier : la circonférence, la hauteur et le
volume de l'arbre.

On va ainsi déterminer la structure du dataset

    str(trees)

    ## 'data.frame':    31 obs. of  3 variables:
    ##  $ Girth : num  8.3 8.6 8.8 10.5 10.7 10.8 11 11 11.1 11.2 ...
    ##  $ Height: num  70 65 63 72 81 83 66 75 80 75 ...
    ##  $ Volume: num  10.3 10.3 10.2 16.4 18.8 19.7 15.6 18.2 22.6 19.9 ...

    summary(trees)

    ##      Girth           Height       Volume     
    ##  Min.   : 8.30   Min.   :63   Min.   :10.20  
    ##  1st Qu.:11.05   1st Qu.:72   1st Qu.:19.40  
    ##  Median :12.90   Median :76   Median :24.20  
    ##  Mean   :13.25   Mean   :76   Mean   :30.17  
    ##  3rd Qu.:15.25   3rd Qu.:80   3rd Qu.:37.30  
    ##  Max.   :20.60   Max.   :87   Max.   :77.00

Exploration du jeu de données
-----------------------------

On peut voir qu'on a un dataset de 31 lignes et 3 colonnes les variables
Girth, Height et Volume sont des variables quantitatives

On a déterminés les stats descriptives des 3 variables à travers la
médiane, la moyenne, le minimum et le maximum , le 1er quartile et le 3e
quartile.

    dim(trees)

    ## [1] 31  3

nuage de points
---------------

    plot(trees, col = 1:5)

![](Analysis_part_1_files/figure-markdown_strict/unnamed-chunk-5-1.png)

On peut voir le nuage de points des différentes variables ainsi que leur
évolution.

Essayons de voir la correlation entre les différentes variables

    cor(trees)

    ##            Girth    Height    Volume
    ## Girth  1.0000000 0.5192801 0.9671194
    ## Height 0.5192801 1.0000000 0.5982497
    ## Volume 0.9671194 0.5982497 1.0000000

![](Analysis_part_1_files/figure-markdown_strict/unnamed-chunk-7-1.png)![](Analysis_part_1_files/figure-markdown_strict/unnamed-chunk-7-2.png)![](Analysis_part_1_files/figure-markdown_strict/unnamed-chunk-7-3.png)

Voici la distribution de la hauteur de l'arbre.

Visualisation du dataset

    library(ggplot2)
    ggplot(data = trees) +
      geom_point(aes(x = trees$Volume, y = trees$Height), colour = "yellow") +
      geom_line(aes(x = trees$Volume, y = trees$Height), colour = "blue") +
      ggtitle("Height vs Volume") +
      xlab("Volume") +
      ylab("Height")

![](Analysis_part_1_files/figure-markdown_strict/unnamed-chunk-8-1.png)

Boites à moustaches des stats descriptives pour les 3 variables

    boxplot(trees, col = 1:3)

![](Analysis_part_1_files/figure-markdown_strict/unnamed-chunk-9-1.png)

    library(ggplot2)
    ggplot(data = trees) +
      geom_point(aes(x = trees$Girth, y = trees$Height), colour = "red") +
      geom_line(aes(x = trees$Girth, y = trees$Height), colour = "green") +
      ggtitle("Height vs Girth") +
      xlab("Girth") +
      ylab("Height")

![](Analysis_part_1_files/figure-markdown_strict/unnamed-chunk-10-1.png)

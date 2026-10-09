# Top 10 des communes d'Île-de-France les moins disponibles en Vélib'

**Christella DAVID — Santatriniaina RASOLOFOMANANA — VCOD Gr33**

![Top 10 des communes les moins disponibles en Vélib'](image1.png)

**Source de données :** [Jeu de données – Vélib' – Vélos et bornes – Disponibilité temps réel | data.gouv.fr](https://www.data.gouv.fr/datasets/velib-velos-et-bornes-disponibilite-temps-reel)

## Ce qu'on a utilisé

On a utilisé Power BI Desktop pour construire le graphique et calculer notre indicateur. On a préparé les données avec Power Query, puis on a calculé le taux de disponibilité en pourcentage avec le langage DAX. Pour cela, on s'est servi de trois colonnes : le nom de la commune, le nombre total de vélos disponibles et la capacité de la station. Pour la visualisation, on a choisi un graphique à barres horizontales, avec un filtre « Limite de données » (Bas 10) et un tri croissant.

## Ce qu'on a fait

D'abord, on a calculé le taux de disponibilité. On a pris le nombre de vélos disponibles et on l'a divisé par la capacité des stations :

```dax
Ratio =
DIVIDE(
    SUM(velib[Nombre total vélos disponibles]),
    SUM(velib[Capacité de la station]),
    0
)
```

Ensuite, on a construit le graphique. On a mis les communes sur l'axe vertical et le taux de disponibilité sur l'axe horizontal. Puis on a gardé seulement les 10 communes avec le taux le plus bas. On a trié du plus petit au plus grand, pour que la commune la moins disponible soit tout en haut.

Pour lire une valeur, il faut comprendre que le taux montre la part des places occupées par un vélo disponible. Au Pré-Saint-Gervais, le taux est de 2,38 %, soit environ 2 vélos pour 100 places : les stations sont presque vides. À Montreuil, il est de 16,18 %, soit environ 16 vélos pour 100 places.

## À quoi ça sert ?

**Pourquoi c'est utile.** Ce graphique montre les communes où l'on a le moins de chances de trouver un vélo. Il montre aussi de gros écarts : au Pré-Saint-Gervais, il y a presque 7 fois moins de vélos qu'à Montreuil. On voit donc tout de suite où l'offre ne répond pas à la demande.

**L'utilisateur cible.** Ce graphique s'adresse surtout au gestionnaire du service, c'est-à-dire Île-de-France Mobilités et l'opérateur Vélib' Métropole, et aux services mobilité des communes. Les usagers réguliers peuvent aussi s'en servir pour savoir où le service est moins fiable.

**Effet sur la décision du lecteur.** Avec ce classement, le gestionnaire sait où agir en premier. Il peut envoyer plus de vélos dans les communes les plus vides, comme Le Pré-Saint-Gervais, Chaville ou Villejuif. Il peut aussi se demander si certaines stations sont bien placées ou assez grandes. Et en refaisant le graphique plus tard, il voit si ses actions ont eu un effet.

**Pourquoi cette visualisation.** On a choisi un graphique à barres horizontales parce qu'il permet de comparer facilement des communes. Le tri met la commune la plus en difficulté en premier. Enfin, on a gardé seulement 10 communes pour ne pas surcharger le graphique et se concentrer sur les cas les plus urgents.

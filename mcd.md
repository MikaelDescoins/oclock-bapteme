# Retour concernant l'exercice MCD

> Je trouve que tu t'en es bien sorti sur cet exercie. La modélisation me paraît cohérente. J'ai identifié une petite erreur de cardinalité et quelques améliorations possibles.
> Je te partage ci-dessous ma version de l'exercice ainsi que mes retours :

Comme tu peux le remarquer nos résultats sont très proches. 
J'identifie une différence sur ton rendu au niveau des cardinalités entre les entités PRODUCT et USER sur la relation de LIKE.
En effet tu as vu juste, il s'agit bien d'une relation ManyToMany. En revanche la cardinalité ne peut être 1,1.
Un utilisateur peut LIKER plusieurs produits s'il le souhaite mais il n'est pas obligé. On peut donc traduire ce comportement par une cardinalité minimale de 0 et maximale de N
Un produit peut être LIKÉ par l'intégralité des utilisateurs. On peut également avoir un produit LIKÉ par personnes. On a donc une cardinalité minimale de 0 et maximale de N


## Quelques ajustements sur ton rendu final : 

Les relations sont en général représentées par des bords arrondis.
Pour faciliter la modélisation je t'invite à essayer l'outil gratuit draw.io


Tu as enregistré sur ton entité ORDER un champ 'amount_total'. 
L'idée en bonne, en revanche il s'agit d'une donnée que l'on pourra calculer par la suite grâce aux relations 
entre une commande et les produits. 
En règle générale on évite de stocker directement en BDD des données qui peuvent être calculées (hors cas 
exceptionnels et spécifiques de gestion) pour éviter de surcharger les tables.

Je me permets également d'ajouter quelques éléments supplémentaires : 
Même si l'on souhaite garder la simplicité du projet, je pense qu'il peut être utile de récupérer quelques informations :
- la date a laquelle un utilisateur a liké un produit
- la quantité d'un produit dans une commande

Comme tu as pu le voir, ces propriétés sont ajoutées directement dans la relation. En effet on peut préciser au niveau 
de la relation les informations complémentaires dont on a besoin dans notre logique de conception.

> Si tu souhaites revoir les notions MCD - Merise et aller un petit peu plus loin (MLD) je te partage une courte vidéo qui pourra t'intéresser : 
> https://www.youtube.com/watch?v=OxJo051TMr8&t=448s

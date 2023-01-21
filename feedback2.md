# Commentaire général 💬
* * *

Hello 👋 J'ai bien reçu ton projet, je vais te partager mes retours dans ce compte rendu.

J'ai bien réussi à le faire fonctionner, je pense que tu as eu un peu de mal avec les tâches à réaliser sur cet exercice.

Tout d'abord bravo pour la gestion de tes Views, tu as très bien segmenté ton code et tu as dû remarquer que tu es proche de la correction pour les pages que tu as implémentées.
Pour le reste, tu as parfaitement réussi la liste des Students & Teachers. La notion de récupération en BDD des entités me semble comprise.

En revanche tu as eu un peu plus de mal sur la création. Tu as tout juste commencé la mise en place de la création d'un Teacher.
As-tu manqué de temps pour réaliser la suite ?
J'espère que la correction t'a permis de mieux comprendre certaines notions.

Je vais à travers ce feedback te partager mes retours sur ton code et essayer de te débloquer sur
la création d'une entité. L'idée est la suivante : j'aimerais que tu puisses essayer de nouveau de réaliser les consignes de l'exercice (modification/suppression) et
revenir me voir si tu n'y arrives pas.

Tu n'es pas le seul dans ce cas, on va peut-être prévoir une session de travail pour revoir ces sujets.

# Points relevés ✍🏼
* * *

## Gestion de l'ajout d'un Teacher

Je vais te partager les différentes étapes à réaliser pour construire la création d'un Teacher. Tu peux également regarder
comment est-ce que cela a été fait sur la correction. J'aimerais que tu essayes de le mettre en place sur ton projet et me dire si tu y es parvenu.
Tu as parfaitement construit la route d'ajout en GET (affichage du formulaire d'ajout). Pour la suite :

>1/ Dans le Model Teacher > créer une méthode insert() qui va permettre d'ajouter l'entité en BDD. Cette méthode devra :
>- Récupérer l'objet PDO pour discuter avec la BDD
>- Construire la requête SQL d'ajout (CREATE ...) en lui donnant les données de l'entité comme paramètres
>- Exécuter cette requête
>- Retourner true si tout s'est bien passé
>- Sinon retourner false

>2/ Dans le index.php > Créer une nouvelle route en POST pour gérer la soumission du formulaire

>3/ Dans le TeacherController > implémenter la methode de la nouvelle route POST. Cette méthode devra : 
>- Récupérer les différentes données soumises par le visiteur via le formulaire
>- Vérifier si les données sont correctes. Si non : lister les erreurs dans un tableau
>- Si les données sont bonnes : Créer un nouveau Teacher et lui donner les données le concernant. Faire appel à la méthode `insert()` précédemment créée. Gérer le succès ou les erreurs
>- Si les données sont incorrectes ou manquantes : rediriger vers la page d'ajout en affichant les différentes erreurs

# Pour continuer 🎯
* * *

Tu as normalement réussi à débloquer la création d'un nouveau Teacher. J'aimerais que tu
essayes de nouveau la suite des consignes. Si jamais tu bloques sur une notion, n'hésite pas à regarder la correction. Et si tu n'y arrives pas, n'hésite pas à revenir vers moi.

## Créer un Student

La logique est la même que pour Teacher à une différence près : le fait d'assigner un étudiant à un Teacher existant.
Sur la page GET tu auras besoin des Teachers en BDD pour pouvoir afficher un select complet des professeurs.
La correction pourra t'être utile :) 

## Modifier un Student & Teacher

Pour cela tu vas devoir créer une page qui va ressembler à la page de création à quelques nuances près :
- Le formulaire sera pré-rempli avec les données de l'entité que l'on souhaite modifier (se baser sur l'id passé dans l'url pour identifier l'entité à modifier)
- Lors de la soumission on ne créé pas un nouvel élément, on modifie un élément existant

## Supprimer un Student & Teacher

Pour la suppression:
- les Models devront comporter une méthode de suppression (requête SQL DELETE)
- la methode du Controller devra récupérer l'entité (avec l'id dans l'url) et si elle existe : faire appel à cette methode `delete()`


# PS :
* * *
Je remarque que vous êtes plusieurs à avoir eu du mal sur ce projet. 
Je vais voir avec l'équipe s'il est possible de programmer une session pour revoir les notions clés. 
Je reviens vers vous rapidement.
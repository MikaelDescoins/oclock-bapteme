# Commentaire général 💬
* * *

Merci pour ton message. Je vais, à travers ce document, te faire un retour sur ton projet.
 
D'après ce que je vois, j'imagine que tu as eu un peu de mal sur la réalisation de l'exercice. 

Pour moi, tu as parfaitement réussi l'affichage des `Students` & des `Teachers`. Je pense que cette notion est 
bien comprise.

En revanche, pour la création/modification/suppression, je pense que l'on va pouvoir réaborder certaines notions.

J'ai vu que tu as essayé de réaliser l'ajout des Students et des Teacher. Je pense que tu es resté bloqué sur cette tâche
et tu n'as pas eu le temps de te consacrer aux autres consignes.
J'espère que la correction t'a permis de mieux comprendre certaines notions. 

Je vais à travers ce feedback te partager mes retours sur ton code et essayer de te débloquer sur
la création d'une entité. L'idée est la suivante : j'aimerais que tu essayes de nouveau de réaliser les consignes de l'exercice (modification/suppression) et 
revenir me voir si tu n'y arrives pas.

# Points relevés ✍🏼
* * *

## Gestion des Views

Le premier point que j'aimerai voir avec toi, c'est la façon dont tu as organisé les Views de ce projet. 
Tu as pour chaque fichier reprit l'intégralité du code HTML et tu n'as pas utilisé la logique de réutilisation du code pour les composants communs.
Cela t'a pris, je pense, beaucoup de temps qui aurait été précieux pour aller un peu plus loin dans l'exercice.

Pour rappel : 
Il est important de découper son code HTML en éléments réutilisables pour éviter de dupliquer du code.
Pour cela tu peux séparer tes éléments communs (ex: menu / footer / etc.) dans des fichiers séparés et les appeler dans 
tes fichiers grâce a la fonction `include()`

Prenons l'exemple du menu : avec un fichier commun tu peux modifier les routes à un seul endroit et c'est effectif sur toute ton application.
Cela évite d'avoir des menus avec des routes non fonctionnelles comme c'est le cas aujourd'hui sur ton projet.

N'hésite pas à jeter un oeil à la structure de la correction à ce niveau-là.

## Gestion de l'ajout d'un Student

Pour l'ajout d'un Student, tu t'y es pris correctement. Tu as bien construit ton Model, ton Controller et ton formulaire. 
L'application te retourne cependant une erreur à la soumission car tu essayes de créer en BDD un Student qui ne possède pas de teacher_id.

Pour t'aider je vais te partager la liste des actions que tu vas devoir réaliser pour que cela fonctionne : 

>1/ Dans le StudentController, dans la méthode de gestion de d'ajout d'un Student en méthode `GET`, tu dois récupérer dans une variable l'ensemble des `Teachers` existants en base de données et le transmettre à ta View.

>2/ Dans ta View d'ajout d'un `Student` : au niveau du select d'un `Teacher`, tu dois boucler sur cette nouvelle variable et afficher pour chacun une `<option>` ayant pour value l'id du `Teacher` et en contenu le Nom/prénom

>3/ Dans ton `StudentController` : dans la méthode de gestion de l'ajout du `Student` en méthode `POST` > tu dois ajouter à ton objet `Student` la donnée `teacher_id`

>4/ La dernière étape va être de revoir la méthode `insert()` de ton Model `Student` afin d'intégrer dans ta requête le champ `teacher_id`


# Pour continuer 🎯
* * *

Tu as normalement réussi à débloquer la création d'un nouveau Student. J'aimerais que tu
essayes de nouveau la suite des consignes. Si jamais tu bloques sur une notion, n'hésite pas à regarder la correction. Si tu n'y arrives pas, n'hésite pas à revenir vers moi.

## Créer un Teacher

La logique est la même que pour les étudiants. Ne refais pas la même erreur que pour les Students et sois vigilant à tous les champs obligatoires.

## Modifier un Student & Teacher

Pour cela tu vas devoir créer une page qui va ressembler à la page de création à quelques nuances près :
- Le formulaire sera pré-rempli avec les données de l'entité que l'on souhaite modifier
- Lors de la soumission on ne créé pas un nouvel élément mais on modifie un élément existant

## Supprimer un Student & Teacher

Pour la suppression: 
- les Models devront comporter une méthode de suppression (requête SQL `DELETE`)
- la methode du Controller devra récupérer l'entité (avec l'id dans l'url) et si elle existe : faire appel à cette methode de suppression

# PS : 
* * *

Je remarque que vous êtes plusieurs à avoir eu du mal sur ce projet.
Je vais voir avec l'équipe s'il est possible de programmer une session pour revoir les notions clés.
Je reviens vers vous rapidement.
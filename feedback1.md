# Commentaire général 💬
* * *

Très bon travail 🎉 Je trouve que tu t'en es très bien sorti ! Tu as réalisé les différentes demandes de l'énoncé et 
tu as même développé certains bonus.

J'ai remarqué que la modification d'un Teacher & d'un Student n'était pas fonctionnelle. 
(je te donne une piste de recherche pour résoudre le souci dans mon feedback 😀 )

Je vais également te faire mon retour sur certains éléments du code qui à mon sens peuvent être 
retravaillés ou bien des bonnes pratiques qui peuvent rendre ton code plus lisible et plus clair.

Mais je le répète encore une fois, tu t'en es très bien sorti ! 😎


# Points relevés ✍🏼

---

## Gestion des Models :

### Typage des données

Selon moi, il est important d'ajouter des commentaires sur le type de données de tes entités. 
Aussi bien au niveau de la déclaration des champs que pour les getters & setters.
En effet aujourd'hui cela ne va pas te générer d'erreur, mais pour la suite de ta carrière en développement, tu seras
très probablement amené à utiliser certains frameworks PHP et pour ces derniers le typage est très important.
Je te conseille vivement de prendre cette habitude dès maintenant, cela t'évitera bien des ennuis 😀 

### Fonctions de traitement SQL (insert/update)

Il y a une notion à garder en tête lorsque l'on manipule la base de données : ne jamais faire confiance à l'utilisateur.

En effet, certains utilisateurs peuvent être mal intentionnés et voudront corrompre ta BDD. 
L'une des techniques les plus connues s'appelle l'injection SQL.
Je te partage un court article si tu souhaites en savoir plus : https://www.php.net/manual/fr/security.database.sql-injection.php

Comme tu as pu le voir dans la correction, il est (très) fortement recommandé d'utiliser les fonctions `prepare()` puis `execute()` - 
Ces 2 fonctions vont "échapper" le contenu saisi par l'utilisateur et ainsi éviter d'interpréter des commandes SQL qui auraient pu s'y trouver.
Un autre point important est la façon de transmettre les données reçues par le client dans la requête SQL. 
De ton côté tu les intègres directement :

```php
$sql = "
    INSERT INTO 'teacher' (firstname, lastname, job, status)
    VALUES ('{$this->firstname}','{$this->lastname}','{$this->job}','{$this->status}')
";
```

Dans la correction tu verras que l'on préfère passer par des variables temporaires : 

```php
$sql = '
    INSERT INTO `teacher` (firstname, lastname, job, status)
    VALUES (:firstname, :lastname, :job, :status)
';
```

Puis dans un second temps de renseigner les données de ces variables grâce à la fonction `bindValue()`.
Cette fonction prend en paramètre le nom de la variable inscrite dans la requête SQL ; la donnée à inscrire dans cette variable ; 
le type de données attendu pour ajouter une couche de vérification).

```php 
$pdoStatement->bindValue(':firstname', $this->firstname, PDO::PARAM_STR);
$pdoStatement->bindValue(':lastname', $this->lastname, PDO::PARAM_STR);
$pdoStatement->bindValue(':job', $this->job, PDO::PARAM_STR);
$pdoStatement->bindValue(':status', $this->status, PDO::PARAM_INT);
```

### Fonctions `delete()`

Toutes tes fonctions `delete()` retournent `true`. 
On peut toutefois avoir des erreurs (ex: l'utilisateur passe dans l'url `/teacher/999/delete` alors qu'aucun Teacher ne possède l'id `999`)
Dans ce cas, il serait intéressant de ne pas faire de requête côté SQL et d'afficher une erreur côté utilisateur. 
La correction te sera utile pour cette partie 😉 


## Gestion des Controllers :

### Bonne pratique d'organisation des méthodes 

Pour les controllers qui gèrent le CRUD d'une entité on ordonne en règle générale les méthodes de la manière suivante : 

- Liste (findAll)
- Create (new)
- Show (findBy)
- Update
- Delete

Absolument pas bloquant mais, pour le confort de lecture, c'est une bonne habitude à prendre

### Fonctionnalité d'update Teacher & Student non fonctionnelle

Je ne sais pas si tu as réussi à identifier la raison grâce à la correction. Je te donne une piste de recherche : 
jette un oeil à la route que tu passes à l'attribut action de tes balises `<form>` pour les routes d'update.
Si jamais tu ne trouves pas, n'hésite pas à revenir vers moi 😉

### Amélioration des fonctionnalités création / update

En règle générale on transmet toujours un objet de l'entité aux formulaires (même vide par défaut). Cela permet entre autres de conserver les 
données renseignées par l'utilisateur en cas d'erreur et lui éviter de se retrouver face à un formulaire vide.
La correction te donne normalement les clés pour adapter ton code dans ce sens.

# Pour aller plus loin 🔥

Tu as très bien compris les notions vues cette semaine. Je te propose d'aller, si tu le souhaites, un petit peu plus
loin. Voici quelques sujets qu'il pourrait être intéressant d'implémenter sur ce projet : 

## CSRF Token

C'était une demande dans le super bonus. Je te partage un lien pour comprendre un petit peu mieux la notion d'attaque CSRF 
et pourquoi il est important de s'en prévenir : https://www.phptutorial.net/php-tutorial/php-csrf/
Tu peux bien entendu t'aider de la correction.

## Création d'un page SHOW Teacher pour identifier facilement les étudiants associés

L'idée est de créer un page de détail du Teacher et afficher l'ensemble des étudiants associés. Pour cela tu devras te servir de 
la notion de jointure (JOIN) en SQL pour pouvoir récupérer des éléments associés.
Pour découvrir cette notion : https://sql.sh/cours/jointures
Si tu n'y arrives pas, pas d'inquiétude on abordera ce sujet ensemble très prochainement !

## Flash Message

Il serait intéressant d'ajouter un système de flash message sur l'application pour informer l'utilisateur si l'action 
réalisée (ajout/modification/suppression) s'est bien déroulée ou bien si une erreur est survenue.
Pour cela, on aimerait afficher un court message, soit de type `success` ou bien `error` et afficher ce dernier sur l'écran de l'utilisateur.
Ces messages sont temporaires et ne doivent pas rester à l'écran lorsque l'on change de page.
Si tu souhaites aller encore plus loin, tu peux essayer de faire disparaitre le message au bout de 5 secondes d'affichage.

## Vérification des données côté navigateur

Aujourd'hui la vérification des données soumise par l'utilisateur lors d'une création/modification se fait lors de la soumission et donc côté serveur.
Il pourrait être intéressant d'ajouter une seconde vérification, cette fois-ci avant la soumission et ainsi éviter une requête vouée à l'échec en cas d'erreur.
Pour y parvenir tu devras utiliser tes compétences en Javascript.

Attention la vérification côté navigateur n'est pas suffisante car elle peut facilement être contournée 
par un utilisateur malveillant (en inspectant le site web par exemple). Il faut impérativement conserver la vérification côté serveur.

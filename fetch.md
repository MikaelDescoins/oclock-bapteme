# `fetch()`

La fonction javascript `fetch()` est utilisée pour envoyer une requête HTTP à un serveur web et récupérer une réponse. 
Cela permet à une application web de récupérer des données à partir d'un serveur sans avoir à recharger la page entière.

Au stade d'avancement de la formation, pour récupérer des informations en BDD on utilise les méthodes que nous implémentons au niveau des Models et nous les appelons au sein des Controllers comme tu l'as fait sur le dernier projet PHP. 
L'action de récupération/soumissions des données se fait donc au niveau du controller.

Pour déclencher cette action au niveau du controller, nous avons besoin d'accéder à une route, et donc de rafraichir la page du navigateur.

La fonction `fetch()` permet d'aller requêter une route pour réaliser une action (récupération de données en GET, soumission en POST, etc.) directement dans le navigateur grâce à du Javascript


Si je reprends l'exemple du dernier projet PHP que tu as réalisé, on pourrait imaginer que tu as développé une route en GET du type '/{teacherId}/students' qui retourne la liste des étudiants d'un professeur au format JSON.

Grâce à la méthode `fetch()` tu pourrais ainsi très facilement récupérer la liste des étudiants sans passer par le serveur et rafraichir la page.

La requête pourrait ressembler à ceci : 

```js
fetch(`http://localhost/1/students`)
    .then(response => response.json())
        .then(students => {
            // ici tu pourras utiliser les données récupérées et afficher la liste des étudiants
            console.log(students); // students contiendra l'ensemble des étudiants liés au teacher ayant l'id 1
        });
```

Cette fonction peut être utilisée sur toutes les pages de ton application. Tu peux donc facilement accéder à des données sans coder à chaque fois la logique dans le controller de tes routes.


C'est un exemple très basique mais tu verras par la suite dans ton parcours que l'un des moyens les plus utilisés aujourd'hui pour développer une application web est la mise en place d'API REST.
Pour ne pas te perdre, imagine simplement que le principe de l'API est de mettre en place l'ensemble des routes qui vont exposer les données de notre application et les différentes actions possibles sur ces dernières.

Lorsque ce travail est réalisé, on peut très facilement intéragir avec notre BDD indirectement grâce à la méthode fetch() qui va requêter les routes de cette API. 
On peut aboutir a des application beaucoup plus réactives qui ne demandent pas de rafraichissement de la page permanent (je te donne l'exemple de Slack dans ton navigateur, tu n'as pas besoin de rafraichir ton écran pour voir les derniers messages reçus)


>Je te partage quelques ressources si tu souhaites en savoir plus :
>- Documentation de la fonction fetch() : https://developer.mozilla.org/fr/docs/Web/API/Fetch_API/Using_Fetch
>- Qu'est-ce qu'une API ? https://www.youtube.com/watch?v=fm1xxyBkerc

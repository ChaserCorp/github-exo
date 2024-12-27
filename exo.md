## Réaliser un site utilisant l'API de Github pour afficher les repositories associé à un utilisateur 

Misc : 

- Hébergement Vercell
- Base url : https://api.github.com
- Endpoint à atteindre à l'aide d'un GET : /users/{username}/repos
- Documentation de l'api pour l'exo : https://docs.github.com/en/rest/repos/repos?apiVersion=2022-11-28#list-repositories-for-a-user

Front : 

- Front en VueJS 3 -> TypeScript obligatoire (Avec documentation du code) 
- Affichage de chaques repository de manière responsive 
- Navbar avec différentes sections (lors du clic sur une section le contenu de la page change -> Pas de nouvelle page)
- 2 Sections : 
  - Home :
      - Input pour rentrer le nom de l'utilisateur 
      - Liste des repository associé 
      - Possibilité de mettre en favoris une repositorie 
  - Favoris : 
       - Liste des repositories mises en favoris
- Le site doit contenir une navbar et un footer (Carte Blanche sur le contenu)


Refactor : 

- Changer la position du router view et des élements 
- Revoir le front
- Configurer axios 
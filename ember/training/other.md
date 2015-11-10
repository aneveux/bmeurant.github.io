## Namespaces

{% raw %}

Comme on a pu le constater, au sein d'une application [Ember][ember], les routes sont r�f�renc�es par leur nom qualifi�.
Celui-ci se calcule en accolant les noms de l'ensemble des routes m�res puis du nom de la route fille. Le tout s�par�s 
par des ``.``.

Ainsi la route d�finie de cette mani�re ...

```javascript
// app/router.js
...
Router.map(function() {
  this.route('mere', function() {
    this.route('fille');
  });
});
```

... sera r�f�ren�able par le qualifieur ``mere.fille``. Par exemple :
 
* dans un ``link-to`` : ``{{link-to "Titre route fille" "mere.fille"}}`` 
* lors de l'appel d'un ``transitionTo`` : ``this.transitionTo('mere.fille');``

Chaque niveau de route imbriqu�e est donc ajout� devant le nom de la route elle-m�me. Cela permet d'�viter les 
collisions de nommage. Cependant, il peut s'av�rer n�cessaire ou pr�f�rable de conserver un nom court. Cela est
possible en pr�cisant que l'on souhaite r�initialiser le ``namespace`` via l'option ``resetNamespace`` dans le 
routeur : 

```javascript
// app/router.js
...
Router.map(function() {
  this.route('mere', function() {
    this.route('fille', {resetNamespace: true});
  });
});
```

{% endraw %}

<div class="work">
  {% capture m %}
  {% raw %}
  
1. Modifier la route ``comics.comic`` pour la nommer ``comic``
   * Mettre � jour tous les endroits de l'application ou cette route est r�f�renc�e
    
   > ```javascript
   > //app/routes/application.js
   >
   > import Ember from 'ember';
   > 
   > export default Ember.Route.extend({
   >   beforeModel() {
   >     this.transitionTo('comics');
   >   }
   > });
   > ```
  
  {% endraw %}
  {% endcapture %}{{ m | markdownify }}
</div>


## Plan

### Actions / Routes

cr�ation -> Route & actions + perso url
    save, cancel, willtransition
Edition -> perso route pour renderTemplate create

### Actions / Controllers

Filtering et sorting list
tranformation btn creer par input titre + bouton -> descativation btn si vide et sinon on bascule sur cre�r avec titre
actions avanc�es cr�er liste
actions target form mandatory

### Components

Validation formulaire ?
like component

### Persistence / Ember Data

Extraction model, cr�ation "store" et injection dans routes (au passage brief injections)
Ember-data, store, relations, etc.

### Tests

acceptance et unitaire

### Adv. Tpl

partials sur albums, render, etc.

### Backend

Serveur API -> REST Adapter

### Adv. Routing

Query params sur filtering et sorting comics

### D�ploiement

gest environnements, asset pipeline, etc.

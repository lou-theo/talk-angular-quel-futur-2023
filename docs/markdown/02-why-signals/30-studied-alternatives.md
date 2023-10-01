# Les possibilités étudiées

- Améliorer zone.js
- setState-style APIs
- Compiler-based reactivity
- Proxies
- RxJS
- Signals

Notes:

- Des expérimentations ont été faites dans beaucoup de directions

- On a déjà vu en quoi Zone.Js n'était pas une bonne solution, même dans le cas où on réussirait à affiner sa granularité

- Problème du setState : ne peut pas se destructurer en tant que propriété de classe

- Proxies ne peuvent pas s'appliquer aux primitives (ça demande un objet)

- Compile based : Exemple Svelte, réactivité n'est pas utilisable partout => il faut être dans un composant ou éventuellement dans un store mais avec une syntaxe spécifique

- Le cas RxJs fait polémique et va donc être approfondi.

##==##

# Le cas RxJs

- **Aynchrone** par nature
- Asynchronisme => **mauvaise DX**
- **Side effects** répandus
- Certains le détestent
<!-- .element: class="list-fragment" -->

Notes:

- Certes RxJs peut être synchrone mais comme il peut aussi être asynchrone et qu'on ne peut pas savoir dans quel cas on est, on doit toujours considérer que c'est asynchrone

- Il y aurait des moyens pour utiliser RxJs, que ce soit en obligeant l'utilisation d'Observable synchrones pour les templates ou en obligeant leur initialisation avec une valeur par défaut ou autre mais cela complexifierait l'expérience développeur

- Lorsque l'on subscribe à un observable, toute sorte d'opération peut être déclenchée : appel http, modification de données...

- Lors d'une conférence la core team Angular avait déclaré qu'autant de personnes disaient adorer RxJs et vouloir une intégration plus forte avec Angular que de personnes n'aimant pas et en demandant moins.

- RxJs demande de l'apprentissage et pas simple à debugger

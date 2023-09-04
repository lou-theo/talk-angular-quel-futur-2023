# Les possibilités étudiées

- Improving zone.js
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

- RxJs est aynchrone par nature
- Travailler avec cet asynchronisme appauvrirait l'expérience développeur
- Il est très courant d'avoir des side effects
- RxJs n'est pas aimé de tous
<!-- .element: class="list-fragment" -->

Notes:

- Certes RxJs peut être synchrone mais comme il peut aussi être asynchrone et qu'on ne peut pas savoir dans quel cas on est, on doit toujours considérer que c'est asynchrone

- Il y aurait des moyens pour utiliser RxJs, que ce soit en obligeant l'utilisation d'Observable synchrones pour les templates ou en obligeant leur initialisation avec une valeur par défaut ou autre mais cela complexifierait l'expérience développeur

- Lorsque l'on subscribe à un observable, toute sorte d'opération peut être déclenchée : appel http, modification de données...

- Lors d'une conférence la core team Angular avait déclaré qu'autant de personnes disaient adorer RxJs et vouloir une intégration plus forte avec Angular que de personnes n'aimant pas et en demandant moins.

- RxJs demande de l'apprentissage et pas simple à debugger

##==##

<!-- .slide: class="with-code max-height" -->

# RxJs glitch

<!-- prettier-ignore-start -->
```typescript
const counter$ = new BehaviorSubject(0);
const isEven$ = counter$.pipe(map((value) => value % 2 === 0));
const message$ = combineLatest(
  [counter$, isEven$],
  (counter, isEven) => `${counter} is ${isEven ? 'even' : 'odd'}`
);

message$.subscribe(console.log);
counter$.next(1);
```
<!-- prettier-ignore-end -->

<!-- .element: class="big-code block" -->

```txt
0 is even
1 is even
1 is odd
```

Notes:

- Bref, la team Angular trouve que RxJs est un super outils pour organiser des opérations complexes mais pas du tout adapté pour créer la base de la réactivité

- Ils sont convaincu de l'importance de l'interopérabilité avec RxJs

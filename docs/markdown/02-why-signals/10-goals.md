# Buts et prérequis de ce système

- **Granularité** au niveau du composants ou plus finement
- Permettre la déclaration d'un **état dérivé** d'autres variables
- Avoir une bonne interopérabilité avec **RxJs**
- Avoir un **accès synchrone** à la donnée
- Être sans **side effects** et sans **glitch**
- La gestion des **dépendances** (réactives) doit être simples
<!-- .element: class="list-fragment" -->

Notes:

- Un des objectif premier est d'avoir une détection fine du changement. La précision exacte est à déterminer

- computed : Feature assez demandée, les getters étant non optimisés, les pipes verbeux et pas forcément le plus adapté

- accès synchrone requis pour tout ce qui est binding notamment

- side effect : la donnée ne doit pas être modifiée ou déclencher d'opération

- on reviendra plus tard sur le glitch free

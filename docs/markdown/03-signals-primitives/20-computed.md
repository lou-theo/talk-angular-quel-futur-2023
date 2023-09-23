<!-- .slide: class="with-code max-height" -->

# Definition d'une computed

## Permet de créer un état dérivée à partir d'autres `Signals`

```typescript
function computed<T>(
  computation: () => T,
  options?: { equal?: (a: T, b: T) => boolean }
): Signal<T>;
```

<!-- .element: class="big-code block" -->

- Lazy computations

<!-- .element: class="list-fragment" -->

Notes:

- donne un Signal (readonly) qui est actualisé à chaque fois que l'une des dépendances change

- une dépendance correspond à un Signal utilisé dans la fonction de calcul

- une computed n'est pas calculée tant que quelqu'un ne cherche pas à lire sa valeur

##==##

<!-- .slide: class="with-code max-height" -->

# Utilisation de computed

```typescript
const counter = signal(0);

const isEven = computed(() => counter() % 2 === 0);
const color = computed(() => isEven() ? 'red' : 'blue');

counter.set(2);
```

<!-- .element: class="big-code block" -->

Notes:

- les computed sont des Signals et peuvent donc servir de dépendances

- dans l'exemple, au set de counter et en partant du principe que les computed sont utilisées
  - isEven est recalculé
  - color n'est pas recalculé car isEven n'a pas changé

<!-- .slide: class="with-code max-height" -->

# Definition d'un Signal

```typescript
interface Signal<T> {
  (): T;
  [SIGNAL]: unknown;
}
```

<!-- .element: class="big-code block" -->

```typescript
interface WritableSignal<T> extends Signal<T> {
  set(value: T): void;
  update(updateFn: (value: T) => T): void;
  mutate(mutatorFn: (value: T) => void): void;
  asReadonly(): Signal<T>;
}
```

<!-- .element: class="big-code block fragment" -->

Notes:

- Un Signal est un wrapper autour d'une valeur, pour accéder à sa valeur on l'appel comme une fonction. On peut l'appeler n'importe où (dans un contexte réactif ou non)

- Le symbole `SIGNAL` permet de reconnaitre si une valeur est un Signal en interne

- Un Signal est readonly, pour maj la donnée il faut un WritableSignal (on a donc 2 types de Signals)

- update permet de maj en se basant sur une valeur précédentes / mutate permet de muter un objet/array sans en changer la référence

- le choix de l'API
  - permet autant immutabilité que mutabilité ; Angular ne veut rien imposer à ce sujet
  - force séparation read/write pour bonne architecture

##==##

<!-- .slide: class="with-code max-height" -->

# Création d'un Signal

<!-- prettier-ignore-start -->
```typescript
function signal<T>(
  initialValue: T,
  options?: {equal?: (a: T, b: T) => boolean}
): WritableSignal<T>;
```
<!-- prettier-ignore-end -->

<!-- .element: class="big-code block" -->

Notes:

- fonction qui permet de créer un Signal (on ne passe pas par un new)

- `equal` permet de définir une fonction custom de comparaison
  - par défaut `===` pour primitives et "jamais equal" pour objets/arrays
  - si equal, pas de notification de changement

##==##

<!-- .slide: class="with-code max-height" -->

# Utilisation d'un Signal

```typescript [1-4|6-7]
const counter = signal(0); // 0
counter.set(5); // 5
counter.update((currentValue) => currentValue + 1); // 6
counter.set(counter() + 2); // 8

const names = signal(['John', 'Jane']); // ['John', 'Jane']
names.mutate((names) => names.push('Jack')); // ['John', 'Jane', 'Jack']
```

<!-- .element: class="big-code block" -->

Notes:

- `update` est un shortcut pour `set`

##==##

<!-- .slide: class="with-code max-height" -->

# Inconvénients du format "getter"

- Contre-intuitif pour les développeurs
- Type narrowing délicat
<!-- .element: class="list-fragment" -->

```typescript [1-4|5-8]
// `user.name()` is nullable
if (user.name()) {
  console.log(user.name().first); // ❌ type error
}
const name = user.name();
if (name) {
  console.log(name.first); // ✅
}
```

<!-- .element: class="big-code block fragment" -->

Notes:

- On a répété aux devs que c'est mal de se servir des fonctions dans le template

- pour le narrowing côté template, la team Angular pense réussir à faire quelque chose avec l'Angular Language Service

- les syntaxes alternatives ont été explorées ('.value', get/set, decorator, etc.) mais elles n'ont pas convaincues la team Angular

<!-- .slide: class="with-code max-height" -->

# Traçage des dépendances

<!-- prettier-ignore-start -->

```typescript
const greeting = computed(
  () => showName() ?
    `Hello, ${name()}!`
    :
    'Hello!'
);
```

<!-- prettier-ignore-end -->

<!-- .element: class="big-code block" -->

Notes:

- pour computed et effect

- Vous l'aurez surement remarqué, on n'explicit pas les dépendances
  - Traçage automatique des dépendances, ces dernières devant être des Signals

- Gestion dynamique des dépendances en fonction de la dernière computation
  - dans l'exemple `name`est une dépendance seulement si `showName` est truthy

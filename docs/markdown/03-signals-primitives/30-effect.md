<!-- .slide: class="with-code max-height" -->

# Definition d'un Effect

## Permet d'effectuer des effets de bord

```typescript
function effect(
  effectFn: (onCleanup: (fn: () => void) => void) => void,
  options?: CreateEffectOptions
): EffectRef;
```

<!-- .element: class="big-code block" -->

```typescript [4]
interface CreateEffectOptions {
  injector?: Injector
  manualCleanup?: boolean
  allowSignalWrites?: boolean
}

interface EffectRef {
  destroy(): void
}
```

Notes:

- on défini une fonction qui sera exécutée à chaque fois que l'une des dépendances change

- on peut définir une fonction de cleanup qui sera exécutée avant chaque nouvel exécution de l'effect

- on peut définir des options
  - on ne va pas s'attarder sur injector et manualCleanup
  - allowSignalWrites: permet de définir si les Signals peuvent être modifiés dans l'Effect, par défaut non pour éviter des boucles infinies
  - ==> force à être sur de soit pour modifier des Signals dans un Effect (il est généralement mieux d'utiliser une computed)

- Détail des options non abordées
  - injector: permet de définir un injector pour l'effect
  - manualCleanup: permet de définir si l'effect doit être nettoyé manuellement (par défaut non). Si oui, on peut appeler la méthode destroy de l'effectRef pour nettoyer l'effect

##==##
<!-- .slide: class="with-code max-height" -->

# Utilisation d'un Effect

```typescript [1|2-6|7-10]
effect((onCleanup) => {
  const countValue = this.count();
  let secsFromChange = 0;
  const id = setInterval(() => {
    console.log(`${countValue} had its value unchanged for ${++secsFromChange} seconds`);
  }, 1000);
  onCleanup(() => {
    console.log('Clearing and re-scheduling effect');
    clearInterval(id);
  });
});
```

<!-- .element: class="big-code block" -->

<!-- .slide: class="with-code max-height" -->

# Compatibilité avec RxJS !

## De Signal à Observable

```typescript
function toObservable<T>(
  source: Signal<T>,
): Observable<T>;
```

<!-- .element: class="big-code block" -->

Notes:

- assez simple

- quelques subtilités sur l'asynchronissité qu'il est intéressant d'aller lire dans la RFC

- l'observable doit être manuellement unsubscribed même si le composant lié au Signal est détruit (le signal sera encore utilisé donc non détruit)

##==##
<!-- .slide: class="with-code max-height" -->

# Compatibilité avec RxJS !

## D'Observable à Signal

```typescript
function toSignal<T, U extends T | null | undefined>(
  source: Observable<T>,
  options: { initialValue: U, requireSync?: false }
): Signal<T | U>;

// alternative, on affirme que l'observable est synchrone
function toSignal<T>(
  source: Observable<T>,
  options: { requireSync: true }
): Signal<T>;
```

<!-- .element: class="big-code block" -->

Notes:

- un peu moins facile car un Signal est synchrone et doit donc toujours avoir une valeur
  - si initialValue non fournie, undefined par défaut

- gestion des erreurs intéressante à aller lire dans la RFC (à gérer dans un try/catch ou en amont dans l'observable)

- Subtilité (si question) : la valeur du Signal est directement "calculée" (pas de lazy computation) pour éviter des side effects à la lecture

<!-- .slide: class="with-code max-height" -->

# Changement des Inputs / Outputs ! 🤯

```typescript [3-7|9]
@Component(...)
class AppComponent {
  firstName = input<string>(); // Signal<string | undefined>
  lastName = input('Smith'); // Signal<string>
  address = input<Address>({ // Signal<Address>
    initialValue: { street: "1 Avenue de l'Europe", city: 'Strasbourg' },
  });

  saved = output<User>(); // EventEmitter<User>
}
```

<!-- .element: class="big-code block" -->


Notes:

- input propose plusieurs options qu'on ne va pas creuser (alias...)

- plusieurs possibilités pour écrire la fonction input en fonction de si l'on veut des options ou non, cela donnera plus ou moins de boilerplate
  - pour des valeurs primitives on peut spécifier une valeur par défaut directement entre parenthèses
  - pour des objets on peut spécifier une valeur par défaut dans les options

- on notera que les inputs sont des Signals donc readonly (contrairement à actuellement)

- output change d'API pour s'aligner avec la nouvelle API de input mais pas de changement de comportement

##==##

<!-- .slide: class="with-code max-height" -->

# Révolution du 2-way binding

```typescript [3,7,10]
@Component(...)
class SomeCheckbox {
  checked = model(false); // WritableSignal<boolean>
}

@Component({
  template: `<some-checkbox [(checked)]="isAdmin" />`,
})
export class SomePage {
  isAdmin = signal(false);
}
```

<!-- .element: class="big-code block" -->

Notes:
- plus de magie à devoir bien nommer son input et output pour faire du 2-way binding

- important de remarquer que `SomePage` passe l'instance de son Signal `isAdmin` à l'instance de `SomeCheckbox` et non pas la valeur de `isAdmin` (pas de format getter)

- `model()` donne un WritableSignal donc permet de maj la valeur et la propager au parent

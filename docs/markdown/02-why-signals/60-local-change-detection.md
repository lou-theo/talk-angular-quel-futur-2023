# Quel niveau de granularité ?

- Entire application <= **Zone.js**
- Component tree
- Individual components
- View <= **Angular Signals**
- DOM element <= **SolidJS**
- Binding

Notes:

- Dans un template il peut y avoir plusieurs View, par exemple, chanque branche d'un NgIf/NgFor est une View

- "Individual components" : Composant sans ses enfants (contrairement à "Component tree")

- Aujourd'hui Angular pense qu'il serait trop coûteux d'aller en dessous de la View :

  - chaque noeud à retenir demande de la mémoire et du temps pour gérer le graphe de dépendance
  - le niveau "View" est déjà très efficace, surtout comparé à l'actuel et une vue peut être assez petite (chaque ligne d'un NgFor est une view)
  - Cela facilite l'intégration avec Zone.Js qui travaille déjà avec ce niveau

- VueJs & react utilisent un virtualDOM. VueJs réfléchit à se positionner comme SolidJS (DOM Element)

##==##

<!-- .slide: class="with-code max-height" -->

# Granularité : View, les implications

```typescript [2,6,7,10]
@Component({
  template: `<p>Count {{ count() }} - {{ name }}</p>
    <button (click)="increment()">Increment count</button>`,
})
export class SimpleCounter {
  count = signal(0);
  name = 'Morgan';

  increment() {
    this.count.update((c) => c + 1);
  }
}
```

<!-- .element: class="big-code block" -->

Notes:

- Petit spoil sur la syntaxe des signals, on va en parler juste après

- Ce composant zoneless utilise 1 signal et 1 variable non réactive dans son template

- si `count` est maj, le template aussi

- si name venait à changer, le template ne serait pas maj

- SAUF ! Si le Signal est ensuite maj car ça déclenche une détection de changement au niveau de la View !

- La team Angular est actuellement en réflexion sur ce comportement et réfléchit à ajouter des warnings en cas d'utilisation d'une var non Signal et non read-only dans un template par exemple

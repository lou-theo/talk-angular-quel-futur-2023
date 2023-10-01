# Quel niveau de granularité ?

- Entire application <= **Zone.js**
- Component tree
- Individual components
- View <= **Angular Signals**
- DOM element <= **SolidJS**
- Binding
<!-- .element: class="list-fragment" -->

Notes:

- Dans un template il peut y avoir plusieurs View, par exemple, chanque branche d'un NgIf/NgFor est une View

- "Individual components" : Composant sans ses enfants (contrairement à "Component tree")

- Aujourd'hui Angular pense qu'il serait trop coûteux d'aller en dessous de la View :

  - chaque noeud à retenir demande de la mémoire et du temps pour gérer le graphe de dépendance
  - le niveau "View" est déjà très efficace, surtout comparé à l'actuel et une vue peut être assez petite (chaque ligne d'un NgFor est une view)
  - Cela facilite l'intégration avec Zone.Js qui travaille déjà avec ce niveau

- VueJs & react utilisent un virtualDOM. VueJs réfléchit à se positionner comme SolidJS (DOM Element)

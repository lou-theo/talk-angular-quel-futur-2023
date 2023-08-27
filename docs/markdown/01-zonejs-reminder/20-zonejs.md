# Aperçu de Zone.js

Librairie qui permet de créer des zones d'exécution

Angular est exécuté dans une zone

<br/>

Notes:

- Créé par l'équipe Angular mais peut être utilisé avec n'importe quel framework

- Concept simple: une grande partie de l'API du DOM est surchargée pour être interceptée par Zone.js

- Lorsque zone.js intercepte un appel, il déclenche un changement de détection

##==##

# Lors de la détection de changement

- L'ENSEMBLE des composants est parcouru de manière séquentielle
- On exécute les **lifecycle hooks**
- Pour chaque expression dans le template, on **compare la valeur actuelle / précédente**
- Si la valeur a changé, on **déclenche le rendu du composant**
<!-- .element: class="list-fragment" -->

Notes:

- On part du composant root et on descend dans l'arbre
- on fait tout ça pour le moindre petit event (scroll, setTimeout, etc.)

- Lifecycles : ngOnChanges, ngDoCheck, ngAfterContentChecked, ngAfterViewChecked

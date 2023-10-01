# Aperçu de Zone.js

<div style='border-color: black; border-style: solid; width: 60%;height: 50%;padding: 50px'>
Zone.js
<div style='border-color: red; border-style: solid; width: 80%;height: 30%;padding: 50px;margin: 50px'>
Angular Zone
</div>
</div>

Notes:

- Créé par l'équipe Angular mais peut être utilisé avec n'importe quel framework

- Concept simple: une grande partie de l'API du DOM est surchargée pour être interceptée par Zone.js

- Lorsque zone.js intercepte un appel, il déclenche un changement de détection

##==##

# Lors de la détection de changement

- Parcourt des composants
- Lifecycle hooks
- Comparaison la valeur actuelle / précédente
- Rendu éventuel du composant
<!-- .element: class="list-fragment" -->

Notes:

- pour le moindre event

- L'ENSEMBLE des composants est parcouru de manière séquentielle depuis composant root vers bas

- On exécute les **lifecycle hooks**

- Pour chaque expression dans le template, on **compare la valeur actuelle / précédente**

- Si la valeur a changé, on **déclenche le rendu du composant**

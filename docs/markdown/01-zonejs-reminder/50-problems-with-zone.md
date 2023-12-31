<!-- .slide: class="quote-slide" -->

## Le but initial de Zone.Js

<blockquote>
<cite>
Your state can live in the middle of the Pacific Ocean and you have no wrappers, no Getters / Setters and no APIs you need to remember to call ... it just works!
</cite>
</blockquote>

Notes:

- On peut muter l'état de l'application n'importe où, n'importe comment et ça fonctionne

- Développeur expérience très bonne

##==##

# La magie Zone.Js a des coûts...

- Temps de **chargement**
- **Maintenance** de Zone.Js
- problèmes de **performance**
- ... qui demandent une grande compréhension
<!-- .element: class="list-fragment" -->

Notes:

- Zone.Js doit être chargé avant Angular dans le navigateur => temps de chargement

- Avec le temps il y a de plus en plus d'API JS à patcher dont certaines impossibles et où il faut trouver des workarounds (async/await)

- On met innocemment une lib de chart (par ex) et on se retrouve avec des problèmes de performance

- OnPush, ngZone, ChangeDetector, ngTrackBy, pipes, etc. Plein de concepts à comprendre pour faire du code performant

- Zone.Js est globalement très inefficace car beaucoup de change detection dans le vide

##==##

# Célèbre erreur

<div class="full-center">
 <img style='height: 50%' alt='gif' src="../../assets/images/ExpressionChangedAfterItHasBeenCheckedError.png">
</div>

Notes:

- Demander comment régler l'erreur

- Cette erreur vient de la manière dont fonctionne la détection de changement :

  - Plusieurs API surtout concernant les enfants (queries, directives, etc.) se mettent à jour pendant la détection de changement
  - La détection de changement est top-down

##==##

<!-- .slide: class="with-code max-height" -->

# Célèbre erreur

```typescript
setTimeout(() => {
  this.updateUIRelatedState();
});
```

<!-- .element: class="big-code block" -->

Notes:

- Seul manière de faire dans certains cas

- Utilisé dans le code d'Angular

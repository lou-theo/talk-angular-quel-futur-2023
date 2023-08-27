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

- Temps de chargement du 1er rendu
- Maintenance de Zone.Js pour Angular Team
- Facilité de faire du code avec des problèmes de performance
- ... et qui demande une grande compréhension de Zone.Js et Angular pour corriger
<!-- .element: class="list-fragment" -->

Notes:

- Zone.Js doit être chargé avant Angular dans le navigateur => temps de chargement

- Avec le temps il y a de plus en plus d'API JS à patcher dont certaines impossibles et où il faut trouver des workarounds (async/await)

- On met innocemment une lib de chart (par ex) et on se retrouve avec des problèmes de performance

- OnPush, ngZone, ChangeDetector, ngTrackBy, pipes, etc. Plein de concepts à comprendre pour faire du code performant

- Zone.Js est globalement très inefficace car beaucoup de change detection dans le vide

##==##

<!-- .slide: class="with-code max-height" -->

# Erreur "Expression has changed after it was checked"

## Du code qui ressemble à un workaround

```typescript [4-8]
@Component(...)
class AppComponent implements OnInit {
  ngOnInit() {
    this.myForm.valueChanges?.subscribe(() =>
      setTimeout(() => {
        this.updateUIRelatedState();
      }),
    );
  }
}
```

<!-- .element: class="big-code block" -->

Notes:
Cette erreur vient de la manière dont fonctionne la détection de changement :

- Plusieurs API surtout concernant les enfants (queries, directives, etc.) se mettent à jour pendant la détection de changement

- La détection de changement est top-down

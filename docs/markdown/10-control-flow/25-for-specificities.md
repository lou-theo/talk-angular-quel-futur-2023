# Quelques changements suppléméntaires pour le "for"

- `track` devient obligatoire (SAUF avec les Signals)
- `for` est reactif avec les signaux : itérer sur un Signal donne une liste de Signal
- améliorations divers envisagée (built-in destructuration, "virtual scrolling", autres types de boucles, etc.)
<!-- .element: class="list-fragment" -->

Notes:
- trackBy était une purge à utiliser jusqu'à présent car très verbeux => bien simplifié

- Avec les Signals, tack n'est pas facultatif, il n'est pas permis

- ce changement vient du fait que dans leurs recherches, la team Angular a identifié les boucles comme la source la plus commune aux problèmes de perf

- le "for" réactif est l'une des grosses raisons amenant ce nouveau Control Flow

- les autres types de boucles sont envisagées : "for in" qui itère sur les "keys" ; boucle async, etc.

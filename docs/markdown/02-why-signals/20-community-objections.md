# Des mécontents et quelques incompréhensions

<div class="full-center">
 <img style='height: 60%' alt='gif' src="https://media.tenor.com/6y7ApASFZNIAAAAC/kaamelott-guethenoc.gif">
</div>

##==##

# Des mécontents et quelques incompréhensions

- "Plutôt que de bosser sur un non problème, ça vous dirait de faire de la feature ?"
- Incompréhension par rapport à RxJs
- Peur de la migration engendrée
- confusion d'avoir 2 systèmes de réactivité
<!-- .element: class="list-fragment" -->

Notes:
- J'ai été surpris de la virulance de certains commentaires

- Pour RxJs : certains ne comprennent pas pourquoi ça n'est pas suffisant, d'autres ont l'impression qu'Angular cherche à le remplacer

- La migration d'une app utilisant Zone.Js vers une app zoneless ne pourra pas se faire automatiquement car changement de paradigme. La team Angular reste floue sur la temporalité d'une telle migration mais rassure sur le fait qu'elle doit gérer les milliers d'app Angular de Google et qu'elle ne forcera pas de grosses migrations sur un coup de tête. La fin de Zone.Js n'est pas pour demain

- Pour ne pas perturber la communauté, Angular est conscient qu'il faudra qu'elle affiche sa préférence sur le système de réactivité à utiliser. La documentation devra être mise à jour en ce sens.

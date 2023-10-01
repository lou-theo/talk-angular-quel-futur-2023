# Pourquoi tout changer ?

- Points de douleurs et limites
- Incompatibilité Signals
- Amélioration trop risquée
<!-- .element: class="list-fragment" -->

Notes:

- Angular est sorti en 2016 => 7 ans que c'est comme ça

- Les pain points potentiels (ils ne sont pas explicités mais je suppose) :

  - verbosité
  - non prise en compte de certains cas (else if, empty for)
  - syntaxe différente du JS pur ('as' pour assignation...)

- problème pour améliorer la syntaxe :

  - risques de breaking change non maitrisés sur une fonctionnalité de base
  - complexification du code pour les directives

- Les Signals sont l'excuse parfaite pour travailler sur un rework de la syntaxe

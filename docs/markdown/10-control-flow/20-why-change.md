# Pourquoi changer ?

## Une fonctionnalité qui a 7 ans, n'est-elle pas suffisamment mature ?

- Identification d'un certain nombre de "points de douleurs" et limites à la syntaxe actuelle
- Syntaxe actuelle insuffisante pour fonctionner avec les Signals
- Ratio risques / gains insuffisant pour améliorer la syntaxe actuelle
<!-- .element: class="list-fragment" -->

Notes:

- Angular est sorti en 2016

- Les pain points potentiels (ils ne sont pas explicités mais je suppose) :

  - verbosité
  - non prise en compte de certains cas (else if, empty for)
  - syntaxe différente du JS pur ('as' pour assignation...)

- problème pour améliorer la syntaxe :

  - risques de breaking change non maitrisés sur une fonctionnalité de base
  - complexification du code pour les directives

- Les Signals sont l'excuse parfaite pour travailler sur un rework de la syntaxe

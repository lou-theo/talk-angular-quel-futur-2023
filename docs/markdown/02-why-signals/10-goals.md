# Prérequis de ce système

- **Granularité**
- **Accès synchrone** à la donnée
- Permettre des **états dérivés**
- Interopérabilité avec **RxJs**
- Gestion simple des **dépendances**
- Sans **side effects**
<!-- .element: class="list-fragment" -->

Notes:

- détection fine du changement
  - niveau composant
  - précision exacte à déterminer

- computed
  - Feature assez demandée
  - getters non optimisés, les pipes verbeux

- accès synchrone => binding DOM

- side effect => lecture ne doit rien modifier

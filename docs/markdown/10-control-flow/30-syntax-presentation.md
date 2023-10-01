# A quoi ça ressemble ?

<div class="full-center">
 <img style='height: 50%' alt='gif' src="https://media.tenor.com/txDqgTLcIW0AAAAC/spy-spying.gif">
</div>

Notes:

- La syntaxe n'est pas figée ! Notamment hésite entre 2

- We refer to the community-proposed syntax as "@ syntax", and to the RFC's flavor as "block syntax"

- Pour chaque cas, on les 2 syntaxes affichées

##==##

<!-- .slide: class="two-column-layout" -->

# If

##--##

<!-- .slide: class="with-code" -->

```angular2html
{#if cond.expr}
    Main case was true!
  {:else if other.expr}
    Extra case was true!
  {:else}
    False case!
{/if}
```

<!-- .element: class="big-code block" -->

##--##

<!-- .slide: class="with-code" -->

```angular2html
@if (cond.expr) {
  Main case was true!
} @else if (other.expr) {
  Extra case was true!
} @else {
  False case!
}
```

<!-- .element: class="big-code block" -->

Notes:

- Enfin un else if !

- flow plus simple à lire / écrire

##==##

<!-- .slide: class="two-column-layout" -->

# For

##--##

<!-- .slide: class="with-code" -->

```angular2html
<ul>
  {#for item of items; track item.id}
      <li>{{ item.name }}</li>
    {:empty}
      <li>No items...</li>
  {/for}
</ul>
```

<!-- .element: class="big-code block" -->

##--##

<!-- .slide: class="with-code" -->

```angular2html
<ul>
  @for (item of item; track item.id) {
    <li>{{ item.name }}</li>
  } @empty {
    <li>No items...</li>
  }
</ul>
```

<!-- .element: class="big-code block" -->

Notes:

- trackBy était une purge à utiliser jusqu'à présent car très verbeux => bien simplifié

- trackBy devient obligatoire sauf avec les Signals

  - Etude Angular a montré que le for sans track est à l'origine de la plupart des problèmes de perf

- itérer sur un Signal donne une liste de Signal

- améliorations divers envisagée
  - built-in destructuration
  - "virtual scrolling"
  - autres types de boucles : "for in" qui itère sur les "keys" ; boucle async, etc.

##==##

<!-- .slide: class="two-column-layout" -->

# Switch

##--##

<!-- .slide: class="with-code max-height" -->

```angular2html
{#switch kind}
  {:case 'human'}
    <human-cmp />
  {:case 'robot'}
    <robot-cmp />
  {:default}
    <alien-cmp />
{/switch}
```

<!-- .element: class="big-code block" -->

##--##

<!-- .slide: class="with-code max-height" -->

```angular2html
@switch (kind) {
  @case ('human') {
    <human-cmp />
  } @case ('robot') {
    <robot-cmp />
  } @default {
    <alien-cmp />
  }
}
```

<!-- .element: class="big-code block" -->

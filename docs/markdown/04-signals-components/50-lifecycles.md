# Nouveaux lifecycles !

## Au niveau application ...

- `afterNextRender`
- `afterRender`
- `afterRenderEffect`

Notes:

- Demander au public quels sont les 8 lifecycles existants

- `afterNextRender` est appelé après le prochain render (oneshot)
  - utile pour init une lib externe

- `afterRender` est appelé après chaque render (pareil que `afterNextRender` mais pas oneshot)

- `afterRenderEffect` est un `effect` special qui est appelé au même moment que `afterRender`
  - je ne vois pas de usecase pour le moment

##==##
<!-- .slide: class="with-code max-height" -->

# Nouveaux lifecycles !

## Au niveau application ...

```typescript [6-8]
@Component(...)
export class MyChartCmp {
  chartRef = viewChild<ElementRef>('chart');
  chart: MyChart | null;

  constructor() {
    afterNextRender(() => {
      this.chart = new MyChart(this.chartRef().nativeElement);
    });
  }
}
```

<!-- .element: class="big-code block" -->

Notes:

- nouveaux lifecycles peuvent être utilisées à peu près partout (services...)
  - pas d'interface à implémenter
  - ce sont des fonctions à qui il faut donner un callback

##==##

# Nouveaux lifecycles !

## ... Qui remplacent les anciens

- on ne garde que `ngOnInit` et `ngOnDestroy`

<br/><br/>

- `ngOnChanges` => `computed` et/ou `effect`
- `ngDoCheck` => `effect`
- `ngAfterViewInit` => `afterNextRender`
- les autres => manipuler les Signals des queries

<!-- .element: class="fragment" -->

Notes:

- Grosse simplification des lifecycles

- le lifecycle actuel d'Angular est fortement couplé à la détection de changement. En changeant de modèle de détection, plus de sens à garder les anciens cycles

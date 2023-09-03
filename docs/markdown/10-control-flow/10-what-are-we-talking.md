<!-- .slide: class="with-code max-height" -->

# Control flow ? Kesako ?

```angular2html
<div *ngIf="condition; else elseCase">Condition vraie</div>
<ng-template #elseCase>Condition fausse</ng-template>

<div *ngFor="let item of items; index as i; trackBy: trackByFn">
  {{ i }} - {{ item }}
</div>

<ng-container [ngSwitch]="switch_expression">
  <some-element *ngSwitchCase="match_expression_1">...</some-element>
  <some-element *ngSwitchDefault>...</some-element>
</ng-container>
```

<!-- .element: class="big-code block" -->

Notes:

- Il s'agit des directives *ngIf, *ngFor et *ngSwitch

- une des plus grosses bases Angular côté template

- On ne parle pas des directives structurelles custom

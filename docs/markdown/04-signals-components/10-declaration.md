<!-- .slide: class="with-code max-height" -->

# Déclarer un Signal based component

```typescript [2]
@Component({
  signals: true,
  selector: 'temperature-calc',
  template: `<p>F: {{ fahrenheit() }}</p>`,
})
export class TemperatureCalc {
  celsius = signal(25);
  fahrenheit = computed(() => this.celsius() * 1.8 + 32);
}
```

<!-- .element: class="big-code block" -->

Notes:
- nouvelle propriété `signals` dans le `@Component`

- detectionStrategy plus disponible car pas de sens avec les Signals

- les composants zone-based et signal-based peuvent cohabiter dans une même application, Angular s'occupe des détails

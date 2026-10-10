# Property binding with [disabled]

Property binding lets you push a component value straight into a real HTML property. You use square brackets for it. Interpolation with `{{ }}` is for showing text, while `[property]="expression"` sets the DOM property itself, so it's the right tool for things like `disabled`, `src`, or `value`.

```ts
isBusy = true;
```

```html
<button [disabled]="isBusy">
  {{ isBusy ? 'Saving…' : 'Save' }}
</button>
```

## On screen

On screen you'd see a Profile form with Name and Email filled in, plus a grayed-out “Saving…” button. It won't take another tap as long as `isBusy` is true.

![Mockup](../images/2026-09-30-property-binding.jpg)

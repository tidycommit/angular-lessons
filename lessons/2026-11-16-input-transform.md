# Input Transforms: Turn Attribute Strings into Real Values

When you write `<product-card featured qty="3">` in a template, Angular hands your component plain strings: `''` and `"3"`. An **input transform** converts them for you, so `featured` becomes `true` and `qty` becomes the number 3.

Angular ships two ready-made helpers, `booleanAttribute` and `numberAttribute`, and you plug them into `input()` with the `transform` option. The older way is the `@Input({ transform: booleanAttribute })` decorator form; before transforms people converted values by hand in a setter.

```ts
import { Component, input, booleanAttribute, numberAttribute } from '@angular/core';

@Component({
  selector: 'product-card',
  standalone: true,
  template: `
    <h3>Coffee Mug</h3>
    @if (featured()) { <span class="badge">Featured</span> }
    <p>Qty: {{ qty() }}</p>
  `,
})
export class ProductCard {
  featured = input(false, { transform: booleanAttribute });
  qty = input(1, { transform: numberAttribute });
}
// <product-card featured qty="3" />
```

## On screen
Ada's Shop shows a Coffee Mug card with a gold "Featured" badge, even though the template only says `featured` with no value. Qty shows 3 as a real number.

![Input transform mockup](../images/2026-11-16-input-transform.jpg)

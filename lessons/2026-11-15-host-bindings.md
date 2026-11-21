# Host Bindings: Style the Component's Own Tag

Every component sits inside its own element, like `<product-card>`. The **host** metadata lets a component set classes, attributes, and event listeners on that element, right from the component file. No wrapper div needed.

In modern Angular you use the `host` property of `@Component`, with signals driving the values. The older way is the `@HostBinding` and `@HostListener` decorators; you'll see them in lots of code, and they still work.

```ts
import { Component, signal } from '@angular/core';

@Component({
  selector: 'product-card',
  standalone: true,
  host: {
    '[class.active]': 'active()',
    '(mouseenter)': 'active.set(true)',
    '(mouseleave)': 'active.set(false)',
  },
  template: `<h3>Coffee Mug</h3><button>Add to cart</button>`,
})
export class ProductCard {
  active = signal(false);
}
```

## On screen
Ada's Shop shows a Coffee Mug card with an "Add to cart" button. When the pointer moves over the card, the whole card gets the `active` class and lights up with a blue ring; it fades back when the pointer leaves.

![Host bindings mockup](../images/2026-11-15-host-bindings.jpg)

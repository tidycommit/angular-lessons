# Directive Composition with hostDirectives

Today's tip is the **directive composition API**. With `hostDirectives`, a component can pull in other standalone directives and expose only the inputs you choose. You reuse behavior without inheritance and without repeating attributes in every template.

Here Ada's `ProductTile` component applies `Highlight` and `Tooltip` automatically and forwards their inputs. Anyone using `<app-product-tile>` can write `appHighlight="gold"` on it. The older way was extending a base class or copying the directive onto each element.

```ts
import { Component } from '@angular/core';
import { Highlight } from './highlight';
import { Tooltip } from './tooltip';

@Component({
  selector: 'app-product-tile',
  template: `<h3>Coffee Mug</h3><button>Add to cart</button>`,
  hostDirectives: [
    { directive: Highlight, inputs: ['appHighlight'] },
    { directive: Tooltip, inputs: ['tip'] },
  ],
})
export class ProductTile {}
```

```html
<app-product-tile appHighlight="gold" tip="Fresh stock" />
```

## On screen
The tile shows the heading "Coffee Mug" and an Add to cart button. Because `ProductTile` composes `Highlight` and `Tooltip`, setting `appHighlight="gold"` and `tip="Fresh stock"` on `<app-product-tile>` applies those behaviors without repeating the directives in the template. The mockup places this in a My Shop phone titled "Ada's profile card", adds highlight and tooltip chips, a mug photo, a Sale price of $14.99, and a tooltip that says "This product will stand out with a tooltip on hover" rather than "Fresh stock".

![Directive composition mockup](../images/2026-11-24-host-directives.jpg)

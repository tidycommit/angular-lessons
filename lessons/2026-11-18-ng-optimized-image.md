# NgOptimizedImage: Fast Photos Without Layout Shift

Today's tip is **NgOptimizedImage**, Angular's built-in way to load pictures the way a fast page should. Swap `src` for `ngSrc`, give the image a `width` and `height` so the layout doesn't jump while it loads, and mark the main photo with `priority` so the browser fetches it first. Angular then lazy-loads other images by default and can build a `srcset` for you.

Import `NgOptimizedImage` from `@angular/common` and add it to the component's `imports`. The older way is a plain `<img src="...">`, which works, but it can shift the page as the photo appears and won't prioritize your hero image.

```ts
import { Component } from '@angular/core';
import { NgOptimizedImage } from '@angular/common';

@Component({
  selector: 'product-card',
  imports: [NgOptimizedImage],
  template: `
    <h3>Coffee Mug</h3>
    <img
      ngSrc="assets/mug.jpg"
      width="400"
      height="400"
      alt="Coffee Mug"
      priority
    />
    <p>$12</p>
  `,
})
export class ProductCard {}
```

## On screen
A Coffee Mug card shows a product photo, the heading "Coffee Mug", and the price $12. Because the image uses `ngSrc` with width, height, and `priority`, the space for the photo is reserved from the start and the browser treats it as the page's main image. The mockup places this card in Ada's My Shop, adds the "Ada's picks" label, and includes an "Add to cart" button.

![NgOptimizedImage mockup](../images/2026-11-18-ng-optimized-image.jpg)

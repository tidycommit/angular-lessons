# Interpolation with {{ }}

Once your component has a property, put it on screen with interpolation.

In the template, wrap the property name in double curly braces. Angular reads the value from the component class and drops it into the HTML wherever you place that expression.

```typescript
// greeting.component.ts
export class GreetingComponent {
  name = 'Ada';
}
```

```html
<!-- greeting.component.html -->
<h1>Hello, {{ name }}</h1>
<p>Welcome back</p>
```

## On screen

A Material-style app bar, a card that says “Hello, Ada,” a quiet “Welcome back” line, and a Say hi button — the name comes from the component property, not hard-coded copy in the markup.

![Mockup](../images/2026-09-28-interpolation.png)

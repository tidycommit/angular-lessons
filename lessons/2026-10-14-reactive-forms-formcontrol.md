# Reactive Forms: Your First FormControl

Good morning! Today we meet **reactive forms**, starting with their smallest building block: the `FormControl`. Instead of letting the template own the input's value (like `[(ngModel)]` does), you create the control in your TypeScript class and connect it to the input with `[formControl]`. The class is now the single source of truth, so you can read, set, validate, and watch the value from code.

Import `ReactiveFormsModule` straight into a standalone component's `imports`. In older Angular you added `ReactiveFormsModule` to an `NgModule`'s `imports` array; the `FormControl` itself works the same way.

```ts
import { Component } from '@angular/core';
import { FormControl, ReactiveFormsModule } from '@angular/forms';

@Component({
  selector: 'app-greeter',
  imports: [ReactiveFormsModule],
  template: `
    <input [formControl]="name" placeholder="Your name">
    <p>Hello, {{ name.value }}!</p>
  `,
})
export class Greeter {
  name = new FormControl('Ada');
}
```

## On screen

A text box already filled with "Ada" and, below it, "Hello, Ada!". If you change the box to "Grace", the line updates instantly to "Hello, Grace!".

![Phone mockup showing the input and greeting](../images/2026-10-14-reactive-forms-formcontrol.jpg)

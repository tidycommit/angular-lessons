# Custom pipes

Today's tip is about **custom pipes**. You already know built-in pipes like `uppercase` and `date`. When you keep writing the same little formatting logic in your templates, wrap it in your own pipe: a class with `@Pipe({ name: 'initials' })` and a `transform()` method that takes a value and returns the display version. Add the pipe to your component's `imports`, then use it anywhere with `{{ person | initials }}`.

Pipes are *pure* by default, which means Angular only reruns `transform()` when the input value changes, so they're cheap even inside a long `@for` list. In older code you'll see `standalone: true` on the pipe, or the pipe listed in an NgModule's `declarations`; today pipes are standalone by default.

```ts
import { Component, Pipe, PipeTransform } from '@angular/core';

@Pipe({ name: 'initials' })
export class InitialsPipe implements PipeTransform {
  transform(name: string): string {
    return name
      .split(' ')
      .map(part => part[0])
      .join('')
      .toUpperCase();
  }
}

@Component({
  selector: 'app-team',
  imports: [InitialsPipe],
  template: `
    <h1>Team</h1>
    @for (person of people; track person) {
      <div class="row">
        <span class="avatar">{{ person | initials }}</span>
        {{ person }}
      </div>
    }
  `,
})
export class Team {
  people = ['Ada Lovelace', 'Grace Hopper', 'Alan Turing'];
}
```

## On screen

A "Team" page with a red header and three rows. Each row starts with a colored circle showing bold initials, AL, GH, and AT, followed by the full names Ada Lovelace, Grace Hopper, and Alan Turing. The names in the data are plain strings; the pipe turned each one into its initials right in the template.

![Team list with initials avatars](../images/2026-10-24-custom-pipes.jpg)

# class-binding

## React

```bash
npm install classnames --save
```

Component:
```tsx
import classNames from 'classnames';

class Rocket extends React.Component {
  constructor(props) {
    super(props);
    this.state = { active: true };
  }

  render() {
    const classes = classNames({
      nasa: this.props.isNasa,
      active: this.state.active,
    });

    const sty = { backgroundColor: 'red' };

    return (<h1 className={classes} style={sty}>My rocket</h1>};
  }
}
```

## Angular

Component:
```ts
@Component({ ... })
class RocketComponent {
  @Input() isNasa: boolean;
  active = true;
  sty = { backgroundColor: 'red' }; // or 'background-color
}
```

Component template:
```html
<h1 [ngClass]="{ nasa: isNasa, active: active }"
    [ngStyle]="sty">My rocket</h1>
```

or

```html
<h1 [class.nasa]="isNasa" [class.active]="active"
    [style.backgroundColor]="sty.backgroundColor"
>My rocket</h1>
<!-- or [style.background-color]="" -->
```

### Other

```html
<div
  [style.border-color]="'yellow'"
  [style.border-style]="'solid'"
  [style.border-width.px]="10"
  [style.border-width.em]="10"
  [style.font-size.rem]="5"
  [style.font-size.em]="5"
  [style.font-size.px]="15"
></div>
```

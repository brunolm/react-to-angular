# events

## React

```tsx
class Rocket extends React.Component {
  // instead of `fly()` use `fly = () =>` to make `this` have the component context
  // another option would be `.bind(this)` which is bad for performance
  fly = (proxyEvent) => {
    console.log(proxyEvent);
    console.log(this); // Rocket
  };

  render() {
    return (<button onClick={this.fly}>rocket</button>);
  }
}
```

## Angular

Component:
```ts
@Component({ ... })
class RocketComponent {
  fly(event: Event) {
    console.log(event); // Event
    console.log(this); // Rocket
  }
}
```

Component template:
```html
<button (click)="fly($event)">rocket</button>
```

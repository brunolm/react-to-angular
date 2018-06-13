# events

## React

```tsx
class Rocket extends React.Component {
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

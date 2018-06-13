# state

## React

```tsx
class Rocket extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      flying: true,
    };
  }

  toggle() {
    this.setState((prevState) => ({
      flying: !prevState.flying,
    }));
  }

  render() {
    return (<div>{this.state.flying ? 'Yohoo' : 'meh'}</div>);
  }
}
```

## Angular

Component:
```ts
@Component({ ... })
class RocketComponent {
  flying = true;

  toggle() {
    this.flying = !this.flying;
  }
}
```

Component template:
```html
<div>{{ flying ? 'Yohoo' : 'meh' }}</div>
```

# props

## React

Parent file:
```tsx
<Rocket title="Hello Angular" />
```

Component:
```tsx
class Rocket extends React.Component {
  render() {
    return (<h1>{this.props.title}</h1>);
  }
}
```

## Angular

Parent file:
```html
<app-rocket title="Hello Angular" />
```

Component:
```ts
@Component({ selector: 'app-rocket', ... })
class RocketComponent {
  @Input() title: string;
}
```

Component template:
```html
<h1>{{ title }}</h1>
```

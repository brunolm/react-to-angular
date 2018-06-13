# attribute-binding

## React

Component:
```tsx
class Rocket extends React.Component {
  render() {
    const title = 'my rocket title';
    return (
      <div data-something="hello" custom-something="x" title="my rocket title">
        <span title={title}>My rocket</span>
      </div>
    );
  }
}
```

## Angular

Component:
```ts
@Component({ ... })
class RocketComponent {
  title = 'my rocket title';
}
```

Component template:
```html
<div [attr.data-something]="hello" [attr.custom-something]="x" title="my rocket title">
  <span [title]="title">My rocket</span>
</div>
```

# conditional-render

## React

```tsx
class Rocket extends React.Component {
  render() {
    let flyingStatusBar;

    if (value === 1) {
      flyingStatusBar = (<div>one</div>);
    }
    else if (value === 2) {
      flyingStatusBar = (<div>two</div>);
    }
    else {
      flyingStatusBar = (<div>three</div>);
    }

    return (<div>{flyingStatusBar}</div>);
  }
}
```

### Simple

```tsx
const flyingStatusBar = flying ? (<div>flying</div>) : undefined;

return (<div>{flyingStatusBar}</div>);
```

or

```tsx
return (
  <div>
    {flying &&
      <div>flying</div>
    }
  </div>
);
```

## Angular

Component:
```ts
@Component({ ... })
class RocketComponent {
  value = 3;
}
```

Component template:
```html
<div *ngIf="value === 1; else two">one</div>

<ng-template #two>
  <div *ngIf="value === 2; else three">two</div>
</ng-template>

<ng-template #three>
  <div>three</div>
</ng-template>
```

or

```html
<div [ngSwitch]="value">
  <div *ngSwitchCase="1">one</div>
  <div *ngSwitchCase="2">two</div>
  <div *ngSwitchCase="3">three</div>
  <div *ngSwitchDefault>default</div>
</div>

```

### Simple

Component:
```ts
@Component({ ... })
class Rocket {
  flying = true;
}
```

Component template:
```html
<div *ngIf="flying">flying</div>
```

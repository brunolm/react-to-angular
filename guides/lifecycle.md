# lifecycle

## React

https://twitter.com/dan_abramov/status/981712092611989509

### Mounting

```ts
constructor
getDerivedStateFromProps
render
componentDidMount
```

### Updating

```ts
getDerivedStateFromProps // new props only
shouldComponentUpdate // new props or setState
render
getSnapshotBeforeUpdate
componentDidUpdate
```

### Unmounting

```ts
componentWillUnmount
```

## Angular

https://angular.io/guide/lifecycle-hooks#lifecycle-sequence

```ts
ngOnChanges()
ngOnInit()
ngDoCheck()
ngAfterContentInit()
ngAfterContentChecked()
ngAfterViewInit()
ngAfterViewChecked()
ngOnDestroy()
```

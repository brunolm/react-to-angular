# lists

## React

Component:
```tsx
class AnimeList extends Component {
  animes = [
    'One Punch Man',
    'Dragon Ball Super',
    'Berserker',
  ];
  render() {
    return (
      <ul>
        {this.animes.map((anime, i) => (
          <li key={i}>{i}. {anime}</li>
        ))}
      </ul>
    );
  }
}
```

## Angular

Component:
```ts
@Component({ selector: 'app-rocket', ... })
class AnimeListComponent  {
  animes = [
    'One Punch Man',
    'Dragon Ball Super',
    'Berserker',
  ];
}
```

Component template:
```html
<ul>
  <li *ngFor="let anime of animes; let i = index">{{ i }}. {{ anime }}</li>
</ul>
```

## lists with id as keys

### React

Component:
```tsx
class AnimeList extends Component {
  animes = [
    { id: 1, name: 'One Punch Man' },
    { id: 2, name: 'Dragon Ball Super' },
    { id: 3, name: 'Berserker' },
  ];
  render() {
    return (
      <ul>
        {this.animes.map((anime, i) => (
          <li key={anime.id}>#{anime.id}. {anime.name} (index = {i})</li>
        ))}
      </ul>
    );
  }
}
```

### Angular

Component:
```ts
@Component({ selector: 'app-rocket', ... })
class AnimeListComponent  {
  animes = [
    { id: 1, name: 'One Punch Man' },
    { id: 2, name: 'Dragon Ball Super' },
    { id: 3, name: 'Berserker' },
  ];

  trackById(index, item) {
    return item.id;
  }
}
```

Component template:
```html
<ul>
  <li *ngFor="let anime of animes; let i = index; trackBy: trackById">
    #{{ anime.id }} {{ anime.name }} (index: {{ i }})
  </li>
</ul>
```

Example: switch `anime` array to a completely new array (not same references) it will keep track by id and not update existing items. Example usage: full list of animes filtered by a search field.

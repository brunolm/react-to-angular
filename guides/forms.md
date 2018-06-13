# forms

## React

```tsx
class Rocket extends React.Component {
  constructor(props) {
    super(props);
    this.state = { name: '' };

    this.validationSchema = {
      name: [
        (value) => (/^\w+@\w+.com$/i.test(value) ? { email: false } : { email: true }),
        (value) => (/^a/i.test(value) ? { pattern: false } : { pattern: true }),
      ],
    };

    this.errors = {};
    this.validationMessages = {
      email: 'gibe email pls',
      pattern: 'gibe this pattern pls',
    }
  }

  componentWillMount() {
    for (const field of Object.keys(this.state)) {
      this.errors = { ...this.validate(field, this.state[field]) };
    }
  }

  validate(name, value) {
    return this.validationSchema[name].reduce((a, b) => {
      a = { ...a, ...b(value) };
      return a;
    }, {});
  }

  handleChange = (e) => {
    const name = e.target.name;
    const value = e.target.value;
    this.setState({[name]: value}, () => {
      this.errors = { ...this.validate(name, value) };
      return false;
    });
  }

  handleSubmit = (e) => {
    e.preventDefault();
    const valid = Object.keys(this.errors).every((error) => !this.errors[error]);
    if (!valid) {
      console.log(this.errors);
    }
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit} ref={form => this.formEl = form} noValidate>
        <label>
          <input type="email" name="name"
            value={this.state.name} onChange={this.handleChange} />
          <div>
            { Object.keys(this.errors).map((error, i) => (
              <div key={i}>{ error ? this.validationMessages[error] : '' }</div>
            )) }
          </div>
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```

## Angular

Module:
```ts
import { ReactiveFormsModule } from '@angular/forms';

@NgModule({
  imports: [ BrowserModule, ReactiveFormsModule ],
  ...
})
```

Component:
```ts
import { FormControl, FormGroup, Validators } from '@angular/forms';

@Component({ ... })
class RocketComponent {
  form = new FormGroup({
    name: new FormControl(undefined, [Validators.email, Validators.pattern(/^a/)]),
  });

  validationMessages = [
    { type: 'email', message: 'gibe email pls' },
    { type: 'pattern', message: 'gibe this pattern pls' },
  ];

  submit() {
    if (this.form.invalid) {
      console.log('error')
    }
  }
}
```

Component template:
```html
<form (ngSubmit)="submit()" [formGroup]="form">
  <input type="text" formControlName="name" />

  <div *ngFor="let validation of validationMessages">
    <div *ngIf="(form.get('name').touched || form.get('name').dirty) && form.get('name').errors && form.get('name').errors[validation.type]">
      {{ validation.message }}
    </div>
  </div>

  <button type="submit">Send</button>
</form>
```

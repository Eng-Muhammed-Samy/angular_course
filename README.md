# Es6 Features

## Constants

#### Es6

```javascript
const PI = 3.14; // Es6
```

#### Native Javascript

```javascript
Object.defineProperty(typeof global === "object" ? global : window, "PI", {
  value: 3.141593,
  enumerable: true,
  writable: false,
  configurable: false,
});
```

## Default Parameter Values

#### Es6

```javascript
function f(x, y = 7, z = 42) {
  return x + y + z;
}
```

#### Native Javascript

```javascript
function f(x, y, z) {
  if (y === undefined) y = 7;
  if (z === undefined) z = 42;
  return x + y + z;
}
```

## Rest Parameter

#### Es6

```javascript
function f(x, y, ...a) {
  return (x + y) * a.length;
}
f(5, 5, 1, 2, 3, 4, 5); // 50
```

#### Native Javascript

```javascript
function f(x, y) {
  var a = Array.prototype.slice.call(arguments, 2);
  return (x + y) * a.length;
}
```

## Spread Operator

#### Es6

```javascript
var params = ["hello", true, 7];
var other = [1, 2, ...params]; // [ 1, 2, "hello", true, 7 ]
```

```javascript
function f(x, y, ...a) {
  return (x + y) * a.length;
}
f(1, 2, ...params);
```

```javascript
var str = "foo";
var chars = [...str]; // [ "f", "o", "o" ]
```

#### Native Javascript

```javascript
var params = ["hello", true, 7];
var other = [1, 2].concat(params); // [ 1, 2, "hello", true, 7 ]
```

```javascript
function f(x, y) {
  var a = Array.prototype.slice.call(arguments, 2);
  return (x + y) * a.length;
}
f.apply(undefined, [1, 2].concat(params));
```

```javascript
var str = "foo";
var chars = str.split(""); // [ "f", "o", "o" ]
```

## String Interpolation

#### Es6

```javascript
var customer = { name: "Foo" }
var message = `Hello ${customer.name}

```

#### Native

```javascript
var customer = { name: "Foo" };
var message = "Hello " + customer.name;
```

## Binary & Octal Literal

#### Es6

```javascript
0b111110111 === 503; //(binary to decimals) -->  true
0o767 === 503; // (octal to decimal )  --> true
```

#### Native

```javascript
// parseInt("binary or octal", base)
parseInt("111110111", 2) === 503;
parseInt("767", 8) === 503;
```

## Enhanced Object Properties (Property Shorthand)

#### Es6

```javascript
var x = 0,
  y = 0;
obj = { x, y };
```

#### Native

```javascript
var x = 0,
  y = 0;
obj = { x: x, y: y };
```

## Class Definition

#### Es6

```javascript
class Shape {
  constructor(id, x, y) {
    this.id = id;
    this.move(x, y);
  }
  move(x, y) {
    this.x = x;
    this.y = y;
  }
}
```

#### Native

```javascript
var Shape = function (id, x, y) {
  this.id = id;
  this.move(x, y);
};
Shape.prototype.move = function (x, y) {
  this.x = x;
  this.y = y;
};
```

## Inheritance

#### Es6

```javascript
class Rectangle extends Shape {
  constructor(id, x, y, width, height) {
    super(id, x, y);
    this.width = width;
    this.height = height;
  }
}
```

#### Native

```javascript
var Rectangle = function (id, x, y, width, height) {
  Shape.call(this, id, x, y);
  this.width = width;
  this.height = height;
};
Rectangle.prototype = Object.create(Shape.prototype);
```

## Setter/Getter

#### Es6

```javascript
    set width  (width)  { this._width = width }
    get width  ()       { return this._width }
```

#### Native

```javascript
Rectangle.prototype = {
  set width(width) {
    this._width = width;
  },
  get width() {
    return this._width;
  },
};
```

## Modules

#### Es6

```javascript
//  lib/math.js
export function sum(x, y) {
  return x + y;
}
export var pi = 3.141593;

//  someApp.js
import * as math from "lib/math";
console.log("2π = " + math.sum(math.pi, math.pi));

//  otherApp.js
import { sum, pi } from "lib/math";
console.log("2π = " + sum(pi, pi));
```

#### Native

```javascript
//  lib/math.js
LibMath = {};
LibMath.sum = function (x, y) {
  return x + y;
};
LibMath.pi = 3.141593;

//  someApp.js
var math = LibMath;
console.log("2π = " + math.sum(math.pi, math.pi));

//  otherApp.js
var sum = LibMath.sum,
  pi = LibMath.pi;
console.log("2π = " + sum(pi, pi));
```

[ES6 VS ES5 Reference](http://es6-features.org/#Constants)

## Webpack introduction

## Definition

> At its core, webpack is a **static module bundler** for modern JavaScript applications. When webpack processes your application, it internally builds a **_dependency graph_** from one or more entry points and then combines every module your project needs into one or more bundles, which are static assets to serve your content from.

> Since **version 4.0.0**, webpack does not require a _configuration file_ to bundle your project. (**_webpack.config.js_**)

## To get started you only need to understand its Core Concepts:

## - **Entry**

```
module.exports = {
  entry: './path/to/my/entry/file.js',
};

```

## - **Output**

```
module.exports = {
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'my-first-webpack.bundle.js',
  },
};
```

## - **Loaders**

##### At a high level, loaders have two properties in your webpack configuration:

- _The test property identifies which file or files should be transformed._
- _The use property indicates which loader should be used to do the transforming_

```javascript
module.exports = {
  module: {
    rules: [{ test: /\.txt$/, use: "raw-loader" }],
  },
};
```

## - **Plugins**

```javascript
module.exports = {
  plugins: [new HtmlWebpackPlugin({ template: "./src/index.html" })],
};
```

## - **Mode**

```javascript
module.exports = {
  mode: "production", // or development
};
```

## - **Browser Compatibility**

```
Webpack supports all browsers that are ES5-compliant (IE8 and below are not supported)
```

[Webpack reference](https://webpack.js.org/concepts/)

# Introduction To Angular

### What is Angular?

_Angular is a development platform, built on TypeScript. As a platform, Angular includes:_

- A component-based framework for building scalable web applications
- A collection of well-integrated libraries that cover a wide variety of features, including routing, forms management, client-server communication, and more

- A suite of developer tools to help you develop, build, test, and update your code

## Angular App

1. **install angular cli**

```javascript
npm i @angular/cli -g
```

2. **create fisrt app**

```javascript
ng new first-app
```

## Angular Component

#### what is component

![component](https://i.stack.imgur.com/AUsyx.png)
_angular component consists of 3 files (**typescript [main file]**, html ans css)_

![angular component](https://dotnettrickscloud.blob.core.windows.net/img/angular/angular-component-page-view.png)

```javascript
import { Component } from "@angular/core";

@Component({
  // decorator (meta data)
  selector: "app-root",
  templateUrl: "./app.component.html", // html file
  styleUrls: ["./app.component.css"], // css files
})
export class AppComponent {
  constructor() {}
}
```

## Component lifecycle

![lifecycle](https://codecraft.tv/courses/angular/components/lifecycle-hooks/images/lifecycle-hooks.png)

- **_ngOnChanges:_** This hook is called when Angular sets or resets data-bound input properties. It receives a SimpleChanges object of current and previous property values. It is called before ngOnInit and whenever one or more data-bound input properties change. You can use this hook to respond to changes in input properties or to initialize them.
  
- **_ngOnInit:_** This hook is called once after the first ngOnChanges. It is a good place to initialize the component or directive, fetch data from a service, or set up subscriptions.
  
- **_ngDoCheck:_** This hook is called every time Angular runs change detection. It is a custom change detection hook that you can use to detect and act upon changes that Angular can’t or won’t detect on its own. For example, you can use this hook to implement a custom comparison for objects that are not immutable.
  
- **_ngAfterContentInit:_** This hook is called once after Angular projects external content into the component’s view, or into the view that a directive is in. It is a good place to query for projected content using @ContentChild or @ContentChildren.
  
- **_ngAfterContentChecked:_** This hook is called after every Angular check of the projected content. It is similar to ngDoCheck, but for projected content.
  
- **_ngAfterViewInit:_** This hook is called once after Angular initializes the component’s view, or the view that contains the directive. It is a good place to query for view elements using @ViewChild or @ViewChildren.
  
- **_ngAfterViewChecked:_** This hook is called after every Angular check of the component’s view, or the view that contains the directive. It is similar to ngDoCheck, but for view elements.
  
- **_ngOnDestroy:_** This hook is called once before Angular destroys the component or directive. It is a good place to perform any cleanup logic, such as unsubscribing from observables, detaching event handlers, or freeing resources.

## Data bindnig

![data binding](https://vegibit.com/wp-content/uploads/2018/11/angular-databinding.png)

- **String Interpolation**

```javascript
 <div> {{person.name}} </div>
```

- **Property Binding**

```javascript
 <img [src]="itemImageUrl">
```

- **Event Binding**

```javascript
 <button (click)="onSave()">Save</button>
```

- **Two way binding**

```javascript
    <input [(ngModel)]="person.name" />
```

> need to import import { FormsModule } from '@angular/forms' for two way binding in forms in app module to work

## Directives

1. **Component Directives**

   _Component directive, is nothing but a simple class which is decorated with the @component decorato_

2. **Structural Directives**

   - **\*ngIf**

   ```javascript
   <div *ngIf ="condition">show content</div>
   ```

   - **\*ngSwitch**

   ```javascript
       <ul *ngFor="let person of people" [ngSwitch]="person.country"> // (1)

       <li *ngSwitchCase="'UK'" //(2)
           class="text-success">{{ person.name }} ({{ person.country }})
       </li>
       <li *ngSwitchDefault //(3)
           class="text-warning">{{ person.name }} ({{ person.country }})
       </li>
       </ul>`
   ```

   - **\*ngFor**

   ```javascript
   <ul *ngFor="let person of persons">
       <li *ngIf="person.age < 30"> (1)
       {{ person.name }} ({{ person.age }})
       </li>
   </ul>
   ```

   - **\*ngIf then else**

   ```javascript
   <div *ngIf="condition; then thenBlock else elseBlock"></div>
   <ng-template #thenBlock>Content to render when condition is true.</ng-template>
   <ng-template #elseBlock>Content to render when condition is false.</ng-template>
   ```

3. **Attribute Directives**

- **\*ngClass**

```javascript
    <div [ngClass]="{'text-success': country === 'UK'}"> </div>
```

- **\*ngStyle**

```javascript
    <div [ngStyle]="{'background-color': country === 'UK' ? 'green' : 'red' }"> </<div>
```

## Sharing data between components

![sharing data](https://worldline.github.io/angular-training/assets/img/child-parent.42647f1d.png)

# Routing

### The advantages of an SPA are

- **Can be faster**. Instead of making a time-consuming request to a far away
  server every time the URL changes the client app updates the page much
  faster.
- **Less bandwidth required**. We don’t send over a big HTML page for every
  URL change, instead we might just call a smaller API which returns just
  enough data to render the change in the page.

## Route Configuration

- Import the **`AppRoutingModule`** into AppModule and add it to the
  imports array.
- **`Import`** **`RouterModule`** and Routes into your routing module.
- Define your routes in your _`Routes array`_ into your routing module.
- Add your routes to your application using **_`routerLink`_** and update your
  component **template** to include <router-outlet>. This element informs
  Angular to update the application view with the component for the selected
  route, it acts as a placeholder that Angular dynamically fills based on the
  current router state.

## Navigation

`To navigate to other component will use :`

#### - From template using Router link on **`<a>`** tag with 2 ways :

```javascript
    <a class="nav-link" routerLink="/login">login</a>
    <a [routerLink]="'/login'">Login</a>
    //or
    [routerLink]="['/login']"
```

#### - Add child routes to a parent one

```javascript
    { path: "artist/”,
        children: [
        { path: "", component:ArtistTrackListComponent }]
    },
```

#### - Add general route for not found routes

```javascript
{ path: "**", component: HomeComponent }
 //or
 {path: '**', component:PageNotFoundComponent }

```

### - **_`Navigation : routerLinkActive [Self Study]`_**

#### - Navigation : Using navigate

```javascript
    import Router from ‘@angular/router’
    constructor(private router: Router){}
    this.router.navigate([‘/details’])
```

#### - Parameterised Routes

1. **First we need to configure this id in routes array**

```javascript
const routes: Routes = [
  { path: "movie/:id", component: MovieComponent }, //(1)
];
```

> The path has a variable called id, we know it’s a variable since it begins with a colon (`:`)

2. **To go to this parameterised route we will be from html or ts**

```javascript
// From html
[routerLink] = "['movie', movie.id]";
// From ts
this.router.navigate(["movie", idValue]);
```

3. **To get this parameter in component will user ActivatedRoute**

```javascript
import {ActivatedRoute} from "@angular/router";
constructor(private route: ActivatedRoute) {
this.route.snapshot.params['id']
}
```

## Pipes

> `Pipes are simple functions you can use in template expressions to accept an input value and return a transformed value.`

#### Angular provides built-in pipes for typical data transformations like :

- DatePipe: Formats a date value according to locale rules.

```javascript
 {{ today | date : 'MMMM YYYY' }}
```

- UpperCasePipe: Transforms text to all upper case.

```javascript
{
  {
    name | uppercase;
  }
}
```

- LowerCasePipe: Transforms text to all lower case.

[For More Info](https://angular.io/guide/pipes)

### Custom Pipes

**To generate custom pipe you need to run :**

```
 ng generate pipe pipeName
```

For example you can generate custom pipe that transform file size to MB :

```javascript
 transform(value: any, ...args: any[]): unknown {
    return (value / (1024 * 1024)).toFixed(2) + 'MB';
 }

```
# Forms
Angular provides two different approaches to handling user input through forms: 
reactive and template-driven. Both capture user input events from the view, validate 
the user input, create a form model and data model to update, and provide a way to 
track changes.

[Docs](https://angular.io/guide/forms)

## Forms : Template driven forms
- Template-driven forms use two-way data binding to update the data model in 
the component as changes are made in the template and vice versa.
- Template-driven forms rely on directives defined in the `FormsModule`.
- The `NgModel` directive reconciles value changes in the attached form element 
with changes in the data model, allowing you to respond to user input with 
input validation and error handling.
- The `NgForm` directive creates a top-level **`FormGroup`** instance and binds it to a `<form>` element to track aggregated form value and validation status. As soon 
as you import FormsModule, this directive becomes active by default on all `<form>` tags. You don't need to add a special selector.

```html
    <form #form="ngForm" class="w-50" (ngSubmit)="signup(form)">
        <div class="mb-3">
            <div>
                <label class="form-label" for="emil">Email</label>
                <input required email class="form-control" type="text" #emil="ngModel" [(ngModel)]="username" name="email" id="email">
            </div>
           
             <div class="alert alert-danger py-2"
                    *ngIf="emil?.invalid && (emil?.touched || emil?.dirty)">
                    <span *ngIf="emil?.errors?.['required']">Email Required</span>
                    <span *ngIf="emil?.errors?.['email']">Email Not Valid</span>
            </div>
        </div>
    </form>
```
## Forms : Reactive forms

To work with reactive forms, you’ll need to import the **`ReactiveFormsModule`** 

### in module
```javascript
    import { ReactiveFormsModule } from '@angular/forms';
    // And add it to imports array in app module
    @NgModule({
    imports: [... , ReactiveFormsModule ]
    })
```
### in tempale Html
```html
   <form [formGroup]="form" class="w-50" (ngSubmit)="login()">
        <div class="my-2">
            <div>
                <label class="form-label" for="username">Email</label>
                <input type="text" formControlName="username" class="form-control">
            </div>
        </div>
    </form>
```
#### Let’s break it down:
* ***`formGroup`***: The form will be treated as a FormGroup in the component class, so 
the formGroup *`directive`* allows to give a `name` to the form group.
* ***`ngSubmit`***: This is the event that will be triggered upon submission of the form.
* ***`formControlName`***: Each form field should have a *`formControlName directive`*
with a value that will be the name used in the component class.

### in Ts
```javascript
form!: FormGroup;

ngOnInit(): void {
    this.form = new FormGroup({
        username: new FormControl(null, [Validators.required]),
    });
}

login(){
    console.log(this.form.getRawValue())
}

```

# Services
![services](https://www.simplilearn.com/ice9/free_resources_article_thumb/Angular_Services.PNG)

### Why Services !
* Components *`shouldn't fetch or save data`* directly and they certainly 
shouldn't knowingly present fake data. They should **`focus on presenting data`** and delegate data access to a service.
* When you provide the service at the root level, `Angular creates a single, shared instance of this service` and injects into any class that asks for it.
* Registering the provider in the `@Injectable metadata` also allows Angular 
to `optimize` an application by *`removing the service`* if it turns out not to be used after all


## Observable
**`Observable`** is a `stream of events or data` , **Subscribing** "`kicks off`" the observable 
stream. Without a subscribe (or an async pipe) the stream won't start `emitting` values.

## Subscribe
-  A function that defines how to obtain or generate values or messages to 
be published. This function is executed when a consumer calls the `subscribe()` method of an observable.
- The `subscribe()` method takes a JavaScript object `(called an observer)` with up to *`three callbacks`*,one for each type of `notification` that an `observable` can deliver:
    - The **`Success`** notification sends a value such as a number, a string, or an object.
    - The **`error`** notification sends a JavaScript Error or exception.
    - The **`complete`** notification doesn't send a value, but the handler is called when the call completes. cheduled values can continue to be returned after the call completes.

```javascript
    const observable = new Observable(subsciper => {
      subsciper.next(1);
      subsciper.next(2);
      setTimeout(() => {
        subsciper.next(3)
        subsciper.complete()
      }, 2000);
     })
  
     observable.subscribe({
      next: res => console.log("value: " , res),
      error: (err) => console.log("error: ", err)
      complete: () => console.log("completed") 
     })
```
# Http
Most front-end applications need to communicate with a server over the **`HTTP protocol`**, in order to `download` or `upload` data and access other *`back-end`* services. 
- Angular provides a simplified client **`HTTP API`** for Angular applications, the `HttpClient` service class in` @angular/common/http.`

```javascript
// add this to mdule
    import { HttpClientModule } from '@angular/common/http';

//add this to service
    import { HttpClient } from '@angular/common/http';
    getList(): Observable<any> {
    return this.http.get('API');
    }

//add this to component ts
    this.service.getData().subscribe(
        data => { this.data = data },
        error => { console.log('error: ', error)},
        () => { console.log('complete ', "compelete"); 
    });

```

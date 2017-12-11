---
layout: default
---
# Angular
---

>Angular is a framework for building client applications in HTML and either JavaScript or a language like TypeScript that compiles to JavaScript.[https://angular.io](https://angular.io/guide/architecture#architecture-overview)

A component **controls a patch of screen called a view**. As code, a component is a class, with a decorator. The class is JavaScript, specifically TypeScript. It includes all the code needed for the the component’s behaviour during its lifetime.

A decorator is a function that modifies a class. It has parameters, which is an object composed of configuration information as key-value pairs. This object is metadata, and the Angular runtime uses the metadata when initializing the component.

One of the decorator’s properties is a template, defines the appearance of the component.

By definition, HTML is the language of the Angular template. Almost all HTML elements are valid in a template, except for these: html, body, base, and script.

Templates: developers can define a component's view with its companion template. A template is a form of HTML that **tells Angular how to render the component**.
See more: [template syntax](https://angular.io/guide/template-syntax)

Metadata tells Angular **how to process a class**. In other words, To tell Angular that HeroListComponent is a component, attach metadata to the class. It can be attached by using a decorator. (ex: @Component({)

![Image]({{ site.globalurl }}/contents/img_angular/architecture1.jpg)

Another decorator property is the selector. Its value is the name of the custom HTML element in the parent template that becomes the component.

How does the MVC (or MVVM) design patterns map to Angular? Well, in Angular:
The component has the code for the controller and the view model.
The template has the code for the view.


**In Data Binding**, Add binding markup to the template HTML to tell Angular how to connect both sides.
There are four forms of data binding syntax. Each form has a direction — to the DOM, from the DOM, or in both directions.[angular.io](https://angular.io/guide/architecture#data-binding)

![Image]({{ site.globalurl }}/contents/img_angular/architecture2.jpg)

Binding types can be grouped into three categories distinguished by the direction of data flow: from the source-to-view, from view-to-source, and in the two-way sequence: view-to-source-to-view:[angular.io](https://angular.io/guide/template-syntax#binding-syntax-an-overview)

![Image]({{ site.globalurl }}/contents/img_angular/architecture3.jpg)


## Week 8 ##

### Decorator: ###
Again, 
> A decorator is a function that modifies a class. It has parameters, which is an object composed of configuration information as key-value pairs. This object is metadata, and the Angular runtime uses the metadata when initializing the component.

### @Input Decorator ###
If we want to reference the “message” value inside the BlueBoxComponent, we simply add an “@input” decorator to the “message” property.
```js
import { Component, OnInit, Input } from '@angular/core';

@Component({
  selector: 'app-blue-box',
  templateUrl: './blue-box.component.html',
  styleUrls: ['./blue-box.component.css']
})
export class BlueBoxComponent implements OnInit {

  constructor() { }

  ngOnInit() {
  }

  @Input() message: string; // make the "message" property available for binding
}
```
## @Directive decorator ##
Build a simple attribute directive: **ng generate directive highlight**
```js
import { Directive } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
  constructor() { }
}
```

## @Component decorator ##
### Binding Sytax: ###
One of the decorator’s properties is a template, defines the appearance of the component. Angular templates are dynamic. When Angular renders them, it transforms the DOM according to the instructions given by **directives**.[angular.io](https://angular.io/guide/architecture#directives)

![Image]({{ site.globalurl }}/contents/img_angular/architecture3.jpg)

### Binding Targets ###
![Image]({{ site.globalurl }}/contents/img_angular/week81.jpg)
![Image]({{ site.globalurl }}/contents/img_angular/week82.jpg)

### Property binding or interpolation? ###
```html
<p><img src="{{heroImageUrl}}"> is the <i>interpolated</i> image.</p>
<p><img [src]="heroImageUrl"> is the <i>property bound</i> image.</p>
```

### lifecycle hooks: ###
Angular calls the lifecycle hook methods at specific moments. For example, 
**ngOnInit()** initializes the directive/component after Angular first displays the data-bound properties and sets the directive/component's input properties. Called once, after the first ngOnChanges(). , 
**ngOnDestroy()** cleanups just before Angular destroys the directive/component. Unsubscribe Observables and detach event handlers to avoid memory leaks. Called just before Angular destroys the directive/component., 

![Image]({{ site.globalurl }}/contents/img_angular/hooks-in-sequence.png)

### directives: ###
There are three kinds of directives in Angular:

1. Components—directives with a template.
2. **Structural directives—change the DOM layout by adding and removing DOM elements.**
3. Attribute directives—change the appearance or behavior of an element, component, or another directive.

Build a simple attribute directive: **ng generate directive highlight**

two built-in structural directives: *ngFor, *ngIf

```
<li *ngFor="let hero of heroes"></li>
<app-hero-detail *ngIf="selectedHero"></app-hero-detail>
```

> *ngFor tells Angular to stamp out one <li> per hero in the heroes list. *ngIf includes the HeroDetail component only if a selected hero exists.

See more: layout structure- ngModel, modify aspects of DOM elements and components- ngSwitch, ngClass, you can also write your own directives- custom directive

## Routing ##
The purpose of routing is to implement navigation in an app by matching a URL/path to a component.
### Main Routing Components ###
Adding routing to an app: **ng new animals --routing -st**

### New source code: app-routing.module.ts ###
```js
// app-routing.module.ts
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { HorseComponent } from "./horse.component";
import { HomeComponent } from "./home.component";
import { PageNotFoundComponent } from "./page-not-found.component";

const routes: Routes = [
  { path: 'horse', component: HorseComponent },
  { path: 'home', component: HomeComponent },
  { path: '', redirectTo: '/home', pathMatch: 'full' },
  { path: '**', component: PageNotFoundComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }

// Updated code: app.module.ts
import { AppRoutingModule } from './app-routing.module';
...
imports: [
    BrowserModule,
    AppRoutingModule
  ],
...  
```

1. Plan your components and routes
2. Add one or more components that will participate in routing
3. In the HTML markup (i.e. the view code) of the component that will “host” the routed component, add a **<router-outlet>** element
4. In the HTML markup of a navigation component (or any kind of component), use the **routerLink** attribute in the <a> element instead of the href attribute


Directives & Files used when creating an Angular app with Routing are: 
routerLink: <a class="nav-link" routerLink="/horse">Horse</a>
routerLinkActive: 
```html
<ul class="nav navbar-nav">
    <li routerLinkActive="active"><a routerLink="home">Home</a></li>
...
```
router-outlet: <router-outlet></router-outlet>

[Adding routing to an existing app](https://sictweb.github.io/web422/notes/angular-routing-existing-app)

## WEEK9 ##
Angular service:
can provide functionality - service - to one or more components. 
code asset that performs a task. 
not have a user interface.
Often its main task is to perform data service operations (e.g. fetch, add, edit, transform).
can be used by any of your app’s components
Enables you to write the code once, and use it in many places.
mediates between the view (rendered by the template) and the application logic (which often includes some notion of a model).

- how we can create services using the Angular CLI

>ng g s DataManager --module=app --spec false
```js
//data-manager.service.ts
import { Injectable } from '@angular/core';

@Injectable()
export class DataManagerService {
  constructor() { }
}
// simplest implementation of a service
// 1. Declare a private field to hold the data
// 2. Write a public function to deliver the data
```
In  app module (app.module.ts), 
A new import statement near the top
A declaration in the providers array of the @NgModule decorator
These updates enable the new service to be available to every component in the app.
The main task to complete is to write a function, in the service, that can be called by a component. 
it will deliver data to the component. 
Then, the component can display/render the data in its user interface




1. Dependency Injection
- how to include them in our Components using DI (Dependency Injection).

We blend all three together when working with a web service.: HttpClient, RxJS, Observable

Enable the app to use HTTP
In app.module.ts, add the HttpClientModule to the imports collection in the @NgModule decorator.
- import { HttpClientModule } from "@angular/common/http";

To use HttpClient anywhere else in your application, import { HttpClient } from "@angular/common/http";



2. HttpClient
HttpClient is Angular’s mechanism for communicating with a remote server over HTTP.
Additional benefits of HttpClient include testability support, strong typing of request and response objects, request and response interceptor support, and better error handling.

To make HttpClient available everywhere in the app:

1. Open the root AppModule for editing (app.module.ts),
2. Import the HttpClienModule symbol from @angular/common/http,
3. Add it to the @NgModule.imports array.

HttpClient includes a get() function. In essence, it is a stream of asynchronous data. The data could be a single object, or a collection. 



- how we can use it to create “Observable” service methods
- RxJS is a library for composing asynchronous and event-based programs by using observable sequences. to make it easier to compose asynchronous or callback-based code.
  - Observables
    Observables  allow us to watch (observe) the changing values of data over time and execute code when these changes occur.
    [rangle.io](https://angular-2-training-book.rangle.io/handout/observables/) open up a continuous channel of communication in which multiple values of data can be emitted over time.
    [RxJS](http://reactivex.io/rxjs/manual/overview.html)
	Observable: represents the idea of an invokable collection of future values or events.
	Observer: is a collection of callbacks that knows how to listen to values delivered by the Observable.
	Subscription: represents the execution of an Observable, is primarily useful for cancelling the execution.
	Operators: are pure functions that enable a functional programming style of dealing with collections with operations like map, filter, concat, flatMap, etc.
	Subject: is the equivalent to an EventEmitter, and the only way of multicasting a value or event to multiple Observers.
	Schedulers: are centralized dispatchers to control concurrency, allowing us to coordinate when computation happens on e.g. setTimeout or requestAnimationFrame or others.

  - subscribing

5. Route & Query Parameters(ie: /product/3 or /product-list?page=2)




### Creating an "Injectable" Service / Injecting Modules and Services (Dependency Injection / the "constructor" method) ###
### Using the HttpClient Module to return an Observable (with a specific type) to fetch data from a Web API ###
### Working with (subscribing to) Observables ###
### Working with Route & Query Parameters with the ActivatedRoute service ###





Dependency injection
HttpClient and asynchrony
Observable (from RxJS)
Input directive
Data binding in component templates
Structural directives, *ngFor and *ngIf
Routing parameters
Error handling



you can generate a service using the Angular CLI with the command "ng g s serviceName --spec false"
so do not forget to add them to the providers array of @ngModule in app.module.ts. 
get" request (using the HTTPClient module) with the path: "/positions" or "/position/id"
will return an Observable of type Position[], ie: Observable<Position[]> 
Now, for any component who has "injected"  the LogService, they can either subscribe to the public getLog "Subject", or write a message to be stored and broadcasted to subscribers (using the "writeLog" method) 

EmployeesComponent (employees.component.ts) 
 
Properties: 
•	employees ( type Employee[] ) 
•	filteredEmployees ( type Employee[] ) 
•	getEmployeesSub ( type any ) 
Methods:  
•	constructor() 
In this method, we must inject the following Services: 
o	EmployeeService from employee.service o Router from @angular/router 
•	ngOnInit() 
In this method, we will use Injected services / modules to perform the following task: 
o	populate the "employees" and "filteredEmployees" properties using the EmployeeService service (Note: 
a reference to the subscription should be stored using "getEmployeesSub" so that it can be disposed of later) 
•	routeEmployee(id: string) 
In this method, we use the Injected router instance to "navigate" the to the /employee/id route (where id is the parameter passed to the function) 
•	ngOnDestroy 
In this method we call the "unsubscribe()" methods on any saved subscriptions within the component (ie: getEmployeesSub) - Note: we must make sure they are not "undefined" before we call "unsubscribe()" 


### Creating a Service to work with Data ###
1. Correctly creating a service using the Angular CLI
2. Working with the HttpClient Module in our services / application
3. Creating classes to define the structure of the returned data (and using them to define “Observable” service methods)
4. Injecting the service into our Components using their constructor methods
5. Subscribing to (injected) Observable service methods and updating Component data
6. Rendering Component data in its template

### Checkpoint ###

At this point in time, we have added, configured, and used a service in our app. In multiple components.

The pattern is predictable:

Create the service
Add functions that deliver data (or otherwise perform data service operations)
In a component, configure it to use a service
Render whatever data you need in your component’s HTML template

### Enable the app to use HTTP ###
import { HttpClientModule } from "@angular/common/http";
add the HttpClientModule to the imports collection in the @NgModule decorator.
Then the user component, 
import { HttpClient } from "@angular/common/http";


Create a new source code file named vm-typicode.ts

And, Prepare the service in the service
import { Observable } from "rxjs/Observable";

import { Post, Comment, Geo, Address, Company, User } from "./vm-typicode";

private url = "http://jsonplaceholder.typicode.com";

getPosts(): Observable<Post[]> {
    return this.http.get<Post[]>(`${this.url}/posts`)
  }

  getComments(): Observable<Comment[]> {
    return this.http.get<Comment[]>(`${this.url}/comments`)
  }

  getUsers(): Observable<User[]> {
    return this.http.get<User[]>(`${this.url}/users`)
  }

// this.userService.getPosts().subscribe(users => this.users = users);

<a *ngFor="let product of products"
  [routerLink]="['/product-details', product.id]">
  {{ product.name }}
</a>

goToProductDetails(id) {
  this.router.navigate(['/product-details', id]);
}

```js
import { Component, OnInit, OnDestroy } from '@angular/core';
import { ActivatedRoute } from '@angular/router';

@Component({
  selector: 'product-details',
  template: `
    <div>
      Showing product details for product: 
    </div>
  `,
})
export class LoanDetailsPage implements OnInit, OnDestroy {
  id: number;
  private sub: any;

  constructor(private route: ActivatedRoute) {}

  ngOnInit() {
    this.sub = this.route.params.subscribe(params => {
       this.id = +params['id']; // (+) converts string 'id' to a number

       // In a real app: dispatch action to load the details here.
    });
  }

  ngOnDestroy() {
    this.sub.unsubscribe();
  }
}
```
<a [routerLink]="['product-list']" [queryParams]="{ page: 99 }">Go to Page 99</a>
goToPage(pageNum) {
    this.router.navigate(['/product-list'], { queryParams: { page: pageNum } });
}

```js
import { Component } from '@angular/core';
import { ActivatedRoute, Router } from '@angular/router';

@Component({
  selector: 'product-list',
  template: `<!-- Show product list -->`
})
export default class ProductList {
  constructor(
    private route: ActivatedRoute,
    private router: Router) {}

  ngOnInit() {
    this.sub = this.route
      .queryParams
      .subscribe(params => {
        // Defaults to 0 if no query param provided.
        this.page = +params['page'] || 0;
      });
  }

  ngOnDestroy() {
    this.sub.unsubscribe();
  }

  nextPage() {
    this.router.navigate(['product-list'], { queryParams: { page: this.page + 1 } });
  }
}
```


In horse.component.ts, use the new function(s) in the service 

<p>All posts:</p>
    <table class="table table-striped">
      <tr>
        <th>User ID</th>
        <th>Title</th>
        <th>Body</th>
      </tr>
      <tr *ngFor='let p of posts'>
        <td>{{p.userId}}</td>
        <td>{{p.title}}</td>
        <td>{{p.body}}</td>
      </tr>
    </table>
    <hr>

```js
app.module.ts
import { HttpClientModule } from "@angular/common/http";
...
imports: [ ... HttpClientModule ...],
  providers: [DataManagerService],
...

data-manager.service.ts
import { Injectable } from '@angular/core';
import { HttpClient } from "@angular/common/http";
import { Observable } from "rxjs/Observable";
import { Post, Comment, Geo, Address, Company, User } from "./vm-typicode";

@Injectable()
export class DataManagerService {
  // Fields
  private teachers: string[] = [];
  private url = "http://jsonplaceholder.typicode.com";

    constructor(private http: HttpClient) { 
    // Load the teachers collection
    this.teachers.push('Pat');
    this.teachers.push('Peter');
    this.teachers.push('Sharmin');
    this.teachers.push('Sunny');
    this.teachers.push('James');
  }
  // Functions
  getTeachers() {
    return this.teachers;
  }
  getPosts(): Observable<Post[]> {
    return this.http.get<Post[]>(`${this.url}/posts`)
  }
  getComments(): Observable<Comment[]> {
    return this.http.get<Comment[]>(`${this.url}/comments`)
  }
  getUsers(): Observable<User[]> {
    return this.http.get<User[]>(`${this.url}/users`)
  }
}

horse.component.ts
import { Component, OnInit } from '@angular/core';
import { DataManagerService } from "./data-manager.service";
import { Post } from "./vm-typicode";
...
export class HorseComponent implements OnInit {

  posts: Post[];
  
  constructor(private m: DataManagerService) { }

  ngOnInit() {
    this.getPosts();
  }

  getPosts(): void {
    this.m.getPosts()
    .subscribe(posts => this.posts = posts);
  }
}
horse.component.html
  <div class="panel-body">
    <p>All posts:</p>
    <table class="table table-striped">
      <tr>
        <th>User ID</th>
        <th>Title</th>
        <th>Body</th>
      </tr>
      <tr *ngFor='let p of posts'>
        <td>{{p.userId}}</td>
        <td>{{p.title}}</td>
        <td>{{p.body}}</td>
      </tr>
    </table>

<a *ngFor="let product of products"
  [routerLink]="['/product-details', product.id]">
  {{ product.name }}
</a>

goToProductDetails(id) {
  this.router.navigate(['/product-details', id]);
}


import { Component, OnInit, OnDestroy } from '@angular/core';
import { ActivatedRoute } from '@angular/router';

@Component({
  selector: 'product-details',
  template: `
    <div>
      Showing product details for product: 
    </div>
  `,
})
export class LoanDetailsPage implements OnInit, OnDestroy {
  id: number;
  private sub: any;

  constructor(private route: ActivatedRoute) {}

  ngOnInit() {
    this.sub = this.route.params.subscribe(params => {
       this.id = +params['id']; // (+) converts string 'id' to a number

       // In a real app: dispatch action to load the details here.
    });
  }

  ngOnDestroy() {
    this.sub.unsubscribe();
  }
}

<a [routerLink]="['product-list']" [queryParams]="{ page: 99 }">Go to Page 99</a>
goToPage(pageNum) {
    this.router.navigate(['/product-list'], { queryParams: { page: pageNum } });
}

import { Component } from '@angular/core';
import { ActivatedRoute, Router } from '@angular/router';

@Component({
  selector: 'product-list',
  template: `<!-- Show product list -->`
})
export default class ProductList {
  constructor(
    private route: ActivatedRoute,
    private router: Router) {}

  ngOnInit() {
    this.sub = this.route
      .queryParams
      .subscribe(params => {
        // Defaults to 0 if no query param provided.
        this.page = +params['page'] || 0;
      });
  }

  ngOnDestroy() {
    this.sub.unsubscribe();
  }

  nextPage() {
    this.router.navigate(['product-list'], { queryParams: { page: this.page + 1 } });
  }
}
```
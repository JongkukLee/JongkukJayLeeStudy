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

---
layout: default
---
# Angular
---

>Angular is a framework for building client applications in HTML and either JavaScript or a language like TypeScript that compiles to JavaScript.[https://angular.io](https://angular.io/guide/architecture#architecture-overview)

A component **controls a patch of screen called a view**. As code, a component is a class, with a decorator. The class is JavaScript, specifically TypeScript. It includes all the code needed for the the component’s behaviour during its lifetime.

A decorator is a function that modifies a class. It has one parameter, which is an object composed of configuration information as key-value pairs. This object is metadata, and the Angular runtime uses the metadata when initializing the component.

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


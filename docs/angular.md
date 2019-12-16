# Angular

- Angular is a framework for building client applications in HTML.
- The framework consists of several libraries.
- The angular application is written by composing HTML templates with angularized markup, writing component classes to manage those templates, adding applications logic in services, and boxing components & services in modules.
- Angular apps are modular and Angular has its own modularity system called NgModules eg: AppModule: which is the root module, @NgModule decorator.
- Decorators are functions that modify Javascript classes. eg: @Input, @Output
- Angular has many decorators that attach metadata to classes.

![angular_overview](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/angular_overview.png)

## Modules

NgModules are containers for a cohesive block of code dedicated to an application domain, a workflow, or a closely related set of capabilities. They can contain components, service providers, and other code files whose scope is defined by the containing NgModule. They can import functionality that is exported from other NgModules, and export selected functionality for use by other NgModules.

### NgModule metadata

NgModule is a decorator function that takes a single metadata object whose properties describe the module, such as

- declarations: the view classes that belong to this module. Angular has three kinds of view classes - components, directives and pipes.
- exports: the subset of declarations that should be visible & usable in the component templates of other modules.
- imports: other modules whose exported classes are needed by component templates declared in this module.
- providers: creators of service that this module contributes to the global collection of services; they become accessible in all parts of the app.
- bootstrap: The main application view, called the root component, which hosts all other app views. Only the root NgModule should set the bootstrap property.

### NgModules and components

NgModules provide a compilation context for their components. A root NgModule always has a root component that is created during bootstrap, but any NgModule can include any number of additional components, which can be loaded through the router or created through the template. The components that belong to an NgModule share a compilation context.

![compilation-context](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/compilation-context.png)

A component and its template together define a view. A component can contain a view hierarchy, which allows you to define arbitrarily complex areas of the screen that can be created, modified, and destroyed as a unit. A view hierarchy can mix views defined in components that belong to different NgModules. This is often the case, especially for UI libraries.

![view-hierarchy](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/view-hierarchy.png)

When you create a component, it's associated directly with a single view, called the host view. The host view can be the root of a view hierarchy, which can contain embedded views, which are in turn the host views of other components. Those components can be in the same NgModule, or can be imported from other NgModules. Views in the tree can be nested to any depth.

Views are typically arranged hierarchically, allowing you to modify or show and hide entire UI sections or pages as a unit. The template immediately associated with a component defines that component's host view. The component can also define a view hierarchy, which contains embedded views, hosted by other components.

![component-tree](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/component-tree.png)

A view hierarchy can include views from components in the same NgModule.

## Architecture overview

- Angular ships with a collection of js modules, you can think of them as library modules. eg:import Angular's Component decorator from the @angular/core library using `import { Component } from '@angular/core';`.
- Component: A component controls a patch of screen called a view. You define a components application logic; what it does to support the view inside a class. The class interacts with the view through an API of properties and methods.
- Templates: You define a components view with its companion template, A template is a form of HTML that tells Angualr how to render the component.
- Metadata tells Angular how to process a class. In Typescript, you attach metadata by using a decorator.
- Service is a class that performs a specific task eg: fetching data from backend or logging service.
- Angular uses dependency injection to provide new components with the services they need, such as the router service that lets you define navigation among views.

![library-module](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/library-module.png)

## Data Binding

A mechanism for coordinating parts of a template with parts of a component.

The following diagram shows the four forms of data binding markup. Each form has a direction: to the DOM, from the DOM, or both.

![databinding](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/databinding.png)

Data binding between a template and its component:

![component-databinding](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/component-databinding.png)

Data binding between parent and child coponents:

![parent-child-binding](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/parent-child-binding.png)

```html
<li>{{hero.name}}</li>
<app-hero-detail [hero]="selectedHero"></app-hero-detail>
<li (click)="selectHero(hero)"></li>
```

- The {{hero.name}} interpolation displays the component's hero.name property value.
- The [hero] property binding passes the value of selectedHero from the parent HeroListComponent to the hero property of the child HeroDetailComponent.
- The (click) event binding calls the component's selectHero method when the user clicks a hero's name.

## Pipes

Angular pipes let you declare display-value transformations in your template HTML. A class with the @Pipe decorator defines a function that transforms input values to output values for display in a view.
eg: `{{interpolated_value | pipe_name}}...<p>Today is {{today | date}}</p>`

## Directives

Angular templates are dynamic, when Angular renders them, it transforms the DOM according to the instructions given by directives.

A component is a directive-with-a-template.

- Structural directive alter layout by adding, removing and replacing elements of DOM. eg: `*ngFor, *ngIf`
- Attribute directive alter the appearance or behavior of an existing element. eg: `[(ngModel)]`
- custom directive eg: `HeroListComponent`

## Routing

The Angular router enables navigation from one view to the next as users perfrom application tasks.

## Forms

- Template-Driven: Angular infers the form object from the DOM
- Reactive: Form is created programmatically & synchronized withe the DOM

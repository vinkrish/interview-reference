- Angular is a framework for building client applications in HTML.
- The framework consists of several libraries.
- The angular application is written by composing HTML templates with angularized markup, writing component classes to manage those templates, adding applications logic in services, and boxing components & services in modules.
- Angular apps are modular and Angular has its own modularity system called NgModules eg: AppModule: which is the root module, @NgModule decorator.
- Decorators are functions that modify Javascript classes.
- Angular has many decorators that attach metadata to classes.

## Architecture overview

- Angular ships with a collection of js modules eg:import Angular's component decorator from the @angular/core library.
- Component: A component controls a patch of screen called a view. You define a components application logic; what it does to support the view inside a class. The class interacts with the view through an API of properties and methods.
- Templates: You define a components view with its companion template, A template is a form of HTML that tells Angualr how to render the component.
- Metadata tells Angular how to process a class. In Typescript, you attach metadata by using a decorator.
- Service is a class that performs a specific task eg: fetching data from backend or logging service.
- Angular uses dependency injection to provide new components with the services they need, such as the router service that lets you define navigation among views.

## Data Binding

A mechanism for coordinating parts of a template with parts of a component.

Binding markup connects your application data and the DOM. There are two types of data binding:

- Event binding lets your app respond to user input in the target environment by updating your application data.
- Property binding lets you interpolate values that are computed from your application data into the HTML.

Add binding markup to the template HTML to tell Angular how to connect both sides.
eg: `<app-hero-detail [hero]="selectedHero"> </app-hero-detail>`

The [hero] property binding passsess the value of selectedHero from the parent Herolist component to the hero property of the child HeroDetailComponent.

## Directives

Angular templates are dynamic, when Angular renders them, it transforms the DOM according to the instructions given by directives.

A component is a directive-with-a-template.

- Structural directive alter layout by adding, removing and replacing elements of DOM. eg: `*ngFor, *ngIf`
- Attribute directive alter the appearance or behavior of an existing element. eg: `[(ngModel)]`
- custom directive eg: `HeroListComponent`

## Routing

The Angular router enables navigation from one view to the next as userss perfrom application tasks.

## Forms

- Template-Driven: Angular infers the form object from the DOM
- Reactive: Form is created programmatically & synchronized withe the DOM

## Modules

NgModule is a decorator function that takes a single metadata object whose properties describe the module.

- declarations: the view classes that belong to this module. Angular has three kinds of view classes - components, directives and pipes
- exports: the subset of declarations that should be visible & usable in the component templates of other modules
- imports: other modules whose exported classes are needed by component templates declared in this module
- providers: creators of service that this module contributes to the global collection of services; they become accessible in all parts of the app

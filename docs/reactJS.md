## How Virtual-DOM works in React

React creates a virtual DOM. When state changes in a component it firstly runs a “diffing” algorithm, which identifies what has changed in the virtual DOM. The second step is reconciliation, where it updates the DOM with the results of diff.

The HTML DOM is always tree-structured — which is allowed by the structure of HTML document. The DOM trees are huge nowadays because of large apps. Since we are more and more pushed towards dynamic web apps (Single Page Applications — SPAs), we need to modify the DOM tree incessantly and a lot. And this is a real performance and development pain.
The Virtual DOM is an abstraction of the HTML DOM. It is lightweight and detached from the browser-specific implementation details. It is not invented by React but it uses it and provides it for free. ReactElements lives in the virtual DOM. They make the basic nodes here. Once we defined the elements, ReactElements can be render into the "real" DOM.

## How React Works

Whenever a ReactComponent is changing the state, diff algorithm in React runs and identifies what has changed. And then it updates the DOM with the results of diff. The point is - it’s done faster than it would be in the regular DOM.

- For a component to access a state of it's parent component, the parent needs to pass the state into the child component as a property.
- A component can only access it's own functions, props and states.
- Pass reference of function to another component as property, another component can use that reference with `this.props.reference_name`.
- In function component we can directly use `props.property_name`.
- Property value can be sent to component (without having any reference in component it is being used).
- You can pass value to reference function.
- Avoid function wrapper method or bind method as it creates new button for evvery render.]
- Use function component if it isn't top level or it's state need to be managed & no personalized event handler.

`Model + Component = DOM`

For any state change, React will regenerate the entire document object model, to avoid this problem React updates virtual DOM; which is fast.

Four ways to create component:

- ES5 createClass
- ES6 class
- ES5 stateless function
- ES6 stateless function

All properties of object is available as props in compnent.

## JSX

JSX is a syntax extension to JavaScript and comes with the full power of JavaScript. JSX produces React “elements”. You can embed any JavaScript expression in JSX by wrapping it in curly braces. After compilation, JSX expressions become regular JavaScript objects. This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions. Eventhough React does not require JSX, it is the recommended way of describing our UI in React app.

## Redux

Redux enforces keeping all state in a single centralized object graph.

A callback function can be invoked when setState has finished and the component is re-rendered. Since the setState is asynchronous, which is why it takes in a second callback function. With this function, we can do what we want immediately after state has been updated.

- React: Someone clicked this 'Save' button.
- Action: Actions are payloads of information that send data from our application to our store. They are the only source of information for the store. We send them to the store using store.dispatch(). Primarly, they are just an object describes what happened in our app.
- Reducer: Reducers specify how the application’s state changes in response to actions sent to the store. Remember that actions only describe what happened, but don’t describe how the application’s state changes. So this place determines how state will change to an action.
- Store: The Store is the object that brings Action and Reducer together. The store has the following responsibilities: Holds application state; Allows access to state via getState(); Allows state to be updated via dispatch(action); Registers listeners via subscribe(listener); Handles unregistering of listeners via the function returned by subscribe(listener).
- React-Redux: Woah, thanks for the new data Mr.Store. I'll now intelligently determine if I should tell React about this change so that it only has to bother with updating the UI when necessary.
- React: Ooh! shiny new data has been passed down via props from the store! I'll update the UI to reflect this.

Reducers are functions that take the current state in an action and then return a new state.

setState() actions are asynchronous and are batched for performance gains. This is explained in documentation as below.

setState() does not immediately mutate this.state but creates a pending state transition. Accessing this.state after calling this method can potentially return the existing value. There is no guarantee of synchronous operation of calls to setState and calls may be batched for performance gains.

This is because setState alters the state and causes rerendering. This can be an expensive operation and making it synchronous might leave the browser unresponsive. Thus the setState calls are asynchronous as well as batched for better UI experience and performance.

Containers are components containing the necessary logic for marshalling data and actions (via props)

Redux store is immutable.

![react_redux_store](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/react_redux_store.png)

The provider component attaches your application to the redux store so you use the provider component to wrap your application's top-level component.

The connect wraps our component so it's connected to the redux store.

children is passes down from react router `{ this.props.children }`

## Questions

1. **What are controlled and uncontrolled components in React?**

    This relates to stateful DOM components (form elements) and the difference:

    In HTML, form elements such as `<input>`, `<textarea>`, and `<select>` typically maintain their own state and update it based on user input. When a user submits a form the values from the aforementioned elements are sent with the form. With React it works differently. The component containing the form will keep track of the value of the input in it's state and will re-render the component each time the callback function e.g. onChange is fired as the state will be updated. A form element whose value is controlled by React in this way is called a "controlled component".

    With a controlled component, every state mutation will have an associated handler function. This makes it straightforward to modify or validate user input.

    A Controlled Component is one that takes its current value through props and notifies changes through callbacks like onChange. A parent component “controls” it by handling the callback and managing its own state and passing the new values as props to the controlled component. You could also call this a “dumb component”.

    A Uncontrolled Component is one that stores its own state internally, and you query the DOM using a ref to find its current value when you need it. This is a bit more like traditional HTML.
    In most (or all) cases we should use controlled components.

2. **What is render() in React? And explain its purpose?**

    Each React component must have a render() mandatorily. It returns a single React element which is the representation of the native DOM component. If more than one HTML element needs to be rendered, then they must be grouped together inside one enclosing tag such as `<form>`, `<group>`, `<div>` etc. This function must be kept pure i.e., it must return the same result each time it is invoked.

3. **What is React.cloneElement? And the difference with this.props.children?**

    React.cloneElement clone and return a new React element using using the passed element as the starting point. The resulting element will have the original element's props with the new props merged in shallowly. New children will replace existing children. key and ref from the original element will be preserved.

    React.cloneElement only works if our child is a single React element. For almost everything {this.props.children} is the better solution. Cloning is useful in some more advanced scenarios, where a parent send in an element and the child component needs to change some props on that element or add things like ref for accessing the actual DOM element.

4. **How Virtual-DOM is more efficient than Dirty checking?**

    In React, each of our components have a state. This state is like an observable. Essentially, React knows when to re-render the scene because it is able to observe when this data changes. Dirty checking is slower than observables because we must poll the data at a regular interval and check all of the values in the data structure recursively. By comparison, setting a value on the state will signal to a listener that some state has changed, so React can simply listen for change events on the state and queue up re-rendering.

    The virtual DOM is used for efficient re-rendering of the DOM. This isn’t really related to dirty checking your data. We could re-render using a virtual DOM with or without dirty checking. In fact, the diff algorithm is a dirty checker itself.

    We aim to re-render the virtual tree only when the state changes. So using an observable to check if the state has changed is an efficient way to prevent unnecessary re-renders, which would cause lots of unnecessary tree diffs. If nothing has changed, we do nothing.

5. **What is PureComponent? When to use PureComponent over Component?**

    PureComponent is exactly the same as Component except that it handles the shouldComponentUpdate method for us. When props or state changes, PureComponent will do a shallow comparison on both props and state. Component on the other hand won't compare current props and state to next out of the box. Thus, the component will re-render by default whenever shouldComponentUpdate is called.

    When comparing previous props and state to next, a shallow comparison will check that primitives have the same value (eg, 1 equals 1 or that true equals true) and that the references are the same between more complex javascript values like objects and arrays.

    It is good to prefer PureComponent over Component whenever we never mutate our objects.

6. **What is Redux Thunk used for?**

    Redux thunk is middleware that allows us to write action creators that return a function instead of an action. The thunk can then be used to delay the dispatch of an action if a certain condition is met. This allows us to handle the asyncronous dispatching of actions. The inner function receives the store methods dispatch and getState as parameters.

7. **What is a higher order component?**

    A higher-order component (HOC) is an advanced technique in React for reusing component logic. HOCs are not part of the React API. They are a pattern that emerges from React’s compositional nature.

    A higher-order component is a function that takes a component and returns a new component.

    HOC’s allow you to reuse code, logic and bootstrap abstraction. HOCs are common in third-party React libraries. The most common is probably Redux’s connect function. Beyond simply sharing utility libraries and simple composition, HOCs are the best way to share behavior between React Components. If you find yourself writing a lot of code in different places that does the same thing, you may be able to refactor that code into a reusable HOC.

8. **What is the difference between state and props?**

    The state is a data structure that starts with a default value when a Component mounts. It may be mutated across time, mostly as a result of user events.

    Props (short for properties) are a Component’s configuration. Props are how components talk to each other. They are received from above component and immutable as far as the Component receiving them is concerned. A Component cannot change its props, but it is responsible for putting together the props of its child Components. Props do not have to just be data — callback functions may be passed in as props.

    There is also the case that we can have default props so that props are set even if a parent component doesn’t pass props down.

9. **What are the differences between a class component and functional component?**

    Class components allows us to use additional features such as local state and lifecycle hooks. Also, to enable our component to have direct access to our store and thus holds state.

    When our component just receives props and renders them to the page, this is a ‘stateless component’, for which a pure function can be used. These are also called dumb components or presentational components.
## What is React?

React is a JavaScript library developed by Facebook for building user interfaces, especially single-page applications. It is component-based, allows the development of reusable UI components, and helps in creating dynamic web apps with great performance.


## What are the key features of React?

- Virtual DOM: Optimizes updates by re-rendering only what’s necessary.
- Component-based architecture: Breaks UI into reusable pieces.
- One-way data binding: Data flows in one direction (from parent to child components).
- JSX: A syntax extension that allows writing HTML in JavaScript.
- Declarative UI: Developers describe what UI should look like.

## What is JSX?

JSX stands for JavaScript XML. It allows writing HTML-like syntax in JavaScript code. Browsers don’t understand JSX directly, so it’s compiled into regular JavaScript using tools like Babel.

You can embed any JavaScript expression in JSX by wrapping it in curly braces. After compilation, JSX expressions become regular JavaScript objects. This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions

## What are components in React?

Components are the building blocks of a React application. They allow splitting the UI into independent, reusable pieces. There are two types:

- Class Components: ES6 classes that extend React.Component and use lifecycle methods.
- Functional Components: JavaScript functions that return JSX and use hooks for managing state and lifecycle.

## What is the Virtual DOM? How does it work?

The Virtual DOM is a lightweight in-memory representation of the actual DOM. React updates the Virtual DOM first, calculates the differences (diffing), and then updates the real DOM only where necessary. This minimizes direct DOM manipulations, improving performance.

## What are props in React?

Props (short for properties) are read-only attributes passed from a parent component to a child component. They allow passing data and methods between components.

## What is state in React?

State is a built-in React object used to store data or information about the component. Unlike props, state is mutable and managed within the component. When state changes, React re-renders the component.

## What is the difference between state and props?

- Props are passed from parent to child components, are immutable, and allow sharing data across components.
- State is local to the component, mutable, and used to manage internal data that can change over time.

## What are hooks in React?

Hooks are special functions that allow using state and other React features in functional components. The most commonly used hooks are:

- useState for state management.
- useEffect for managing side effects like API calls, timers, etc.
- useContext for accessing React context.
- useMemo and useCallback for optimizing performance.

## Lifecycle Methods in Functional Components

Hooks are now the preferred way of working with React lifecycle in functional components.

```js
import { useEffect } from 'react';

function MyComponent() {
  useEffect(() => {
    // componentDidMount & componentDidUpdate logic
    return () => {
      // componentWillUnmount logic
    };
  }, []); // The second argument controls when the effect runs
}
```

## What is the purpose of useEffect in React?

 `useEffect` is a hook used to perform side effects in functional components, like fetching data, updating the DOM, or setting up subscriptions. It runs after the render cycle and can optionally clean up after itself by returning a function.

## How do you handle events in React?

Handling events in React is similar to handling events in plain JavaScript, but with a few key differences:

- **Naming Convention**: React uses camelCase naming for event handlers instead of lowercase. For example, onclick in HTML becomes onClick in React.
- **Passing Functions as Props**: Instead of passing a string representing the event handler, you pass the actual function as a prop to the element.
- **Synthetic Events**: React wraps native browser events in its own synthetic event system to ensure cross-browser compatibility.

## What is the purpose of keys in React?

Keys help React identify which items in a list have changed, are added, or are removed. This improves the efficiency of updating the DOM and is crucial when rendering lists of components.

## What are higher-order components (HOC) in React?

A HOC is a pattern in which a function takes a component and returns a new component with added functionality. It's a way to reuse component logic. For example, adding authentication checks to multiple components.

HOC are the best way to share behavior between React Components. If you find yourself writing a lot of code in different places that does the same thing, you may be able to refactor that code into a reusable HOC. eg: Redux’s connect function

## What is the Context API in React?

The Context API allows for sharing state and functions across multiple components without passing props down manually at every level. It is particularly useful for managing global state like themes, user sessions, etc.

## What is lazy loading in React?

Lazy loading in React is a way to defer loading components until they are needed, improving the initial load time. React provides React.lazy() and Suspense for implementing lazy loading.

## What are React portals?

React portals provide a way to render components outside the main DOM hierarchy. They are useful for rendering modals, tooltips, or popups that require being placed at the root level of the DOM.

## What is the difference between controlled and uncontrolled components?

- Controlled components are those whose form data is handled by the React component state. Input elements like `<input>`, `<textarea>`, and `<select>` are controlled by the component's state using the onChange event handler.
- Uncontrolled components use refs to directly access the DOM element’s values.

## What is the useReducer hook?

`useReducer` is an alternative to useState when managing more complex state logic. It accepts a reducer function (state, action) and an initial state and returns the current state paired with a dispatch method to trigger state updates.

## What is memoization in React?

Memoization is an optimization technique used to speed up rendering by caching results. React provides React.memo and hooks like useMemo and useCallback to avoid unnecessary re-renders and expensive computations.

## What is the difference between useMemo and useCallback?

- useMemo: Returns a memoized value, used to optimize expensive computations.
- useCallback: Returns a memoized function reference, useful when passing functions as props to child components to prevent re-renders.

## How can you improve the performance of a React app?

- Use React's memoization (React.memo, useMemo, useCallback).
- Use Code Splitting and Lazy Loading.
- Avoid anonymous functions in render.
- Implement shouldComponentUpdate or use PureComponent.
- Optimize re-rendering by managing state efficiently.
- Use React Profiler to identify performance bottlenecks.

## What is Redux, and how does it relate to React?

Redux is a state management library that can be used with React (or other frameworks). It provides a central store for managing application state and follows a unidirectional data flow. In React, it's typically used with the react-redux library for binding the store with React components.

## What is the difference between Redux and Context API?

Both Redux and the Context API solve similar problems: sharing state across components. However:

- Redux is more powerful for complex state management, providing middlewares, actions, reducers, and a strict structure.
- Context API is simpler and suitable for smaller apps with less complex state needs.

## What is React Router?

React Router is a popular routing library for React. It allows for dynamic routing, enabling navigation between different views or components in a single-page application without refreshing the page.

## What are render props?

Render props is a technique for sharing code between React components using a prop whose value is a function. It allows for more dynamic and reusable components.

## How do you handle forms in React?

In React, forms can be handled using:

- Controlled components, where form elements are bound to the state and update via onChange handlers.
- Uncontrolled components, using refs to access form values directly from the DOM.

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

## A Chat with Redux

- React: Someone clicked this 'Save' button.
- Action: Thanks React! I will dipatch an action so reducers that care can update state.
- Reducer: Ah, thanks action. I see you passed me the current state and the action to perform. I'll make a new copy of the state and return it.
- Store: Thanks for updating the state reducer, I'll make sure that all connected components are aware.
- React-Redux: Woah, thanks for the new data Mr.Store. I'll now intelligently determine if I should tell React about this change so that it only has to bother with updating the UI when necessary.
- React: Ooh! shiny new data has been passed down via props from the store! I'll update the UI to reflect this.

## How React Works

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
- Es6 class
- ES5 stateless function
- ES6 stateless function

All properties of object is available as props in compnent.

## Redux

Redux enforces keeping all state in a single centralized object graph.

Reducers are functions that take the current state in an action and then return a new state.

Containers are components containing the necessary logic for marshalling data and actions (via props)

Redux store is immutable.

![react_redux_store](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/react_redux_store.png)

The provider component attaches your application to the redux store so you use the provider component to wrap your application's top-level component.

The connect wraps our component so it's connected to the redux store.

children is passes down from react router `{ this.props.children }`

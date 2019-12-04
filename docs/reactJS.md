## A Chat with Redux

- React: Someone clicked this 'Save' button.
- Action: Thanks React! I will dipatch an action so reducers that care can update state.
- Reducer: Ah, thanks action. I see you passed me the current state and the action to perform. I'll make a new copy of the state and return it.
- Store: Thanks for updating the state reducer, I'll make sure that all connected components are aware.
- React-Redux: Woah, thanks for the new data Mr.Store. I'll now intelligently determine if I should tell React about this change so that it only has to bother with updating the UI when necessary.
- React: Ooh! shiny new data has been passed down via props from the store! I'll update the UI to reflect this.

## React-Redux

The provider component attaches your application to the redux store so you use the provider component to wrap your application's top-level component.

The connect wraps our component so it's connected to the redux store.
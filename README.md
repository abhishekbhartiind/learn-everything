# learn-everything

###### Redux helps you make applications that behave consistently, run in different environments (client, server, and native), and are easy to test.

Q: createStore(reducer, preloadedState, enhancer) refers to
A: It creates a redux store that holds complete state tree of an application.

  Reducer: A reducer function accept collections and a value and return new collections, used to reduce a collection of                  values down to a single value.
  initialState/preloadedState: Pre initialise state value, hydrate the state from the server in universal apps
  enhancer: enhance the store with third-party capabilities such as middleware

Q: What is Dispatch?
A: Dispatch is an action, it's the only way to trigger state change in redux. Internally store reducing function will be called    with getState() result and given action synchronously, return value will be considered the next state. It will be returned      from getState() and the change listeners will immediately be notified.

Note: 
  - Don't call dispatch inside reducers, it will throw you error.
  - In Redux, Subscription is called after root reducer changes/return new state, you may dispatch in subscription listener
    You are only disallowed to dispatch inside the reducers because they must have no side effects. If you want to cause a side     effect in response to an action, the right place to do this is in the potentially async action creator.
-----------------------------------------------------------------------------------------------------------------------------

Q: What is an Action?
A: object that describe change in state, only way to pass data to store so any data, UI events, network callbacks needs to        eventually be dispatched as actions. 
   Actions must have a type field that indicates the type of action being performed.
   
   ```
    import { createStore } from 'redux'
    const store = createStore(todos, ['Use Redux'])

    function addTodo(text) {
      return {
        type: 'ADD_TODO',
        text
      }
    }

    store.dispatch(addTodo('Read the docs'))
    store.dispatch(addTodo('Read about the middleware'))
  
   ```
   
   --------------------------------------------------------------------------------------------------------------------------
   

---
layout: post
title: 'Notes-useReducer'
date: 2023-01-08 10:49:33 +0800
categories: Notes
---

# useReducer

## `useReducer(reducer, initialArg, init?)`

### Parameters

- `reducer`: The reducer function that specifies how the state gets updated, should take the state and action as arguments, and should return the next state.
- `initialArg`: The value from which the initial state is calculated. It can be a value of any type.

- optional `init`: If it’s not specified, the initial state is set to initialArg.

### Returns

useReducer returns an array with exactly two values:

- The current state. During the first render, it’s set to init(initialArg) or initialArg (if there’s no init).

- The dispatch function that lets you update the state to a different value and trigger a re-render.

## `dispatch` function

### Parameters

- `action`: The action performed by the user. It can be a value of any type. By convention, an action is usually an object with a type property identifying it and, optionally, other properties with additional information.

### Returns

- dispatch functions do not have a return value.

## Example

`npx create-react-app my-app`

```js
import { useReducer } from 'react';

function App() {
  function reducer(state, action) {
    if (action.type === 'incremented_age') {
      return {
        age: state.age + 1,
      };
    }
    throw Error('Unknown action.');
  }

  const [state, dispatch] = useReducer(reducer, { age: 42 });

  return (
    <>
      <button
        onClick={() => {
          dispatch({ type: 'incremented_age' });
        }}
      >
        Increment age
      </button>
      <p>Hello! You are {state.age}.</p>
    </>
  );
}

export default App;
```

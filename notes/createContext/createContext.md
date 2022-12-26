# createContext

## context

Context is designed to share data that can be considered “global” for a tree of React components, such as the current authenticated user, theme, or preferred language.

Context provides a way to pass data through the component tree without having to pass props down manually at every level.

Context is primarily used when some data needs to be accessible by many components at different nesting levels. If you only want to avoid passing some props through many levels, **component composition** is often a simpler solution than context.

## React.createContext

```js
const MyContext = React.createContext(defaultValue);
```

Creates a Context object. When React renders a component that subscribes to this Context object it will read the current context value from the closest matching Provider above it in the tree.

## Context.Provider

```js
<MyContext.Provider value={/* some value */}>
```

Every Context object comes with a Provider React component that allows consuming components to subscribe to context changes.

## useContext

```js
const value = useContext(MyContext);
```

Accepts a context object (the value returned from React.createContext) and returns the current context value for that context. The current context value is determined by the value prop of the nearest <MyContext.Provider> above the calling component in the tree.

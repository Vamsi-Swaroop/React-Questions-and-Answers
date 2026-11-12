# React  Questions and Answers

## 1. What are the advantages of JSX?

JSX lets us write UI in a way that looks similar to HTML, inside JavaScript.

- It keeps the UI and its related logic together.
- It is easier to read than writing many React.createElement() calls.
- We can write JavaScript expressions inside {}.
- Tools like Babel convert JSX into JavaScript that the browser can use.
- React escapes values by default, which helps protect against XSS attacks.

JSX is optional, but most React projects use it.

## 2. Virtual DOM vs Real DOM

- **Real DOM:** The actual page structure that the browser displays.
- **Virtual DOM:** A JavaScript description of what the UI should look like. React uses it to work out what needs to change.

When state or props change, React creates a new description of the UI and compares it with the previous one. It then updates the necessary parts of the real DOM.

## 3. What is a bundler? Explain Webpack.

A bundler collects the files used by our app, such as JavaScript, CSS and images, and prepares them for the browser.

**Webpack** is a popular bundler. Its main parts are:

- **Entry:** The file where Webpack starts.
- **Output:** The folder and file where the final bundle is saved.
- **Loaders:** Help Webpack understand files such as CSS and JSX.
- **Plugins:** Add extra tasks, such as creating an HTML file or reducing file size.
- **Dev server:** Runs the app locally while we work on it.

Webpack follows the files our app imports and puts the required code into bundles.

## 4. How does Vite work?

Vite is a tool used to run and build modern frontend projects.

It has two main modes:

- **Development:** Starts a development server quickly. It serves source files when the browser requests them and updates changed files without refreshing the whole page.
- **Production build:** Combines and optimizes the files so they are ready to deploy.

In simple terms, Vite avoids bundling all our source code before starting the development server. This helps it start quickly.

## 5. What is Babel?

Babel is a JavaScript tool that converts newer JavaScript features and JSX into code that browsers can understand.

It converts JSX into JavaScript function calls and can convert newer JavaScript features into older syntax when needed.

## 6. What is a React element?

A React element is a JavaScript object that describes what we want to show on the screen.

For example, it describes:
- Which element or component to display.
- Its props.
- Its children.

A React element is not the same as a real HTML element in the browser. A component is a function or class that returns React elements.

## 7. When does a React component re-render?

A component can re-render when:

1. Its state changes.
2. Its parent component re-renders.
3. Its props change.
4. A context value it uses changes.
5. A class component calls forceUpdate().

Changing a useRef value or a normal variable does not cause a re-render.

In development, StrictMode may render components more than once to help find problems.

## 8. When should we use a function component or a class component?

- **Function components:** The normal choice for new React code. They are simpler and can use Hooks.
- **Class components:** Mostly found in older projects. They are also still used to create error boundaries.

## 9. Function component vs class component

A **function component** is a JavaScript function that returns JSX. It uses Hooks such as useState and useEffect.

A **class component** is a JavaScript class that extends React.Component. It uses this.state, this.setState() and lifecycle methods such as componentDidMount().

Function components usually need less code and are the recommended choice for new projects.

## 10. Why should a component name start with a capital letter?

JSX uses the first letter to tell the difference between HTML tags and React components.

So, component names should start with a capital letter.

## 11. Why do we need ReactDOM?

react provides the main React features, such as components, elements and Hooks.

react-dom connects React to the browser's DOM. We use createRoot() from react-dom/client to choose where our React app should appear, and then call root.render().

React Native uses a different renderer to display React apps on mobile devices.

## 12. State vs props

- **Props:** Data passed from a parent component to a child component. The child should not change its props.
- **State:** Data managed inside a component. We update it using a state setter, such as the function returned by useState().

When state or props change, React may re-render the component.

A child can ask its parent to do something by calling a function that the parent passes as a prop.

## 13. JSX vs HTML

JSX looks like HTML, but there are some differences:

- Use className instead of class.
- Use htmlFor instead of for.
- Most attribute names use camelCase, such as onClick.
- Use a JavaScript object for the style prop.
- Close every tag, including tags such as img and br.
- Put JavaScript expressions inside {}.
- Put JSX comments inside {/* ... */}.
- Pass a function to an event handler, not a string.
- A component should return one parent element. We can use a Fragment if we do not want an extra HTML element.

## 14. What are PropTypes?

PropTypes can check whether a component receives props of the expected type.

For example, we can expect title to be a string and count to be a number. If a prop has the wrong type, React gives a warning in the development console.

Many modern projects use TypeScript for type checking instead.

## 15. What are the different ways to update state?

With useState, we can update state in two common ways:

- **Give a new value:** setCount(5)
- **Use the previous value:** setCount(previous => previous + 1)

For objects and arrays, we should create a new object or array instead of changing the old one.

- Add to an array with spread: [...items, newItem]
- Remove from an array with filter().
- Update an item with map().
- Copy an object with spread: { ...user, name: "Sam" }

In class components, this.setState() can merge an object into the current state.

## 16. Why do people say useState is asynchronous?

Calling a state setter does not change the state variable immediately. React schedules the update and then renders the component again.

For example, if we call the state setter three times using the current count value, the count may increase only once because each call uses the same value. If we use the previous-state function form for each update, every update receives the latest value, so the count increases three times.

## 17. Why should we not change state directly?

We should not change an existing state object or array directly.

For example, avoid changing an object property directly or using push() on a state array.

Instead, create a new object or array and pass it to the state setter. This helps React detect the change and keeps our code predictable.

## 18. How do we validate a form in React?

A simple way is to use controlled inputs and an errors state.

1. Store the input values in state.
2. Write a function that checks the values.
3. When the form is submitted, prevent the page from refreshing.
4. Run the validation function and save any errors in state.
5. Show the error message near the related input.
6. Submit the form only when there are no errors.

We can validate when the user types, when they leave a field, or when they submit the form. For large forms, libraries such as React Hook Form can help.

## 19. What is the Virtual DOM and how does it work?

The Virtual DOM is React's JavaScript description of the UI.

A simplified process:

1. **Render:** React creates a description of the UI.
2. **Compare:** When something changes, React compares the new description with the previous one.
3. **Update:** React applies the required changes to the real DOM.

React uses keys to identify items in lists and work out which items have changed.

## 20. Controlled vs uncontrolled components

- **Controlled input:** React state stores the input value. We use value and onChange to keep the input and state in sync.
- **Uncontrolled input:** The browser stores the input value. We can read it using a ref when needed.

Controlled inputs are useful when we need validation or need to respond to every change. Uncontrolled inputs can be simpler for some cases, such as file inputs.

## 21. Why do we use the key prop in lists?

A key helps React identify each item in a list.

It helps React understand which items were added, removed or changed when the list updates.

- Use a stable, unique value such as an item's ID.
- Avoid using the array index if items can be added, removed or reordered.
- key is used by React and is not passed to the component as a normal prop.

## 22. What are lifecycle methods?

Lifecycle methods are special methods used in class components at different stages of a component's life.

**Mounting — when the component is added to the page**
- constructor(): Sets up the initial state.
- render(): Returns the UI.
- componentDidMount(): Runs after the component appears on the page. It can be used for fetching data or starting a timer.

**Updating — when props or state change**
- shouldComponentUpdate(): Decides whether the component should re-render.
- getSnapshotBeforeUpdate(): Reads information from the DOM just before an update.
- componentDidUpdate(): Runs after an update.

**Unmounting — when the component is removed**
- componentWillUnmount(): Used to clean up timers or event listeners.

Function components use Hooks such as useEffect to handle many similar tasks.

## 23. Why do we use Context, and how does it work?

Context lets us share data with many components without passing props through every level.

For example, we can share a theme, language or logged-in user.

Basic steps:

1. Create a context using createContext().
2. Wrap the components that need the data with its Provider.
3. Pass the shared value to the Provider.
4. Read the value in a child component using useContext().

When the context value changes, components that use it re-render.

## 24. What is React.Fragment used for?

A component should return one parent element.

A Fragment lets us group multiple elements without adding an extra HTML element to the page.

We can use the short Fragment syntax, which is an empty opening and closing tag around the elements. When we need to add a key, such as while rendering a list, we use the full React Fragment syntax with a key.

## 25. Can we use loops inside JSX?

Yes. We commonly use map() to display a list.

map() goes through an array and returns an element for each item. Each item should have a unique key.

We can also use filter() first if we only want to display some items.

## 26. What are the advantages of Hooks?

Hooks let function components use React features such as state and effects.

- We can use state without writing a class.
- We can reuse logic with custom Hooks.
- Related code can stay together.
- We do not need to deal with this.
- They often make components shorter and easier to understand.

## 27. What are the different types of Hooks?

Here are some commonly used built-in Hooks:

- **useState:** Stores state in a component.
- **useEffect:** Runs code after a render, often for tasks such as fetching data or setting up a timer.
- **useContext:** Reads a value from Context.
- **useRef:** Stores a value between renders or points to a DOM element.
- **useReducer:** Manages state using actions.
- **useMemo:** Remembers the result of a calculation.
- **useCallback:** Remembers a function between renders.
- **useLayoutEffect:** Runs an effect before the browser paints the screen.
- **useId:** Creates an ID that can be used for accessibility.
- **useTransition and useDeferredValue:** Help keep the UI responsive during updates.

A **custom Hook** is a function we create to reuse logic. Its name should start with use.

## 28. How do we use useEffect?

useEffect lets us run code after React has rendered the component. It is often used for tasks such as fetching data, setting up timers or adding event listeners.

It takes a function and an optional dependency array.

- **No dependency array:** Runs after every render.
- **Empty array []:** Runs after the first render. In development StrictMode, it may run an extra setup and cleanup cycle.
- **Array with values:** Runs after the first render and again when one of those values changes.

The effect can return a cleanup function. We use it to clear timers or remove event listeners.

The effect function itself should not be async. If we need async work, we can create and call an async function inside the effect.

## 29. How do we use useRef?

useRef gives us an object with a .current property. The same ref object stays available between renders.

Changing .current does not cause a re-render.

Common uses:

1. **Accessing an HTML element:** For example, focusing an input.
2. **Storing a value:** For example, an interval ID or a value we need to keep between renders.

## 30. What is the useContext Hook?

useContext lets a component read a value from the nearest matching Context Provider.

It helps us share data, such as a theme or logged-in user, without passing props through many components.

A component using that context re-renders when the context value it reads changes.

## 31. What is the useReducer Hook?

useReducer is another way to manage state. It is useful when state has several related updates.

It uses:

- **Reducer:** A function that receives the current state and an action, then returns the new state.
- **Dispatch:** A function we call to send an action to the reducer.

For example, a shopping cart might have actions such as add, remove and clear.

## 32. Which Hooks can help us manage state?

- **useState:** For simple state, such as a name or counter.
- **useReducer:** For state with several related actions.
- **useContext:** For sharing values between components.
- **useRef:** For values that should persist but should not cause a re-render when changed.
- **useSyncExternalStore:** For reading data from an external store.

Context can be combined with useState or useReducer to share state across components.

## 33. DOM element vs React element

- **DOM element:** A real element in the browser, such as a div. It is part of the page and can be changed directly.
- **React element:** A JavaScript object that describes what should appear on the page. It is not a real browser element.

React uses React elements to decide how to update the real DOM.

## 34. What happens if a runtime error occurs while rendering? How can we handle it?

A runtime error is an error that happens while the app is running. For example, we may try to read a property from a value that is undefined.

If an error happens while a component is rendering, an **Error Boundary** can show a fallback UI instead of letting that part of the app fail without a useful message.

We can also prevent common errors by:
- Checking that a value exists before using it.
- Using optional chaining, such as user?.name.
- Providing default values when needed.

Error Boundaries do not catch errors in event handlers or most asynchronous code. We handle those with suitable error handling, such as try/catch.

## 35. What are the Rules of Hooks?

1. Call Hooks at the top level of a function component or custom Hook.
2. Do not call Hooks inside conditions, loops or nested functions.
3. Call Hooks only from React function components or custom Hooks.
4. Custom Hook names should start with use.

React depends on Hooks being called in the same order on every render.

## 36. Can we call Hooks inside an if statement?

No. Hooks should not be called inside an if statement.

React depends on Hooks being called in the same order every time the component renders. If a Hook is skipped on one render, React can match state to the wrong Hook.

Instead, call the Hook at the top level and put the condition inside the Hook's callback when appropriate.

## 37. What are the advantages of React.StrictMode?

StrictMode helps us find problems while developing an app.

- It can render components an extra time in development to help find code that changes things during rendering.
- It runs an extra effect setup and cleanup cycle in development to help find missing cleanup.
- It helps identify some outdated React practices.

It does not add anything to the visible UI, and these extra development checks do not happen in production.

## 38. How do we create a production build?

For a Vite project, we use the build command from the terminal. It creates a dist folder containing the files ready to deploy. We can use the preview command to test the production build locally. For a Create React App project, the build command usually creates a build folder.

A production build reduces and optimizes the files so the app can load more efficiently.

## 39. Development mode vs production mode

**Development mode**
- Used while building the app.
- Gives helpful warnings and error messages.
- Supports fast updates while we edit files.
- Is easier to debug.

**Production mode**
- Used when the app is deployed.
- Code is optimized and usually smaller.
- Does not include development-only checks.
- Is prepared for users, rather than for debugging.

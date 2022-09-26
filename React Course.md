# Tutorial: Intro to React

[Learn by doing](https://reactjs.org/tutorial/tutorial.html): The note is based on this.

[step-by-step guide](https://reactjs.org/docs/hello-world.html): Learn concepts from the ground up.



## Before We Start the Tutorial

Build a small game.

*learn by doing*

Four parts:

- Setup for the Tutorial
- Overview
- Completing the Game
- Adding Time Travel



### What Are We Building?

Build an **interactive tic-tac-toe game**.

The Final Result is like [this](https://codepen.io/gaearon/pen/gWWZgR?editors=0010).



### Prerequisites

If you are familiar with **HTNL** and **JavaScript** may be better, but they are not necessary.

You should be familiar with basic programming concepts like functions, objects, arrays, and to a lesser extent, classes.

[An overview for JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Language_Overview)

**Remark:** We will use some features from **ES6** --- a recent version of JavaScript. Use [Babel REPL](https://babeljs.io/repl/#?presets=react&code_lz=MYewdgzgLgBApgGzgWzmWBeGAeAFgRgD4AJRBEAGhgHcQAnBAEwEJsB6AwgbgChRJY_KAEMAlmDh0YWRiGABXVOgB0AczhQAokiVQAQgE8AkowAUAcjogQUcwEpeAJTjDgUACIB5ALLK6aRklTRBQ0KCohMQk6Bx4gA) to check what **ES6** code compiles to.

For reference: [arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions), [classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes), [let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let), [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const)



## Setup for the Tutorial



### Setup Option 1: Write Code in the Browser

[Starter Code](https://codepen.io/gaearon/pen/oWWQNa?editors=0010): This tab diaplay an wmpty tic-tac-toe game board and React code.



### Setup Option 2: Local Development Environment

**Important!** 😊

Install `Node.js`

`Create React App`

delete the files in `/src` folder and replace them

use `npm starter` to open the browser

Configure syntax highlighting for editor



### Help, I'm Stuck!

If you get stuck, check out the [community support resources](https://reactjs.org/community/support.html).

Also, [Reactiflux Chat](https://discord.com/invite/reactiflux) is a great way to get help quidkly.

If remaining stuck, **file an issue**.



## Overview



### What Is React?

`React` is a declarative, efficient, and flexible JavaScript library for **building user interfaces**. It lets you compose complex UIs from small and isolated pieces of code called `components`.

Start from `React.Component` subclasses

We use components to tell React what we want to see on the screen. When data changes, React will efficiently update and re-render our components.

```react
class ShoppingList extends React.Component {
  render() {
    return (
      <div className="shopping-list">
        <h1>Shopping List for {this.props.name}</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
          <li>Oculus</li>
        </ul>
      </div>
    );
  }
}

// Example usage: <ShoppingList name="Mark" />
```

ShoppingList is a **React Component class**, or **React component type**. A component takes in parameters, called `props` (short for "properties").

The `render` method returns a *description* of what you want to see on the screen. React takes the decription adn displays the result.

In particular, `render` returns a **React element**, which is a lightweight description of what to render.

Use a special syntax called "JSX" which makes these structures easier to write, i.e. transform the `<div />` syntax to `React.createElement('div')`. The example above is equivalent to:

```react
return React.createElement('div', {calssName: 'shopping-list'},
	React.createElement('h1', /* ... h1 children ... */),
    React.createElement('ul', /* ... ul children ... */)
);
```

[The full expanded version](https://babeljs.io/repl/#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie_mob%2011&build=&builtIns=false&corejs=3.21&spec=false&loose=false&code_lz=DwEwlgbgBAxgNgQwM5IHIILYFMC8AiJACwHsAHUsAOwHMBaOMJAFzwD4AoKKYQgRlYDKJclWpQAMoyZQAZsQBOUAN6l5ZJADpKmLAF9gAej4cuwAK5wTXbg1YBJSswTV5mQ7c7XgtgOqEETEgAguTuYFamtgDyMBZmSGFWhhYchuAQrADc7EA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=react&prettier=false&targets=&version=7.19.2&externalPlugins=&assumptions=%7B%7D)

```react
/*#__PURE__*/
React.createElement("div", {
    calssName: "shopping-list"
}, /*#__PURE__*/React.createElement("ul", null,
/*#__PURE__*/React.createElement("li", null, "Instagram"),
/*#__PURE__*/React.createElement("li", null, "WhatsApp"),
/*#__PURE__*/React.createElement("li", null, "Oculus")));
```

What does the `/*#__PURE__*/` tag means?

[The pure function in JavaScript.](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976)

- A **pure function** is a function which given the same input, always returns the same output. It produces no side effects.
- `/*#__PURE__*/` is and indication that the function in question is pure, or be more precise, side-effect free. This helps with [tree-shaking](https://developer.mozilla.org/en-US/docs/Glossary/Tree_shaking) - the removal of dead code from bundles when nothing else references a particular value. reference: [What's the meaning of /\*#\__PURE\__\*/ in some JaveScript source code?](https://stackoverflow.com/questions/68187576/whats-the-meaning-of-pure-in-some-javascript-source-code)

More detail for `createElement()` in the [API reference](https://reactjs.org/docs/react-api.html#createelement).

JSX comes with the full power of JavaScript. Each React element is a JavaScript object that can be stored in a variable of pass around in program.

[JavaScript HTML DOM](https://www.w3schools.com/js/js_htmldom.asp)

[HTML \<div> tag](https://www.w3schools.com/tags/tag_div.ASP): The `<div>` tag defines a division or a section in an HTML document. It is used as a container for HTML elements - which is then styled with CSS or manipulated with JavaScript.

[HTML \<li> tag](https://www.w3schools.com/tags/tag_li.asp): The `<li>` tag is used inside ordered lists(`<ol>`), unordered lists(`<ul>`), and in menu lists(`<menu>`). 

We can compose and render custom React components. For example, we can now refer to the whole shopping list by writing `<ShoppingList />`. Each React component is encapsulated and can operate independently. 



### Inspecting the Starter Code

Inspect the `index.js` file

There are three React components: Squre, Board, Game.

The Squqre component renders a single `<button>` and the Board renders 9 squares. The Game component renders a board with placeholder values which we'll modify later. There are currently no interactive components.



### Passing Data Through Props

Try to pass some data from Board component to Square component.

Pass a *prop* from a parent Board component to a child Square component.



### Making an Interactive Component

Fill the Square component with an "X" when click it.

Use [devtools](https://developer.chrome.com/docs/devtools/open/) console to track the click.

[Arrow function expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions):

- An **arrow function expression** is a compact alternative to a traditional function expression, but is limited.
- Arrow functions don't have their bindings to `this`, `arguments` or `super`, and should not be used as `methods`.

Components use **state** to remember things.

React components can have state by setting `this.state` in their constructors. `this.state` should be considered as private to a React component that it's defined in. Store the current value of the Square in `this.state`, and change it when the Square is clicked.

Add a **Constructor** to the class to initialize the state.

**Remark:** In `JavaScript` classes, you need to always call `super` when defining the constructor of a subclass. All React component classes that have a `constructor` should start with a `super(props)` call.



### Developer Tools

[React Developer Tools for Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)

Inspect a React component tree with browser's tools (in `Component` tag).



## Completing the Game



### Lifting State Up

We need to maintain the value of each of the 9 squares in one location.

**Declare the shared state in their parent component**

The parent component can pass the state back down to the children by using **props**, and keep the child components **in  sync** with each other and with the parent component.

State is considered to be private to a component that defines it, we cannot update the Board's state directly from Square.

Instead, we will pass down a function from the Board to the Square, and we'll have Square call that function when a square is clicked.

**Remark:** `Props` stand for "Properties". They are read-only components. It is an object which stores the value of attributes of a tag and work similar to the HTML attributes. It gives a way to *pass data from one component to other components*. It is similar to *function arguments*.

In React, it's conventional to use `on[Event]` names for props which represent events and `handle[Event]` for the methods which handle the events.

In React terms, the Square components are now **controlled components**, as thry are under full control of the Board.

In `handleClick`, we call `.slice()` to create a copy of the `squares` array to modify instead of modifying the existing array.



### Why Immutability Is Important

Replace the data with a new copy which has the desired changes.

Benefits:

- Complex Features Become Simple
- Detecting Changes
- Determining When to Re-Render in React: help you build *pure components*

Learn more about `shouldComponentUpdate()` how to build *pure components* by reading [Optimizing Performance](https://reactjs.org/docs/optimizing-performance.html#examples).



### Function Components

Change the Square to be a **function component**.

In React, **function components** are a simpler way to write components that only contain a `render` method and don't have their own state. We can write a function that takes `props` as input and returrns what should be rendered.

Change `onClick={() => this.props.onClick()}` to a shorter `onClick={props.onClick}`.



### Taking Turns

Use a variable to store next step is which player.



### Declaring a Winner

Call `calculateWinner(squares)` in the Board's `render` function to check if a player is won.



## Adding Time Travel

Make it possible to "go back in time" to the previous moves in the game.



### Storing a History of Moves
























































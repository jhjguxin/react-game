# Tutorial: Intro To React

## Before We Start

### What We’re Building

Today, we’re going to build an interactive tic-tac-toe game.

If you like, you can check out the final result here: [Final Result](https://codepen.io/gaearon/pen/gWWZgR?editors=0010). Don’t worry
if the code doesn’t make sense to you yet, or if it uses an unfamiliar syntax.
We will be learning how to build this game step by step throughout this tutorial.

Try playing the game. You can also click on a button in the move list to go
“back in time” and see what the board looked like just after that move was made.

Once you get a little familiar with the game, feel free to close that tab, as
we’ll start from a simpler template in the next sections.

### Prerequisites

We’ll assume some familiarity with HTML and JavaScript, but you should be able
to follow along even if you haven’t used them before.


If you need a refresher on JavaScript, we recommend reading [this guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript).
Note that we’re also using some features from ES6, a recent version of JavaScript. In this tutorial, we’re using [arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions),
[classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes),
[let](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let),
and [const](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const) statements.
You can use the [Babel REPL](https://babeljs.io/repl/#?presets=react&code_lz=MYewdgzgLgBApgGzgWzmWBeGAeAFgRgD4AJRBEAGhgHcQAnBAEwEJsB6AwgbgChRJY_KAEMAlmDh0YWRiGABXVOgB0AczhQAokiVQAQgE8AkowAUPGDADkdECChWeASl4AlOMOBQAIgHkAssp0aIySpogoaFBUQmISdC48QA) to check what ES6 code compiles to.

### How to Follow Along

There are two ways to complete this tutorial: you could either write the code right
in the browser, or you could set up a local development environment on your machine.
You can choose either option depending on what you feel comfortable with.

#### If You Prefer to Write Code in the Browser

his is the quickest way to get started!

First, open this starter code in a new tab. It should display an empty tic-tac-toe
field. We will be editing that code during this tutorial.

You can now skip the next section about setting up a local development environment and head straight to the [overview](https://reactjs.org/tutorial/tutorial.html#overview).

#### If You Prefer to Write Code in Your Editor

Alternatively, you can set up a project on your computer.

Note: **this is completely optional and not required for this tutorial!**

This is more work, but lets you work from the comfort of your editor.

If you want to do it, here are the steps to follow:

1. Make sure you have a recent version of Node.js installed.
2. Follow the installation instructions to create a new project.

  ```shell
  npm install -g create-react-app
  create-react-app react-game
  ```

3. Delete all files in the `src/` folder of the new project (don’t delete the
  folder, just its contents).

  ```shell
  cd react-game
  rm -f src/*
  ```

4. Add a file named `index.css` in the `src/` folder with this [CSS code](https://codepen.io/gaearon/pen/oWWQNa?editors=0100).
5. Add a file named `index.js` in the `src/` folder with this [JS code](https://codepen.io/gaearon/pen/oWWQNa?editors=0010).
6. Add these three lines to the top of `index.js` in the `src/` folder:

  ```js
  import React from 'react';
  import ReactDOM from 'react-dom';
  import './index.css';
  ```

  Now if you run npm start in the project folder and open `http://localhost:3000`
  in the browser, you should see an empty tic-tac-toe field.

  We recommend following [these instructions](http://babeljs.io/docs/editors) to configure syntax highlighting for your editor.


### Help, I’m Stuck!

If you get stuck, check out the [community support resources](https://reactjs.org/community/support.html).
In particular, [Reactiflux](https://reactjs.org/community/support.html#reactiflux-chat) chat
is a great way to get quick help. If you don’t get a good answer anywhere,
please file an issue, and we’ll help you out.

With this out of the way, let’s get started!

## Overview

### What is React?

React is a declarative, efficient, and flexible JavaScript library for building user interfaces.

React has a few different kinds of components, but we’ll start with `React.Component` subclasses:

```js
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

We’ll get to the funny XML-like tags in a second. Your components tell React what you want to render – then React will efficiently update and render just the right components when your data changes.

Here, ShoppingList is a **React component class**, or **React component type**. A component takes in parameters, called `props`, and returns a hierarchy of views to display via the `render` method.

The `render` method returns a description of what you want to render, and then React takes that description and renders it to the screen. In particular, `render` returns a **React element**, which is a lightweight description of what to render. Most React developers use a special syntax called JSX which makes it easier to write these structures. The `<div />` syntax is transformed at build time to React.createElement('div'). The example above is equivalent to:

```js
return React.createElement('div', {className: 'shopping-list'},
  React.createElement('h1', /* ... h1 children ... */),
  React.createElement('ul', /* ... ul children ... */)
);
```

[See full expanded version.](https://babeljs.io/repl/#?presets=react&code_lz=DwEwlgbgBAxgNgQwM5IHIILYFMC8AiJACwHsAHUsAOwHMBaOMJAFzwD4AoKKYQgRg65cAyiXJVqUADKMmUAGbEATlADepRWSQA6SpiwBfTtwD0fAdwCucc12ANWASUrME1RZmDH7R2_YDqhAhMSACC5J7egtz2APIwVhZIEWDmnlYcnuAQrADc7EA)

If you’re curious, `createElement()` is described in more detail in the [API reference](https://reactjs.org/docs/react-api.html#createelement),
but we won’t be using it directly in this tutorial. Instead, we will keep using JSX.

You can put any JavaScript expression within braces inside JSX. Each React element
is a real JavaScript object that you can store in a variable or pass around your program.

The `ShoppingList` component only renders built-in DOM components, but you can
compose custom React components just as easily, by writing `<ShoppingList />`.
Each component is encapsulated so it can operate independently, which allows you
to build complex UIs out of simple components.

## Getting Started

Start with this example: [Starter Code](https://codepen.io/gaearon/pen/oWWQNa?editors=0010).

It contains the shell of what we’re building today. We’ve provided the styles so
you only need to worry about the JavaScript.

In particular, we have three components:

-. Square
-. Board
-. Game

The `Square` component renders a single `<button>`, the `Board` renders 9 squares,
and the `Game` component renders a board with some placeholders that we’ll fill
in later. None of the components are interactive at this point.

### Passing Data Through Props

Just to get our feet wet, let’s try passing some data from the Board component to the Square component.

In Board’s `renderSquare` method, change the code to pass a `value` prop to the Square:

```js
class Board extends React.Component {
  renderSquare(i) {
    return <Square value={i} />;
  }
}
```

Then change Square’s `render` method to show that value by replacing `{/* TODO */}` with `{this.props.value}`:

```js
class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {this.props.value}
      </button>
    );
  }
}
```

After: You should see a number in each square in the rendered output.

[View the current code](https://codepen.io/gaearon/pen/aWWQOG?editors=0010).

### An Interactive Component

Let’s make the Square component fill in an “X” when you click it. Try changing
the button tag returned in the `render()` function of the Square like this:

```js
class Square extends React.Component {
  render() {
    return (
      <button className="square" onClick={() => alert('click')}>
        {this.props.value}
      </button>
    );
  }
}
```

If you click on a square now, you should get an alert in your browser.

This uses the new JavaScript [arrow function](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Functions/Arrow_functions) syntax.
Note that we’re passing a function as the `onClick` prop. Doing
`onClick={alert('click')}` would alert immediately instead of when the button
is clicked.

React components can have state by setting `this.state` in the constructor, which
should be considered private to the component. Let’s store the current value of
the square in state, and change it when the square is clicked.

First, add a constructor to the class to initialize the state:

```js
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button className="square" onClick={() => alert('click')}>
        {this.props.value}
      </button>
    );
  }
}
```

In [JavaScript classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes),
you need to explicitly call `super();` when defining the constructor of a subclass.

Now change the Square `render` method to display the value from the current state,
and to toggle it on click:

-. Replace `this.props.value` with `this.state.value` inside the `<button>` tag.
-. Replace the `() => alert()` event handler with `() => this.setState({value: 'X'})`.

Now the `<button>` tag looks like this:

```js
class Square extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: null,
    };
  }

  render() {
    return (
      <button className="square" onClick={() => this.setState({value: 'X'})}>
        {this.state.value}
      </button>
    );
  }
}
```

Whenever `this.setStat`e is called, an update to the component is scheduled,
causing React to merge in the passed state update and rerender the component along
with its descendants. When the component rerenders, `this.state.value` will be `'X'`
so you’ll see an X in the grid.

If you click on any square, an X should show up in it.
View the current code.

[View the current code.](https://codepen.io/gaearon/pen/VbbVLg?editors=0010)

### Developer Tools

The React Devtools extension for [Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en)
and [Firefox](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/) lets
you inspect a React component tree in your browser devtools.

It lets you inspect the props and state of any of the components in your tree.

After installing it, you can right-click any element on the page, click “Inspect”
to open the developer tools, and the React tab will appear as the last tab to the right.

However, note there are a few extra steps to get it working with CodePen:

1. Log in or register and confirm your email (required to prevent spam).
2. Click the “Fork” button.
3. Click “Change View” and then choose “Debug mode”.
4. In the new tab that opens, the devtools should now have a React tab.

### Lifting State Up

We now have the basic building blocks for a tic-tac-toe game. But right now, the state is encapsulated in each Square component. To make a fully-working game, we now need to check if one player has won the game, and alternate placing X and O in the squares. To check if someone has won, we’ll need to have the value of all 9 squares in one place, rather than split up across the Square components.

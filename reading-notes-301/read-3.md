# Passing Functions to Components

>How do I pass an event handler (like onClick) to a component?
Pass event handlers and other functions as props to child components:

```
<button onClick={this.handleClick}>
```

>If you need to have access to the parent component in the handler, you also need to bind the function to the component instance (see below).

# How do I bind a function to a component instance?

>There are several ways to make sure functions have access to component attributes like this.props and this.state, depending on which syntax and build steps you are using.

```
Bind in Constructor (ES2015)
class Foo extends Component {
  constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    console.log('Click happened');
  }
  render() {
    return <button onClick={this.handleClick}>Click Me</button>;
  }
}
Class Properties (Stage 3 Proposal)
class Foo extends Component {
  // Note: this syntax is experimental and not standardized yet.
  handleClick = () => {
    console.log('Click happened');
  }
  render() {
    return <button onClick={this.handleClick}>Click Me</button>;
  }
}
Bind in Render
class Foo extends Component {
  handleClick() {
    console.log('Click happened');
  }
  render() {
    return <button onClick={this.handleClick.bind(this)}>Click Me</button>;
  }
}
```

```
Arrow Function in Render
class Foo extends Component {
  handleClick() {
    console.log('Click happened');
  }
  render() {
    return <button onClick={() => this.handleClick()}>Click Me</button>;
  }
}
```

>Is it OK to use arrow functions in render methods?
>Generally speaking, yes, it is OK, and it is often the easiest >way to pass parameters to callback functions.

>If you do have performance issues, by all means, optimize!

# Why is binding necessary at all?

>In JavaScript, these two code snippets are not equivalent:

>obj.method();
>var method = obj.method;
>method();
>Binding methods helps ensure that the second snippet works the same way as the first one.

>With React, typically you only need to bind the methods yopass to other components. For example, <button onClick={this.handleClick}> passes this.handleClick so you want to bind it. However, it is unnecessary to bind the render method or the lifecycle methods: we don???t pass them to other components.

>This post by Yehuda Katz explains what binding is, and how functions work in JavaScript, in detail.

>Why is my function being called every time the component renders?
>Make sure you aren???t calling the function when you pass it to the component:

```
render() {
  // Wrong: handleClick is called instead of passed as a reference!
  return <button onClick={this.handleClick()}>Click Me</button>
}
Instead, pass the function itself (without parens):

render() {
  // Correct: handleClick is passed as a reference!
  return <button onClick={this.handleClick}>Click Me</button>
}
```

>How do I pass a parameter to an event handler or callback?
You can use an arrow function to wrap around an event handler and pass parameters:

```
<button onClick={() => this.handleClick(id)} />
This is equivalent to calling .bind:

<button onClick={this.handleClick.bind(this, id)} />
```

>Example: Passing params using arrow functions
const A = 65 // ASCII character code

```
class Alphabet extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      justClicked: null,
      letters: Array.from({length: 26}, (_, i) => String.fromCharCode(A + i))
    };
  }
  handleClick(letter) {
    this.setState({ justClicked: letter });
  }
  render() {
    return (
      <div>
        Just clicked: {this.state.justClicked}
        <ul>
          {this.state.letters.map(letter =>
            <li key={letter} onClick={() => this.handleClick(letter)}>
              {letter}
            </li>
          )}
        </ul>
      </div>
    )
  }
}
```

>Example: Passing params using data-attributes
Alternately, you can use DOM APIs to store data needed for event handlers. Consider this approach if you need to optimize a large number of elements or have a render tree that relies on React.PureComponent equality checks.

````
const A = 65 // ASCII character code

class Alphabet extends React.Component {
  constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
    this.state = {
      justClicked: null,
      letters: Array.from({length: 26}, (_, i) => String.fromCharCode(A + i))
    };
  }

  handleClick(e) {
    this.setState({
      justClicked: e.target.dataset.letter
    });
  }

  render() {
    return (
      <div>
        Just clicked: {this.state.justClicked}
        <ul>
          {this.state.letters.map(letter =>
            <li key={letter} data-letter={letter} onClick={this.handleClick}>
              {letter}
            </li>
          )}
        </ul>
      </div>
    )
  }
}
```

## How can I prevent a function from being called too quickly or too many times in a row?

>If you have an event handler such as onClick or onScroll and want to prevent the callback from being fired too quickly, then you can limit the rate at which callback is executed. This can be done by using:

- throttling: sample changes based on a time based frequency (eg _.throttle)
- debouncing: publish changes after a period of inactivity (eg _.debounce)
- requestAnimationFrame throttling: sample changes based on requestAnimationFrame (eg raf-schd)
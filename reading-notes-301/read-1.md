# What Is React?

>React is a declarative, efficient, and flexible JavaScript library for building user interfaces. It lets you >compose complex UIs from small and isolated pieces of code called “components”.
>React has a few different kinds of components.


# Create React App

>Create React App is a comfortable environment for learning React, and is the best way to start building a new single-page application in React.
>It sets up your development environment so that you can use the latest JavaScript features, provides a nice developer experience, and optimizes your app for production. You’ll need to have Node >= 10.16 and npm >= 5.6 on your machine. To create a project, run:

```
npx create-react-app my-app
cd my-app
npm start

```


 # Passing Data Through Props

>To get our feet wet, let’s try passing some data from our Board component to our Square component.
>We strongly recommend typing code by hand as you’re working through the tutorial and not using copy/paste. This will help you develop muscle memory and a stronger understanding.

>In Board’s renderSquare method, change the code to pass a prop called value to the Square:
```
class Board extends React.Component {
  renderSquare(i) {
    return <Square value={i} />;
  }
}
```
>Change Square’s render method to show that value by replacing {/* TODO */} with {this.props.value}:
```
class Square extends React.Component {
  render() {
    return (
      <button className="square">
        {this.props.value}
      </button>
    );
  }
}
````
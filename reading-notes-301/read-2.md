# What are component lifecycle events?

>React lets you define components as classes or functions. The methods that you are able to use on these are called lifecycle events. These methods can be called during the lifecycle of a component, and they allow you to update the UI and application states.



## Mounting

>When an instance of a component is being created and inserted into the DOM it occurs during the mounting phase. Constructor, static getDerivedStateFromProps, render, componentDidMount, and UNSAFE_componentWillMount all occur in this order during mounting.

## Updating

>Anytime a component is updated or state changes then it is rerendered. These lifecycle events happen during updating in this order.
static getDerivedStateFromProps, shouldComponentUpdate, render,
getSnapshotBeforeUpdate, componentDidUpdate, UNSAFE_componentWillUpdate, UNSAFE_componentWillReceiveProps

## Unmounting

>The final phase of the lifecycle if called when a component is being removed from the DOM. componentWillUnmount is the only lifecycle event during this phase.

## constructor()

>The constructor for a React component is called before it is mounted.If the component is a subclass you should call super(props), or the props will be undefined. constructors can be used to assign state using this.state or to bind event handle methods to an instance. Let’s take a look at some example code.
class FishTableRow extends React.Component {

~~~
constructor() {
super(props); //gives us access to props
//Don’t call this.setState() here
this.state = { //intitialize local state
showDescription: false
}; }
~~~

>Avoid using this.setState() in the constructor because it can lead to side effects, and it is unnecessary. Doing this will ignore all updates to props, so it shouldn’t be done unless it is intentional.
static getDerivedStateFromProps()
>This method exists for rare cases where the state relies on changes in props over time.

## render()

>Render is the only required method in a class component. It will examine this.props and this.state when called. The render function should not modify the component state because it would cause a lot of bugs by changing the state every time it rerenders. I also should not directly interact with the browser. render will not be invoked if shouldComponentUpdate() returns false. Here is an example of using render.

~~~
ReactDOM.render(
<FishTable fishes= {fishData}/>,//set fishes document.getElementById(‘app’)
);
~~~

## componentDidMount()

>This method is invoked immediately after a component is mounted. If you need to load anything using a network request or initialize the DOM, it should go here. This method is a good place to set up any subscriptions. If you do that, don’t forget to unsubscribe in componentWillUnmount().
setState() can be called here, but it should be used sparingly, because it will cause a rerender, which can lead to perfomance issues.
Here we use componentDidMount() to connect to the YouTube API and get videos when the components is rendered.
~~~
 componentDidMount() {
console.log(‘got videos’);
this.getVideos(‘cats’);
}
getVideos(query) {
var options = {
key: this.props.YOUTUBE_API_KEY,
query: query
};
~~~

## shouldComponentUpdate()
>The default behavior in react is to rerender after every state change. Setting shouldComponentUpdate() to false allows you to prevent this from happening. This is in order to optimize performance. If you want to use this method, it may be better to use PureComponent instead, which performs a shallow comparison of props and state. If you do decide to use this method, be sure to check the previous props and state with the current props and state. If shouldComponentUpdate() returns false, then UNSAFE_componentWillUpdate(), render(), and componentDidUpdate() will not be invoked.

## getSnapshotBeforeUpdate()

>This is another rarely used method that allows you to capture a picture of the DOM to check it before actually changing anything on the DOM.

## componentDidUpdate()

>This method is useful for performing network requests after a change has occurred.
~~~
componentDidUpdate(prevProps) {
// Typical usage (don’t forget to compare props):
if (this.props.userID !== prevProps.userID) {
this.fetchData(this.props.userID);
}
}
````

## componentWillUnmount()
>This method allows you to clean up the DOM and netwrok requests/ subscriptions.
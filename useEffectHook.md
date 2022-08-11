# Component Lifecycle / Use Effect Hook

## Effect Hook 

### Example Using Classes
In React **class components**, the `render` method itself shouldn’t cause side effects. It would be too early — we typically want to perform our effects after React has updated the DOM.

This is why in React classes, we put side effects into `componentDidMount` and `componentDidUpdate`.

```
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  componentDidMount() {
    document.title = `You clicked ${this.state.count} times`;
  }
  componentDidUpdate() {
    document.title = `You clicked ${this.state.count} times`;
  }

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Click me
        </button>
      </div>
    );
  }
}
```

### Example Using Hooks
The Effect Hook lets you perform side effects in **function components**:

```
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

Examples of side effects:
- Data fetching.
- Setting up a subscription.
- Manually changing the DOM in React components.

#### What does useEffect do?
By using this Hook, you tell React that your component needs to do something after render. 

#### Why is useEffect called inside a component?
Placing `useEffect` inside the component lets us access the count state variable (or any props) right from the effect.

#### Does useEffect run after every render? 
Yes! By default, it runs both after the first render and after every update. 

## Effects with Cleanup

### Example Using Classes
In a React class, you would typically set up a subscription in `componentDidMount`, and clean it up in `componentWillUnmount`. For example, let’s say we have a ChatAPI module that lets us subscribe to a friend’s online status. Here’s how we might subscribe and display that status using a class:

```
class FriendStatus extends React.Component {
  constructor(props) {
    super(props);
    this.state = { isOnline: null };
    this.handleStatusChange = this.handleStatusChange.bind(this);
  }

  componentDidMount() {
    ChatAPI.subscribeToFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }
  componentWillUnmount() {
    ChatAPI.unsubscribeFromFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }
  handleStatusChange(status) {
    this.setState({
      isOnline: status.isOnline
    });
  }

  render() {
    if (this.state.isOnline === null) {
      return 'Loading...';
    }
    return this.state.isOnline ? 'Online' : 'Offline';
  }
}
```

### Example Using Hooks
You might be thinking that we’d need a separate effect to perform the cleanup. But code for adding and removing a subscription is so tightly related that useEffect is designed to keep it together. If your effect returns a function, React will run it when it is time to clean up:

```
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // Specify how to clean up after this effect:
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}
```

#### Why did we return a function from our effect? 
This is the optional cleanup mechanism for effects. Every effect may return a function that cleans up after it.

#### When exactly does React clean up an effect? 
React performs the cleanup when the component unmounts. However, as we learned earlier, effects run for every render and not just once. This is why React also cleans up effects from the previous render before running the effects next time.

## Reference:

[Effects Hook](https://reactjs.org/docs/hooks-effect.html)

### [Home Page](./README.md)
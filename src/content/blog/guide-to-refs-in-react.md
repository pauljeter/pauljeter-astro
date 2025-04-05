---
title: "A Guide to Refs in React"
description: ""
pubDate: 2019-08-17
heroImage: "/images/reactjs.jpg"
---

Sometimes when using React.js you’ll need an escape hatch to write imperative-style code to interact directly with DOM elements. Using React’s createRef method allows you to do just that!

React provides a way to get references to DOM nodes by using React.createRef(). It’s really just an equivalent of this all-too-familiar snippet of JavaScript:

```javascript
document.getElementById('foo-id');
```

This is exactly what React.createRef() does, although it requires a bit of a different setup.

##Usage
To get the a reference to the DOM node you have to do two things:

```javascript
import React, { Component } from 'react';

class Foobar extends Component {
  constructor(props) {
    super(props);
    this.myInput = React.createRef();    // initialize "this.myInput"  
  }

  render() {
    return (
      <input ref={this.myInput}/>        {/* pass "this.myInput" as prop */}
    );
  }
}
```

All standard HTML elements in React have a reserved prop called ref (much like style which is a reserved prop). Simply pass the ref you initialized in the constructor to the ref prop… and voila! You can start interacting with the <input> DOM node by using this.myInput.current!

> `this.myInput.current` holds the reference to the DOM node

### Example: Focusing an `<input>`
Taking that last code snippet, let’s make a small adjustment to demonstrate how we could start interacting with the <input> DOM node:

```javascript
import React, { Component } from 'react';

export default class App extends Component {
  constructor(props) {
    super(props);
    this.myInput = React.createRef();  
  }
  render() {
    return (
      <div>
        <input ref={this.myInput}/>

        <button onClick={() => {
          this.myInput.current.focus();
        }}>
          focus!
        </button>
      </div>
    );
  }
}
```

Calling the `focus()` method isn’t a React.js thing… it’s a normal JavaScript thing! For example, this is how it’s done with vanilla JavaScript:

```javascript
document.getElementById('myInput').focus();
```

### Controlling an HTML media element
You can also use `React.createRef()` and the standard JavaScript `<video>` API to control playback!

```javascript
import React, { Component } from 'react';

export default class App extends Component {
  constructor(props) {
    super(props);
    this.myVideo = React.createRef();
  }
  render() {
    return (
      <div>
        <video ref={this.myVideo} width="320" height="176" controls>
          <source src="https://blender.com/big-buck-bunny.mp4" type="video/mp4" />
        </video>
        <div>
          <button onClick={() => {
            this.myVideo.current.play();
          }}>
            Play
          </button>
          <button onClick={() => {
            this.myVideo.current.pause();
          }}>
            Pause
          </button>
        </div>
      </div>
    );
  }
}
```

## Refs with React Hooks Using useRef
Refs in React Hooks aren’t much different than `class` components. It’s achieved using the [useRef](https://reactjs.org/docs/hooks-reference.html#useref) hook. Just remember to omit `this` and you are golden

```javascript
import React, { useRef } from "react";

function App() {

  const myInput = useRef(null);

  return (
    <div>
      <input ref={myInput}/>
      <button onClick={() => {
        myInput.current.focus();
      }}>
        focus!
      </button>
    </div>
  );  
}
```

You can’t use `createRef` for pure functional components since they lack many of the React-y features like state & lifecycle components

Visit the [React docs](https://reactjs.org/docs/refs-and-the-dom.html) for detailed info about `createRef`.
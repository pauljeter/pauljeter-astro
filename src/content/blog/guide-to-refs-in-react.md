---
title: "A Guide to Refs in React"
description: "When to reach for refs in React, with examples for focusing inputs and controlling a video element."
pubDate: 2019-08-17
heroImage: "/images/reactjs.jpg"
---

Most of the time in React you don't touch the DOM directly. State flows down, events flow up, and the framework handles the rest. But every so often you need to do something imperative. Focus an input after a button click. Trigger play on a video. Measure an element's width.

That's what refs are for. They're React's escape hatch.

## The Mental Model

If you've written vanilla JavaScript, you've done this:

```javascript
document.getElementById('foo-id');
```

A ref is the React-flavored version. You set one up, attach it to an element, and React hands you back the underlying DOM node. From there it's the same DOM API you already know.

## Class Components

Two steps. Create the ref in the constructor, then attach it with the `ref` prop.

```javascript
import React, { Component } from 'react';

class Foobar extends Component {
  constructor(props) {
    super(props);
    this.myInput = React.createRef();
  }

  render() {
    return (
      <input ref={this.myInput} />
    );
  }
}
```

`ref` is a reserved prop, same as `key` or `style`. Once the component mounts, `this.myInput.current` points at the actual `<input>` DOM node.

> `this.myInput.current` holds the reference to the DOM node.

## Example: Focus an Input

The classic use case. A button that focuses an input.

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
        <input ref={this.myInput} />

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

Worth noting: `focus()` isn't a React method. It's the same DOM API you'd use without React:

```javascript
document.getElementById('myInput').focus();
```

You're not learning a new platform when you use refs. You're using the platform you already knew, through a different door.

## Example: Controlling a Video

Same pattern, applied to `<video>`. The HTMLMediaElement API gives you `play()`, `pause()`, `currentTime`, all of it. Refs let you call them.

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

## Refs with Hooks

In a function component, use [useRef](https://reactjs.org/docs/hooks-reference.html#useref). Same idea, less ceremony. Drop the `this`.

```javascript
import React, { useRef } from "react";

function App() {
  const myInput = useRef(null);

  return (
    <div>
      <input ref={myInput} />
      <button onClick={() => {
        myInput.current.focus();
      }}>
        focus!
      </button>
    </div>
  );
}
```

`createRef` won't work in a function component. It creates a new ref on every render, which defeats the purpose. `useRef` holds onto the same ref across renders, which is what you want.

## When Not to Use Refs

If you're reaching for a ref to read or set state, stop. Use state. Refs are for the cases where state genuinely doesn't fit: focus management, text selection, media playback, integrating with imperative libraries.

The React team's [refs docs](https://reactjs.org/docs/refs-and-the-dom.html) cover the edge cases in detail. Worth a read if you're doing anything past the examples here.

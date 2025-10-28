---
title: 'A Simple Guide to React Redux'
description: 'A hands-on guide to understanding Redux and React-Redux through real-world examples using vanilla JS and React.'
pubDate: '2019-09-13'
heroImage: '/images/redux.jpg'
category: 'Engineering'
tags: ['redux', 'react', 'javascript']
---

Redux is one of those libraries that sounds more complex than it really is. My goal here is to break it down in a practical way, starting with core Redux concepts, then moving into React integration with both class-based and functional components.

This guide is split into three parts:

1. **Core Redux** - Actions, Reducers, Store, and using Redux with vanilla JavaScript.
2. **React Redux with Class Components** - Wiring up Redux using `connect`.
3. **React Redux with Functional Components** - Using Redux hooks like `useSelector` and `useDispatch`.

There's also a bonus section that touches on middleware and async actions using `redux-thunk`.

---

## Part One: Core Redux (Vanilla JS)

### What Redux Solves

As your app grows, managing state across multiple components becomes a pain. Redux introduces a single source of truth: a centralized, immutable state tree. Think of Redux as your app's state manager.

Redux revolves around three key concepts:

- **Actions** - Describe _what_ happened.
- **Reducers** - Handle _how_ the state changes.
- **Store** - Holds your application state and lets you dispatch actions and subscribe to updates.

### Example App: Notes App in Vanilla JS

We'll build a dead-simple notes app to get a feel for Redux. No styling, no frills, just pure functionality.

```js
// Example state
{
  notes: [
    { title: 'First Note', content: 'Some content here' },
    { title: 'Second Note', content: 'More content' }
  ]
}
```

Each note is an object with a title and content. All notes live in an array under the `notes` key in the state tree.

### Setting Up the Project

If you're on a Unix-based system:

```bash
mkdir -p redux-notes-app/{dist,src/{actions,reducers,store}} && cd redux-notes-app
touch index.html .babelrc webpack.config.js
touch src/actions/actions.js src/reducers/reducers.js src/store/store.js src/main.js
```

Install your dependencies:

```bash
npm init -y
npm install redux webpack webpack-cli @babel/core babel-loader @babel/preset-env --save-dev
```

Or with Yarn:

```bash
yarn init -y
yarn add redux webpack webpack-cli @babel/core babel-loader @babel/preset-env --dev
```

### Writing Actions

```js
// src/actions/actions.js
export const ADD_NOTE = 'ADD_NOTE';

export function addNote(title, content) {
  return {
    type: ADD_NOTE,
    title,
    content
  };
}
```

Actions just describe what happened. They don't contain logic.

### Writing a Reducer

```js
// src/reducers/reducers.js
import { ADD_NOTE } from '../actions/actions';

const initialState = {
  notes: []
};

export default function notesReducer(state = initialState, action) {
  switch (action.type) {
    case ADD_NOTE:
      return {
        ...state,
        notes: [...state.notes, { title: action.title, content: action.content }]
      };
    default:
      return state;
  }
}
```

### Creating the Store

```js
// src/store/store.js
import { createStore } from 'redux';
import notesReducer from '../reducers/reducers';

const store = createStore(
  notesReducer,
  window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
);

export default store;
```

### Hooking Up the UI

In `main.js`, you subscribe to store updates and re-render the UI manually.

```js
// src/main.js
import store from './store/store';
import { addNote } from './actions/actions';

store.subscribe(() => {
  const state = store.getState();
  console.log(state);
  // Update the DOM with notes here
});
```

You get the idea, Redux lets you centralize state and make it predictable.

---

## Part Two: React + Redux (Class Components)

### Setting Up

Install Redux and React Redux:

```bash
npm install redux react-redux
```

Wrap your `<App />` in a `Provider` and pass it the store:

```jsx
// index.js
import { Provider } from 'react-redux';
import store from './store/store';

<Provider store={store}>
  <App />
</Provider>
```

### Connecting a Component with `connect`

```jsx
import { connect } from 'react-redux';
import { addNote } from '../actions/actions';

class NotesForm extends React.Component {
  handleSubmit = () => {
    this.props.addNote('Title', 'Content');
  };

  render() {
    return <button onClick={this.handleSubmit}>Add</button>;
  }
}

export default connect(null, { addNote })(NotesForm);
```

Use `mapStateToProps` when you need state, and `mapDispatchToProps` for actions.

---

## Part Three: React + Redux (Functional Components)

With functional components, you ditch `connect()` and use hooks.

### `useSelector` and `useDispatch`

```jsx
import { useSelector, useDispatch } from 'react-redux';
import { addNote, removeNote } from '../actions/actions';

function NotesForm() {
  const dispatch = useDispatch();

  const handleAdd = () => {
    dispatch(addNote('Title', 'Content'));
  };

  return <button onClick={handleAdd}>Add</button>;
}

function AllNotes() {
  const notes = useSelector(state => state.notes);
  const dispatch = useDispatch();

  return (
    <ul>
      {notes.map((note, idx) => (
        <li key={idx}>
          {note.title}
          <button onClick={() => dispatch(removeNote(idx))}>Delete</button>
        </li>
      ))}
    </ul>
  );
}
```

The `useSelector` hook lets you read from the store, and `useDispatch` lets you send actions.

---

## Bonus: Async Actions with Redux Thunk

Redux alone only handles sync actions. Use `redux-thunk` for async logic.

Install it:

```bash
npm install redux-thunk
```

Apply the middleware:

```js
// src/store/store.js
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';

const store = createStore(
  rootReducer,
  applyMiddleware(thunk)
);
```

Now you can write async actions:

```js
export function fetchNotes() {
  return function (dispatch) {
    fetch('/api/notes')
      .then(res => res.json())
      .then(data => dispatch({ type: 'FETCH_NOTES_SUCCESS', payload: data }));
  };
}
```

---

## Final Thoughts

Redux is a great tool, but it's most powerful when you apply it where it actually adds value. Don't use it just because it's popular, use it when your state starts to sprawl and local component state doesn't cut it anymore.

If you want to take this app further:

- Add note editing
- Add form validation
- Create an API backend
- Apply a polished design
- Extend it with filtering, archiving, or tagging

---

This guide is for engineers who want to go deeper and apply Redux with confidence. Use it as a launchpad. And when in doubt, keep things simple and iterate from there.

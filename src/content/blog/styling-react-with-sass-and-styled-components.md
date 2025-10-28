---
title: 'Styling React with Sass and Styled Components'
description: 'A practical guide comparing Sass and Styled Components in React, covering setup, benefits, and how to decide which to use.'
pubDate: '2019-09-20'
heroImage: '/images/sass-styled-components.jpg'
category: 'React'
tags: ['react', 'css-in-js', 'sass']
---

There's no shortage of opinions online about how to style your React apps. Should styles live in CSS files? Should they live alongside your components as CSS-in-JS? This article won't try to convince you one way or the other. Instead, we'll walk through how to use both Sass and Styled Components in a React application so you can see the trade-offs for yourself.

We'll build the same simple social card UI component using each approach. It'll include an image, username, timestamp, avatar, and status. Nothing fancy, just enough to explore the tooling.

---

## What's the Debate About?

The core of the CSS-in-JS vs. traditional stylesheets debate is around **separation of concerns**. Should styles live next to your markup and logic? Or should they be in separate files?

There's no universal answer. Some folks prefer the locality of Styled Components. Others want the simplicity and flexibility of Sass. I've found both useful, and more often than not, I reach for Sass, but that's not a hard rule.

Let's look at both so you can decide what works for your projects.

---

## Styled Components: CSS-in-JS for React

Styled Components is one of the most popular CSS-in-JS libraries for React. It lets you write actual CSS inside your JavaScript and scope styles to components.

### Installation

If you already have a React app set up, install Styled Components:

```bash
npm install styled-components
# or
yarn add styled-components
```

### Creating the Card

```jsx
import styled from 'styled-components';

const Card = styled.div`
  max-width: 350px;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
  margin: 30px auto;
  overflow: hidden;

  img {
    max-width: 100%;
  }
`;
```

This is a typical use of Styled Components. You define styled versions of native elements like `div`, `h1`, etc., and use them directly in your JSX.

### Responsive Styling

Styled Components also supports media queries:

```js
@media (max-width: 1000px) {
  background-color: red;
}
```

You can even use nested selectors (just like Sass):

```js
> div {
  padding: 10px 20px;

  p {
    font-weight: bold;

    span {
      color: #999;
    }
  }
}
```

### Dynamic Styles with Props

```jsx
const Card = styled.div`
  border: ${(props) => props.border || '1px solid #ccc'};
`;
```

You can drive styles with props, which comes in handy for theming and component variations.

### Using a Theme

```jsx
import { ThemeProvider } from 'styled-components';

const theme = {
  primary: '#333',
  secondary: '#999',
};

<ThemeProvider theme={theme}>
  <App />
</ThemeProvider>
```

Now you can access theme values in your styled components using `props.theme`.

---

## Sass in React

Sass is a mature and powerful CSS preprocessor that compiles down to CSS. It gives you variables, nesting, mixins, and more.

### Setup with Parcel

We'll use Parcel to keep setup minimal:

```bash
npm install parcel
npm install sass
```

Create your Sass folder structure like this:

```
sass/
├── _variables.scss
├── _elements.scss
├── components/
│   └── _socialcard.scss
└── app.scss
```

In `app.scss`, import your partials:

```scss
@import './variables';
@import './elements';
@import './components/socialcard';
```

### Sass Variables

```scss
// _variables.scss
$font: sans-serif;
$primary: #333;
$secondary: #999;
```

### Global Styles

```scss
// _elements.scss
body {
  font-family: $font;
  color: $primary;
}
```

### Component Styles

```scss
// components/_socialcard.scss
.social_card {
  max-width: 350px;
  border: 1px solid rgba(0, 0, 0, 0.1);
  border-radius: 5px;
  box-shadow: 5px 5px 10px rgba(0, 0, 0, 0.3);
  margin: 30px auto;
  overflow: hidden;

  img {
    max-width: 100%;
  }

  .social_card_body {
    padding: 10px 20px;

    > div {
      display: flex;
      justify-content: space-between;

      p {
        font-weight: bold;

        span {
          color: $secondary;
          font-weight: 300;
          font-size: 0.8rem;
        }
      }

      img {
        max-width: 50px;
        border-radius: 100%;
      }
    }

    .social_interactions {
      display: flex;
      justify-content: space-between;

      p {
        display: flex;
        align-items: center;

        img {
          width: 20px;
          padding: 5px;
          opacity: 0.3;
        }
      }
    }
  }
}
```

Import `app.scss` into your React entry point:

```js
import './sass/app.scss';
```

---

## Final Thoughts

Both Sass and Styled Components are powerful, and each has its sweet spots:

- **Styled Components** are great for component-scoped styles, dynamic theming, and colocating logic and styling.
- **Sass** shines when you want global styling conventions, easy reuse with mixins, and fast, familiar CSS syntax.

You don't need to pick one forever. Try both and use what feels right for each project. I lean toward Sass in most production work, but I'll reach for Styled Components when I want tighter integration with component logic.

---

Choose the tools that help your team move quickly, stay consistent, and build something great.

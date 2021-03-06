# Getting Started

## Installation

Download the minified library from a [CDN](https://unpkg.com/hyperapp).

```html
<script src="https://unpkg.com/hyperapp"></script>
```

And import it.

```js
const { h, app } = hyperapp
```

Or install with npm / Yarn.

<pre>
npm i <a href="https://www.npmjs.com/package/hyperapp">hyperapp</a>
</pre>

Then with a module bundler like [rollup](https://github.com/rollup/rollup) or [webpack](https://github.com/webpack/webpack), use as you would anything else.

```jsx
import { h, app } from "hyperapp"
```

See [JSX] or [hyperx] for setup instructions.

[hyperx]: /docs/hyperx.md
[JSX]: /docs/jsx.md


## Hello World

Let's begin with a simple program. Paste this code in a new HTML file and open it in your browser or [try it here](https://codepen.io/hyperapp/pen/PmjRov?editors=1010).

```html
<body>
<script src="https://unpkg.com/hyperapp"></script>
<script>

const { h, app } = hyperapp

app({
  state: {
    title: "hello!"
  },
  view: state => h("h1", {}, state.title)
})

</script>
</body>
```

You should see "hello!" is displayed on the page.

The state describes the application's data.

```js
state: {
  title: "hello!"
}
```

The view describes the application's user interface.

```js
state => h("h1", {}, state.title)
```

You can create a view using [JSX] or [hyperx] too.

```jsx
state => <h1>{state.title}</h1>
```

The [app](/docs/api.md#app) function wraps it all together and renders the view on the DOM.

```jsx
app({ ... })
```

Let's make it interactive! Add the following code below the view declaration.

```jsx
actions: {
  reverse(state) {
    return {
      title: state.title.split("").reverse().join("")
    }
  }
}
```

[Actions](/docs/actions.md) allow you to update the state tree to trigger a re-render.

Modify the view function to take the action and call it when the heading is clicked.

```jsx
view: (state, { reverse }) =>
  <h1 onclick={reverse}>
    {state.title}
  </h1>
```

Well done! You can [try it online](https://codepen.io/hyperapp/pen/NvYdma?editors=0010) too.

Continue reading to learn more and don't miss out the [tutorials](/docs/tutorials.md) section. Happy coding!

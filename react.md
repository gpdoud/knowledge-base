# React

This is an example of a function that renders HTML

```jsx
function PageTitle(props) {
  return ( 
    <div className={props.color}>
      <h1>{props.title}</h1>
      <h3>{proper.subtitle}</h3>
    </div>
  )
}
```

- The function name that will be used as an HTML tag must start with an uppper case character.
- There should be a single parent element returned.
- If the function takes parameters, the function should be declared as `props`
- Interpolation requires wrapping variables with single braces
- Wrap multiple JSX statements in parentheses
- `className` is used to render the `class` attribute
- In JSX, opening tags only (like `<input>`) require the trailing slash (`<input />`)
- Wrap code in single braces to treat is like ordinary Javascript (`<span> {2 + 3} </span>`)

### Adding events

```jsx
  function alert() {
    alert("This is an alert");
  }
  const html = (
    <button onClick={alert}>Click me!</button>
  )
```

### Add React to existing project

Start by adding the following script tags right before the `</body>` tag.

```jsx
  <!-- ... other HTML ... -->

  <!-- Load React. -->
  <!-- Note: when deploying, replace "development.js" with "production.min.js". -->
  <script src="https://unpkg.com/react@18/umd/react.development.js" crossorigin></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js" crossorigin></script>

  <!-- Load our React component. -->
  <script src="like_button.js"></script>
  


</body>
```

The `like_button.js` is React code to execute.

```jsx
'use strict';

const e = React.createElement;

class LikeButton extends React.Component {
  constructor(props) {
    super(props);
    this.state = { liked: false };
  }

  render() {
    if (this.state.liked) {
      return 'You liked this.';
    }

    return e(
      'button',
      { onClick: () => this.setState({ liked: true }) },
      'Like'
    );
  }
}

<!-- React code to run
const domContainer = document.querySelector('#like_button_container');
const root = ReactDOM.createRoot(domContainer);
root.render(e(LikeButton));
```

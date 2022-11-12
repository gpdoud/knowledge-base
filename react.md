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

### Components

```jsx
  class MyComponent extends React.Component {
    render() {
      <h1>Welcome to My Component</h1>
    }
  }
  ReactDOM.render(
    <MyComponent />,
      document.getElementById('app')
```

- `props` can be displayed by referencing `this.props`.
- `props` and `state` are the only dynamic properties
- Attribute values must surround the value with braces UNLESS the value is a string.

### State

Keeps the state of a component

```jsx
  class MyClass extends React.Component {
    constructor(props) {
      super(props);
      this.state = { a: "aaa", b: "bbb", ... }
      this.changeState = this.changeState.bind(this);
    }
    changeState() {
      this.setState({ z: "zzz"});
    }
    render() {
      return ( ... )
    }
  }
```

- The changeState.bind is to reestablish the `this`.
- The `setState(..)` CANNOT be called from inside the `render()` function

### Adding events

```jsx
  function alert() {
    alert("This is an alert");
  }
  const html = (
    <button onClick={alert}>Click me!</button>
  )
```

### map

`map` is like a `foreach` in C#. It is a function that iterates through a collection using lambda syntax.

```jsx
  const names = [ 'Greg', 'Cindy', 'Nick', 'Ken' ];
  names.map(name => <li>{name}</li>);
  // results
  // <li>Greg</li>
  // <li>Cindy</li>
  // <li>Nick</li>
  // <li>Ken</li>
```

Each item can include the jsx `key` attribute to help keep the order of the collection.

```jsx
  names.map( (name, i) => <li key={'fred_'+i}>{name}</li>

### Using &&

The logial and [&&] can be used to show or hide some jsx. Below, if `isBlack` is true, the 'Black' option will be included.

```jsx
  let isBlack = true;
  const options = (
    <ul>
      <li>Red</li>
      <li>Green</li>
      <li>Blue</li>
      { isBlack && <li>Black</li> }
    </ul>
  );
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

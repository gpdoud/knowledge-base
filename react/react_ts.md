# React/Typescript

## `creating a react project with vite`

```
npm create vite@latest [project-name]
```

## `rendering & rerendering`

A component is rendered the first time it is encountered.

After the initial render, if the state is a number, string, or boolean, the component will be rerendered if the state changes. If the state does not change, the component is NOT rerendered.

If the state is a composite component (i.e. record), and the object containing the data is updated with properties that change, the component will NOT be rerendered. To get the component to rerender, you have to change to object to a different object.

```tsx
let initCust = { id: 0, name: "DSI" };
const [customer, setCustomer] = setState(initCust);

const changeCustomer = (newId, newName) => {
  initCust.id = newId;
  initCust.name = newName;
  setCustomer(initCust); // this does not rerender the component because it is using the same object (initCust)

  newCust = [...initCust]; // copies initCust
  newCust.id = newId;
  newCust.name = newName;
  setCustomer(newCust); // this does rerender the component
};
```

## `useReducer()`

This hook is similar to the `useState()` but it likely used in a more complex environment. When using the reducer, it operates by making a call to a function called `reducer` that takes two parameters: the state and the action.

```tsx
import { useReducer } from "react";

enum ActionType {
  Add = "add",
  Sub = "sub",
}

interface IAction {
  type: ActionType;
  payload: number;
}

interface IState {
  sum: number;
}

function reducer(state: IState, action: IAction) {
  const { type, payload } = action;
  switch (type) {
    case ActionType.Add:
      return {
        ...state,
        sum: state.sum + payload,
      };
    case ActionType.Sub:
      return {
        ...state,
        sum: state.sum - payload,
      };
    default:
      return state;
  }
}

export default function App() {
  const [state, dispatch] = useReducer(reducer, { sum: 0 });

  const Add = () => dispatch({ type: ActionType.Add, payload: 1 });
  const Sub = () => dispatch({ type: ActionType.Sub, payload: 1 });

  return (
    <>
      <label>Count: {state.sum}</label>
      <button onClick={Add}>Add</button>
      <button onClick={Sub}>Sub</button>
    </>
  );
}
```

## `useState()`

This hook is used like a variable within a component. It allows reading and setting the value of data along with defining the inital state of the data. It can be used as a generic allowing the defining the type when created.

When the data in `useState()` is changed, if it is used on the UI, the UI is rerendered automatically. If the state value does NOT change, the component is not rerendered.

When setting the property, if it is a complex object, the entire object my be set.

```tsx
const [ name, setName ] = useState<string>('');

// accessing the state property
<h1>{ name }</h2>

// setting the state property
setName('Pat');

// useState with an object
interface Customer {
  id: number;
  name: string;
}

const [ customer, setCustomer ] = useState<Customer>({
  id: 0, name: ''
});

setCustomer({
  id: 10, name: 'ACME Mfg'
})
```

## `useEffect()`

This is a construct that will execute some code whenever the dependencies change. If there is not dependencies, it will execute only once.

```tsx
const [ counter; setCounter ] = useState<number>(0);

useEffect(() => {
  console.log("Counter is", counter);
},[counter]);

return (
  <button
    onClick={() => setCounter(c => c + 1)}>
      Increment
    </button>
)
```

## `useContext`

useContext allows passing data to any components that need it.

```tsx
// Create the context. It may be exported
export const CustomerContext = createContext<Customer>({
  id: 0,
  name: "",
} as Customer);
// Retrieve the context
let context = useContext(CustomerContext);
// Change the context
context = { id: 1, name: "DSI" };

return (
  <div>
    <h1>
      id: {context.id} name: {context.name}
    </h1>
  </div>
);
```

## `useRef()`

This hook holds a property that is not relevant to the UI. It can be changed like any normal variable. It could be used to hold something like the UI theme (i.e. 'dark' or 'light') or some feature that is turned on or off. This hook works similarly to `useState` except changes to `useRef()` does NOT cause the UI to be rerendered

```tsx
const AdvancedFeature = useRef(true);

AdventureFeature = false;
```

## `useId()`

This hook creates a unique id value. It should NOT be used as a Key value. Keys should come from the data.

```tsx
const newId = useId();
```

## `use()`

_This is experimental_.

This hook is a way to read a resource like a context that is not a part of the component.

## `React.FC`

FC stands for function component and it provides a simplier syntax for component that takes props. It also allows default values for the props.

```tsx
interface Props {
    code: number;
    name: string;
    email: string;
}

export const TestFC: React.FC<Props> = ({code, name, email}) => {

    TestFC.defaultProps = {
        {/* uses the default if code is not provided in the props */}
        code: 0, name: '?', email: '?'
    }

    return (
        <>
        <p>{code}</p>
        <p>{name}</p>
        <p>{email}</p>
        </>
    )
}
```

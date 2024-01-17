# React/Typescript

## `useEffect()`

This is a construct that will execute some code whenever the dependencies change. If there is not dependencies, it will execute only once.

```tsx
const [ counter; setCounter ] = useState<number>(0);

useEffect(() => {
  console.log("Counter is", counter);
},[counter]);

return (
  <button 
    onClick={() => setCounter(counter + 1)}>
      Increment
    </button>
)
```

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
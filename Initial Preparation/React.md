# React

## Route

BrowserRouter, Router, Route and Link from react-router-dom

`npm install react-router-dom`

For the code below, then rendering the rooms component, home component will be rendered too since the path also matches (`/rooms` starts with `/` too)

```JavaScript
<Route path="/" component={Home} />
<Route path="/rooms" component={Room} />
<Route path="/single-room" component={SingleRoom} />
```

For the code below, React will only render the component with the path that matches exactly


```JavaScript
<Route exact path="/" component={Home} />
<Route exact path="/rooms" component={Room} />
<Route exact path="/single-room" component={SingleRoom} />
```

### Error Page

To have a 404 error page, use the wildcard path

```JavaScript
<Route path="*" component={Error} />
```

## React Icons

`npm install react-icons -save`

## Class vs. Function Components

The 3 built-in lifecycle methods like componentDidMount, componentDidUpdate, and componentWillUnmount are the main difference

For class components

```JavaScript
class MyComponent extends Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  componentDidMount() {
    console.log('Component mounted');
  }

  render() ...
```

For function components, use hook to manage the component life cycle, if the array at the end has dependencies the first log will be set for the component updated lifecycle, if the array is empty, the component lifecycle is mounted

```JavaScript
const MyComponent = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log('Component mounted or updated');
    return () => {
      console.log('Component will unmount');
    };
  }, []);

  return () ...
```

Or to put all 3 life cycles together

```JavaScript
const MyComponent = () => {
  const [isMounted, setIsMounted] = useState(false);

  useEffect(() => {
    // This runs only once when the component mounts
    setIsMounted(true);

    return () => {
      // This runs when the component unmounts
      console.log('Component will unmount');
    };
  }, []);

  useEffect(() => {
    if (isMounted) {
      // This runs on updates after the initial mount
      console.log('Component updated');
    }
  });
  return () ...
```
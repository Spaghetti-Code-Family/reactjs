## Focusable Input Coding Challenge Using ReactJS - [On TestDome](https://app.testdome.com/questions/react-js/focusable-input/85204)

Finish the FocusableInput component so that the input element automatically receives focus on the first render if the shouldFocus prop is true.

The component should use React Hooks.

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const FocusableInput = (props) => {
  // Write your code here
  const inputRef = React.useRef();

  React.useEffect(() => {
    props.shouldFocus && inputRef.current.focus();
  }, []);
  return <input ref={inputRef} />;
};

document.body.innerHTML = "<div id='root' />";
ReactDOM.render(
  <FocusableInput shouldFocus={true} />,
  document.getElementById("root")
);
setTimeout(() => console.log(document.getElementById("root").innerHTML));
```

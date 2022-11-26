## Simple Calculator Coding Challenge Using ReactJS - [On TestDome](https://app.testdome.com/questions/react-js/simple-calculator/76485)

<p>Finish the App component so that it updates and displays the calculated number using mathematical operations.

The Operations object is finished and should not be changed.

The App component should use the React.useReducer Hook to update the state using dispatched actions. When the App component is finished, the result div should display the number after the clicked mathematical operation is performed.
</p>

```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const OPERATIONS = {
  ADD: "ADD",
  SUBTRACT: "SUBTRACT",
};

function App() {
  const [number, updateNumber] = React.useState(0);

  const [state, dispatch] = React.useReducer((state, action) => {
    /* implement the reducer which should update the state based on the action */
    switch (action.type) {
      case "add":
        return state + number;
      case "subtract":
        return state - number;
      default:
        return state;
    }
    return state;
  }, 0);

  /* implement dispatches */
  const add = () => dispatch({ type: "add" });
  const subtract = () => dispatch({ type: "subtract" });

  const handleNumberChange = (e) => updateNumber(Number(e.target.value));

  return (
    <div>
      <div id="result">{state}</div>
      <div>
        <button id="add" onClick={add}>
          Add
        </button>
        <button id="subtract" onClick={subtract}>
          Subtract
        </button>
      </div>
      <div>
        <input type="text" value={number} onChange={handleNumberChange} />
      </div>
    </div>
  );
}

document.body.innerHTML = "<div id='root'></div>";
const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

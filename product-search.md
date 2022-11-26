## Product Search Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/product-search/57886)

A web store uses the following React component for showing suggestions while users are typing product names:
```
const ProductSearch = (props) => {
  let [name, setName] = React.useState();
  let [suggestions, setSuggestions] = React.useState([]);
  
  React.useEffect(() => {
    if(name !== undefined) {
      props.requestSuggestions(name, setSuggestions);
    }
  }, [name]);

  const onChange = (event) => {
    setName(event.target.value);
  };
  
  return (
    <div>
      <label htmlFor={"search"}>Product name</label>
      <input onChange={onChange} id={"search"} list={"suggestions"}></input>
      <datalist id={"suggestions"}>
        { suggestions.map((suggestion) => <option>{ suggestion }</option>) }
      </datalist>
    </div>
  );
};
```
Select all the correct answers.

---
### Solution:
- If the props.requestSuggestions function invokes setSuggestions using [name, suggestions] as the second parameter of React.useEffect, the component will be rerendered after each React.useEffect call.
- On the first component render, the value of the suggestions variable will be []
- If the requestSuggestions function calls setSuggestions with two items, they will be shown in the datalist.

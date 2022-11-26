## Subscriptions - [On TestDome](https://app.testdome.com/questions/react-js/subscription/57789)

```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const SubscribeButton = (props) => {
  // Write your code here
  const [isClicked, setIsClicked] = React.useState(false);
  const handleClick = () => setIsClicked((pre) => !pre);
  const content = isClicked ? (
    <p>Thank you for subscribing!</p>
  ) : (
    <button onClick={handleClick}>Click to subscribe!</button>
  );
  return content;
};

document.body.innerHTML = "<div id='root' />";
ReactDOM.render(<SubscribeButton />, document.getElementById("root"));

setTimeout(() => console.log(document.body.innerHTML));
```

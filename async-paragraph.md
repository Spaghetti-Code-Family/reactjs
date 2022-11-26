## Async Paragraph Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/async-paragraph/58348)

The AsyncParagraph component is used for rendering a paragraph whose value is changed by an async function.

The component will receive as props:

dataVersion - a version of the data.
loadData - a function that returns a Promise that resolves to a string.
The component should only invoke the loadData function on the first render and every time the dataVersion or loadData props are changed. The string that is returned from loadData should be rendered in a paragraph element.

For example, if the component is rendered like this:
```
<AsyncParagraph dataVersion="10"
  loadData={ 
              () => { 
                     return new Promise((resolve, reject) => { resolve("Data!"); }); 
              } 
           }
/>
```
the component should render to:
```
<p>Data!</p>
```

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const AsyncParagraph = (props) => {
  // Write your code here
  const [data, setData] = React.useState("");
  React.useEffect(() => {
    props.loadData().then((result) => setData(result));
  }, [props.dataVersion, props.loadData]);
  return <p>{data}</p>;
};

document.body.innerHTML = "<div id='root' />";
ReactDOM.render(
  <AsyncParagraph
    dataVersion="10"
    loadData={() => {
      return new Promise((resolve, reject) => {
        resolve("Data!");
      });
    }}
  />,
  document.getElementById("root")
);
setTimeout(() => console.log(document.getElementById("root").innerHTML), 300);
```

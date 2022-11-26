## Reorder Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/reorder/76647)

Complete the List component, which accepts an items prop and moves the clicked element to the first place in the list.

For example, if the component has the list prop ["A", "B", "C"], the list should look like:
```
<ul>
  <li>A</li>
  <li>B</li>
  <li>C</li>
</ul>
```
When item C is clicked in the list above, the list should be reordered, resulting in the following order:
```
<ul>
  <li>C</li>
  <li>A</li>
  <li>B</li>
</ul>
```

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const List = (props) => {
  // Yоur cоdе gоеs hеrе
  const [reorderedList, setreorderedList] = React.useState(props.items);

  const handleClick = (e) => {
    const filteredItems = reorderedList.filter(
      (item) => item !== e.target.textContent
    );
    setreorderedList([e.target.textContent, ...filteredItems]);
  };
  return (
    <ul>
      {reorderedList.map((item) => (
        <li key={item} onClick={handleClick}>
          {item}
        </li>
      ))}
    </ul>
  );
};

document.body.innerHTML = "<div id='root'> </div>";

const rootElement = document.getElementById("root");
ReactDOM.render(<List items={["A", "B", "C"]} />, rootElement);

let listItem = document.querySelectorAll("li")[2];
if (listItem) {
  listItem.click();
}
setTimeout(() => console.log(document.getElementById("root").innerHTML));
```

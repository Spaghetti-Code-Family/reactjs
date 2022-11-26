## List Wrapper Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/list-wrapper/57463)

Implement the withList function. It should accept a React component as an ItemComponent argument and it should return a new component that renders an array of ItemComponent - one for each element in the items prop. The returned component will receive the items prop that is an array, and the component should pass each item from the array to ItemComponent as an item prop.

For example, calling the withList function with the Link component and rendering it with the following as an items prop:
```
[
  { href:"https://www.google.com", text:"Google" },
  { href:"https://www.bing.com", text:"Bing" }
]
```
It should render as:
```
<ul>
  <li>
    <a href="https://www.google.com">Google</a>
  </li>
  <li>
    <a href="https://www.bing.com">Bing</a>
  </li>
</ul>
```

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
function withList(ItemComponent) {
  return ({ items }) => {
    return (
      <ul>
        {items.map((item, index) => (
          <li key={index}>
            <ItemComponent item={item} />
          </li>
        ))}
      </ul>
    );
  };
}

class Link extends React.Component {
  render() {
    return <a href={this.props.item.href}>{this.props.item.text}</a>;
  }
}

const LinkList = withList(Link);

document.body.innerHTML = "<div id='root'></div>";
const rootElement = document.getElementById("root");

if (LinkList) {
  let items = [
    { href: "https://www.google.com", text: "Google" },
    { href: "https://www.bing.com", text: "Bing" },
  ];
  ReactDOM.render(<LinkList items={items} />, rootElement);
  console.log(rootElement.innerHTML);
}
```

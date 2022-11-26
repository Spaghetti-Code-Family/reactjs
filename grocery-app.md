## Grocery App Coding Challenge Using ReactJS - [On TestDome](https://app.testdome.com/questions/react-js/grocery-app/76506)

You have a GroceryApp component, which receives a list of products, each one with name and votes. The app should render an unordered list, with a list item for each product. Products can be upvoted or downvoted.

By appropriately using React state and props, implement the upvote/downvote logic. Keep the state in the topmost component, while the Product component should accept props.

For example, passing the following array as products prop to GroceryApp [{ name: "Oranges", votes: 0 }, { name: "Bananas", votes: 0 }] and clicking the '+' button next to the Oranges should result in HTML like:
```
<div id="root">
  <ul>
    <li>
      <span>Oranges</span> - <span>votes: 1</span><button>+</button> <button>-</button>
    </li>
    <li>
      <span>Bananas</span> - <span>votes: 0</span><button>+</button> <button>-</button>
    </li>
  </ul>
</div>
```

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const Product = (props) => {
  const plus = () => {
    // Call props.onVote to increase the vote count for this product
    props.onVote("+", props.product.name);
  };
  const minus = () => {
    // Call props.onVote to decrease the vote count for this product
    props.onVote("-", props.product.name);
  };
  return (
    <li>
      <span>{props.product.name}</span> -{" "}
      <span>votes: {props.product.votes}</span>
      <button onClick={plus}>+</button> <button onClick={minus}>-</button>
    </li>
  );
};

const GroceryApp = (props) => {
  let [products, setProducts] = React.useState(props.products);
  const onVote = (dir, name) => {
    // Update the products array accordingly ...
    setProducts((prev) =>
      prev.map((item) => {
        if (item.name === name) {
          if (dir === "+") {
            item.votes++;
          } else if (dir === "-") {
            item.votes--;
          }
        }
        return item;
      })
    );
  };

  return (
    <ul>
      {products.map((product) => (
        <Product key={product.name} product={product} onVote={onVote} />
      ))}
    </ul>
  );
};

document.body.innerHTML = "<div id='root'></div>";

ReactDOM.render(
  <GroceryApp
    products={[
      { name: "Oranges", votes: 0 },
      { name: "Bananas", votes: 0 },
    ]}
  />,
  document.getElementById("root")
);

let plusButton = document.querySelector("ul > li > button");
if (plusButton) {
  plusButton.click();
}
console.log(document.getElementById("root").outerHTML);
```

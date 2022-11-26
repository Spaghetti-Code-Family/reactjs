## Shopping List Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/shopping-list/70728)

The ShoppingList component renders an unordered list, with each item displaying the name of the item and a button. Implement the removeItem method so that when the button is clicked, the item is removed from the list.

Using the sampleItems provided, the list will look like this:

TV[Remove]

Using the sampleItems provided, when the button is clicked on the only item, the list should be empty:

`<ul></ul>`

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const sampleItems = [
  {
    name: "TV",
    id: 876234812,
  },
];

class ShoppingList extends React.Component {
  constructor(props) {
    const { items } = props;
    super(props);
    this.state = { items };
    this.removeItem = this.removeItem.bind(this);
  }

  removeItem = (id) => {
    // Write your code here
    this.setState({
      items: this.state.items.filter((item) => item.id !== id),
    });
  };

  render() {
    return (
      <ul>
        {this.state.items.map((item) => (
          <li key={item.id}>
            {" "}
            {item.name}
            <button
              id="removeBtn"
              onClick={() => this.removeItem(item.id)}
              type="button"
            >
              Remove
            </button>
          </li>
        ))}
      </ul>
    );
  }
}

document.body.innerHTML = "<div id='root'> </div>";
const rootElement = document.getElementById("root");
ReactDOM.render(<ShoppingList items={sampleItems} />, rootElement);

document.getElementById("removeBtn").click();
setTimeout(() => console.log(rootElement.innerHTML));
```

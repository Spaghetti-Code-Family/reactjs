## Todo List - [On TestDome](https://app.testdome.com/questions/react-js/todo-list/76484)

<p>
Write a TodoList component that expects an items prop which is a list of objects, each with text and done properties.

TodoList also accepts an onItemClick function prop, which should be called when a user clicks an item in the list, if the item is not marked as done. 
Otherwise, the onItemClick should not be called and the click event itself should not be propagated further. 
The function should be called with the item object from the items list as the first parameter and the event as the second parameter.
</p>

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const TodoItem = (props) => <li onClick={props.onClick}>{props.item.text}</li>;

class TodoList extends React.Component {
  render() {
    const { items, onListClick } = this.props;
    return (
      <ul onClick={onListClick}>
        {items.map((item, index) => (
          <TodoItem
            item={item}
            key={index}
            onClick={this.handleItemClick.bind(this, item)}
          />
        ))}
      </ul>
    );
  }

  handleItemClick(item, event) {
    // Write your code here
    if (item.done) {
      event.stopPropagation();
      return;
    }
    this.props.onItemClick(item, event);
  }
}

const items = [
  { text: "Buy grocery", done: true },
  { text: "Play guitar", done: false },
  { text: "Romantic dinner", done: false },
];

const App = (props) => (
  <TodoList
    items={props.items}
    onListClick={(event) => console.log("List clicked!")}
    onItemClick={(item, event) => {
      console.log(item, event);
    }}
  />
);

document.body.innerHTML = "<div id='root'></div>";
const rootElement = document.getElementById("root");
ReactDOM.render(<App items={items} />, rootElement);
```

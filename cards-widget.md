## Cards Widget Coding Challenge Using ReactJS - [On TestDome](https://app.testdome.com/questions/react-js/cards-widget/47129)

An HTML widget for a children's game represents a clickable card row. Initially, all cards are face down. Whenever a card is clicked, it is turned over to face up, and any card that was previously face up is turned over to face down. Only one card can be face up at one time. Cards that are face up should have the content 'up' while face down cards should have the content 'down'. When an 'up' card is clicked, it remains 'up'.

Implement the React component Cards that accepts the amount prop which defines how many cards there should be. The component should be rendered as a table element. 

For example, after clicking the second cell on the Cards component, rendered as:
```
<Cards amount={4} />
```
the page should contain the following table:
```
<table>
  <tbody>
    <tr>
      <td>down</td>
      <td>up</td>
      <td>down</td>
      <td>down</td>
    </tr>
  </tbody>
</table>
```

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const Cards = (props) => {
  const [clickedItem, setClickedItem] = React.useState(0);
  return (
    <table>
      <tbody>
        <tr>
          {[...Array(props.amount).keys()].map((item, index) => (
            <td key={item} onClick={() => setClickedItem(index + 1)}>
              {clickedItem === index + 1 ? "up" : "down"}
            </td>
          ))}
        </tr>
      </tbody>
    </table>
  );
};

document.body.innerHTML = "<div id='root'> </div>";

const rootElement = document.getElementById("root");
ReactDOM.render(<Cards amount={4} />, rootElement);

let row = document.getElementById("root").getElementsByTagName("tr")[0];
if (row) {
  let cell = row.getElementsByTagName("td")[1];
  if (cell) {
    cell.click();
  }
}
setTimeout(() => console.log(document.getElementById("root").innerHTML));
```

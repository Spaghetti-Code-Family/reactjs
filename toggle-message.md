## Toggle Message Coding Challenge Using ReactJS - [On TestDome](https://app.testdome.com/questions/react-js/toggle-message/57704)

The Message component contains an anchor element and a paragraph below the anchor. Rendering of the paragraph should be toggled by clicking on the anchor element using the following logic:

- At the start, the paragraph should not be rendered.
- After a click, the paragraph should be rendered.
- After another click, the paragraph should not be rendered.
- Finish the Message component by implementing this logic.

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
class Message extends React.Component {
  state = {
    isVisible: false,
  };
  render() {
    return (
      <React.Fragment>
        <a
          href="#"
          onClick={() => this.setState({ isVisible: !this.state.isVisible })}
        >
          Want to buy a new car?
        </a>
        {this.state.isVisible ? <p>Call +11 22 33 44 now!</p> : null}
      </React.Fragment>
    );
  }
}

document.body.innerHTML = "<div id='root'> </div>";

const rootElement = document.getElementById("root");
ReactDOM.render(<Message />, rootElement);

console.log("Before click: " + rootElement.innerHTML);
document.querySelector("a").click();
console.log("After click: " + rootElement.innerHTML);
```

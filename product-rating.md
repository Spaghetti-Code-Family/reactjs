## Product Rating Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/product-rating/49059)

The Rating component consists of 5 stars. Each star is represented by a span element. The component should render to this HTML code:
```
<div id='rating'>
  <span>*</span>
  <span>*</span>
  <span>*</span>
  <span>*</span>
  <span>*</span>
</div>
```
When a span element is clicked, the active class should be added to that span element and to all span elements before it. Also, the active class should be removed from all span elements after it, if there are any.

For example, after the third span element has been clicked, the HTML code should look like this:
```
<div id='rating'>
  <span class="active">*</span>
  <span class="active">*</span>
  <span class="active">*</span>
  <span>*</span>
  <span>*</span>
</div>
```
Complete the Rating component so that it implements the logic of the HTML widget.

---

### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
class Rating extends React.Component {
  state = {
    clicked: 0,
  };
  render() {
    return (
      <div id="rating">
        {[...Array(5).keys()].map((_, index) => (
          <span
            onClick={() => this.setState({ clicked: index + 1 })}
            className={index + 1 <= this.state.clicked ? "active" : null}
          >
            *
          </span>
        ))}
      </div>
    );
  }
}

document.body.innerHTML = "<div id='root'> </div>";

const rootElement = document.getElementById("root");
ReactDOM.render(<Rating />, rootElement);

document.querySelectorAll("span")[2].click();
console.log(document.getElementById("rating").outerHTML);
```

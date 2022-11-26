## Click Button Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/click-button/57460)

A company is using the following component for various buttons that can only be clicked once:

```
class ClickOnceButton extends React.Component {
  constructor(props) {
    super(props);
    this.state = { wasClicked: false };
  }
  
  onButtonClick(event) {
    if(!this.state.wasClicked) {
      this.props.onClick(event);
    }
    this.setState({ wasClicked: true });
  }
  
  render() {
    return (<button onClick={ ____________ }>{ this.props.text }</button>);
  }
}
```
Select all the answers that fill the blank in onClick so that it correctly calls the onButtonClick method.

---
### Solution:
- `this.onButtonClick.bind(this)`
- `(event) => this.onButtonClick(event)`

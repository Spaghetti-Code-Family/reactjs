## Details Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/details/79807)

Consider the following React component:

```
class Details extends React.Component {
  constructor(props) {
    super(props);
    this.state = { visible: props.visible };
  }
 
  onClick() {
    this.setState((state, props) => { 
      return { visible: !state.visible }; 
    });
  }
  
  render() {
    return (
      <div>
        <p onClick={ this.onClick.bind(this) }>Show/Hide details</p>
        { this.state.visible ? <p>{ this.props.text }</p> : null }
      </div>
    );
  }
}

Details.defaultProps = { visible: true };
```
Select all the true statements.

---

#### Solution:
- If the component is rendered as: `<Details visible={true} text="Details!" />` the details will be visible after rendering
- If the setState call is replaced with the following: `this.setState(!this.state.visible);` it will result in an exception.


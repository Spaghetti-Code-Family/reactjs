## Email Input Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/email-input/57461)

Consider the following React component which is used to validate emails in forms:
```
class EmailInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = { inputValue: '', isValid: false };
  }
  
  render() {
    let onChange = (event) => {
      this.setState({inputValue: event.target.value}); 
      if(event.target.value.includes("@")) {
        this.setState({isValid: true});
      } else {
        this.setState({isValid: false});
      }
    };
    
    return <div><input onChange={onChange} /><p>{ this.state.isValid ? '' : this.props.message }</p></div>
  }
}
```
A new component, Form, was recently added to the app. Form will always be a parent component to EmailInput and make decisions based on data from it.

Select the minimal changes so that the state is lifted up from EmailInput to the Form component.

---
### Solution:
- The inputValue state should be kept in the Form component and passed as a prop to the EmailInput component.
- The Form component should pass a callback as a prop to update the state of isValid and inputValue.
- The onChange event handler should invoke the callback passed from the Form component to update the values.

## Email Form Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/email-form/78814)

Consider the following component here and below:
```
class FormField extends React.Component {
  onChange = (event) => {
    event.stopPropagation();
    this.props.onChange({
      name: event.target.name,
      value: event.target.value
    })
  }
  render() {
    return <div {...this.props} onChange={this.onChange}>{this.props.children}</div>
  }
}
```
Finish the render method in the App component for sending emails:

- It should render two FormField components, one for subject and one for body. The component for subject should be rendered before the component for the body.
- When rendered, FormField of the subject should contain an input element with the "subject" name prop.
- When rendered, FormField of the body should contain an input element with the "body" name prop.
- Each FormField component should have the onChange prop specified.

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
class App extends React.Component {
  state = {
    subject: "",
    body: "",
  };

  onChange = ({ name, value }) => {
    this.setState({
      [name]: value,
    });
  };

  render() {
    return (
      <form>
        {/*Write your code here*/}
        <FormField onChange={this.onChange}>
          <input name="subject" />
        </FormField>
        <FormField onChange={this.onChange}>
          <input name="body" />
        </FormField>
      </form>
    );
  }
}
```

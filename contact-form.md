## Contact Form Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/contact-form/78813)

<p>
Write a ContactForm component to display the following input fields:

An input with the name attribute set to "firstName".
An input with the name attribute set to "age".
If the users age is greater than or equal to 14, it should also display an input for the email address, with the name attribute set to "email".
If the user's age is less than 14, the email input should not be rendered.
The values for the fields should be stored in the component state, under the "firstName", "age", and "email" keys.
</p>

---

### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
class ContactForm extends React.Component {
  state = {
    // Fill in appropriate state properties
    firstName: "",
    age: 0,
    email: "",
  };

  handleChange = (e) => {
    this.setState((prev) => ({
      ...prev,
      [e.target.name]: e.target.value,
    }));
  };

  render() {
    return (
      <div>
        {/* render contact form input fields here */}
        <input type="text" name="firstName" onChange={this.handleChange} />
        <input type="number" name="age" onChange={this.handleChange} />
        {Number(this.state.age) >= 14 && (
          <input type="email" name="email" onChange={this.handleChange} />
        )}
      </div>
    );
  }
}

document.body.innerHTML = "<div id='root'></div>";
const rootElement = document.getElementById("root");
ReactDOM.render(<ContactForm />, rootElement);
```

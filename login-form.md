## Login Form Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/login-form/57790)

The following React component is used as a login form for a website:
```
function LoginForm(props) {
  let [username, setUsername] = React.useState("");
  let [password, setPassword] = React.useState(null);
  
  return (<div>
    <input onChange={(event) => setUsername(event.target.value)} name="username"></input>
    <input onChange={(event) => setPassword(event.target.value)} name="password" type="password"></input>
    <button onClick={() => props.login(username, password)}>Login</button>
  </div>);
}
```
Select all the true statements.

---
### Solution:
- Pasting into the input field named "password" will change the value of the password variable to the value of the input field.
- LoginForm is a functional component.
- The parent component should pass a prop function named login to handle the click event on the "Login" button.

## Theme Context Switcher Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/theme-context-switcher/76488)

Finish the Content and App components so that the section has its class set appropriately. When the user clicks the button, class should toggle between "theme-light" and "theme-dark" values. Note the following criteria:

The ThemeContext Context provider should be used in your implementation. No additional prop-passing is needed.
The Content component should use the React.useContext function to pass the Context between components.
For example, after the first render, the section element should look like this:
```
<section class="theme-dark"><span>Current theme: dark</span><button>Switch Theme</button></section>
```
After the first click, the section element should look like this:
```
<section class="theme-light"><span>Current theme: light</span><button>Switch Theme</button></section>
```

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const ThemeContext = React.createContext();

const Content = () => {
  const context = React.useContext(ThemeContext); // change this
  return (
    <section className={`theme-${context.theme}`}>
      <span>Current theme: {context.theme}</span>
      <button onClick={context.switchTheme}>Switch Theme</button>
    </section>
  );
};

function App() {
  const [theme, setTheme] = React.useState("dark");
  const switchTheme = () => {
    theme === "dark" ? setTheme("light") : setTheme("dark");
  };
  return (
    <ThemeContext.Provider value={{ theme, switchTheme }}>
      <Content />
    </ThemeContext.Provider>
  );
}

document.body.innerHTML = "<div id='root'></div>";
const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

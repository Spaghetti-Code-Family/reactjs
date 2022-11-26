## Toggle Options Visibility Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/toggle-options-visibility/45274)

<p>
The OptionsShower component renders a button and a list of options. Initially, none of the options should be visible. When clicked, the component should invert the visibility of all available options provided in sampleOptions. However, currently when the button is clicked nothing happens.

Fix the bug.
</p>
---

#### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const sampleOptions = [
  { id: "753", title: "This is the first option" },
  { id: "035", title: "This is the second option" },
];

class OptionsShower extends React.Component {
  constructor(props) {
    super(props);
    const { options } = props;
    this.state = { options, displayOptions: false };
  }

  displayOptions = () => {
    this.setState({
      options: this.state.options,
      displayOptions: !this.state.displayOptions,
    });
  };

  render() {
    var options = null;
    if (this.state.displayOptions) {
      options = (
        <ul id="options">
          {this.state.options.map((option) => (
            <li key={option.id}>{option.title}</li>
          ))}
        </ul>
      );
    }
    return (
      <div>
        <button onClick={this.displayOptions}>
          {this.state.displayOptions ? "Hide options" : "Show options"}
        </button>
        {options}
      </div>
    );
  }
}

document.body.innerHTML = "<div id='root'> </div>";
const rootElement = document.getElementById("root");
ReactDOM.render(<OptionsShower options={sampleOptions} />, rootElement);
```

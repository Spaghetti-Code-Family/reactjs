## Tab Strip Coding Challenge Using ReactJS - [On TestDome](https://app.testdome.com/questions/react-js/tab-strip/76486)

The TabStrip component should render a list of tabs:

- When a tab is clicked, only that tab should have the TabStrip-title-active CSS class, while all others should have the TabStrip-title CSS class.
- Implement the setActiveIndex and getActiveIndex methods. activeIndex property is the currently active tab index.
- The TabStrip component should change the active index using the onActiveIndexChange callback.

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
class TabStrip extends React.Component {
  render() {
    return (
      <div className="TabStrip">
        {this.props.titles.map((title, index) => {
          const className =
            "TabStrip-title" +
            (this.isActive(index) ? " TabStrip-title-active" : "");

          return (
            <div
              onClick={() => this.setActiveIndex(index)}
              key={index}
              className={className}
            >
              {title}
            </div>
          );
        })}
      </div>
    );
  }

  isActive(index) {
    return index === this.getActiveIndex();
  }

  setActiveIndex(activeIndex) {
    this.props.onActiveIndexChange(activeIndex);
  }

  getActiveIndex() {
    return this.props.activeIndex;
  }
}

class App extends React.Component {
  state = { activeIndex: 1 };
  render() {
    return (
      <div>
        <TabStrip
          activeIndex={this.state.activeIndex}
          onActiveIndexChange={(activeIndex) => {
            this.setState({
              activeIndex,
            });
          }}
          titles={["My account", "Settings", "Dashbboard"]}
        />
      </div>
    );
  }
}

document.body.innerHTML = "<div id='root'></div>";
const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

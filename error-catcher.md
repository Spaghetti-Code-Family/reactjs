## Error Catcher Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/error-catcher/47138)

Consider the following React component:
```
class ErrorCatcher extends React.Component {
  constructor(props) {
    super(props);
    this.state = { error: false };
  }

  static getDerivedStateFromError(error) {
    return { error: true };
  }
  
  render() {
    if(this.state.error) {
      return <h1>An error occured! Error catcher name: { this.props.description.name }</h1>;
    }
    return this.props.children;
  }
}
```
#### If the component is rendered by the following JSX expression
```
<ErrorCatcher description={ { name: "First" } }>
  <TogglableParagraph text="First!" />
</ErrorCatcher>
```
and the TogglableParagraph component throws an exception in it's render method, then:
- The ErrorCatcher will catch the exception and render the error message. (solution)

#### If the component is rendered by the following JSX expression
```
<React.Fragment>
  <ErrorCatcher description={ { name: "First" } }>
  </ErrorCatcher>

  <TogglableParagraph text="Second!" />
</React.Fragment>
```
and the TogglableParagraph component throws an exception in it's render method, then:
- The ErrorCatcher will not catch the exception. (solution)

#### If the component is rendered by the following JSX expression
```
<ErrorCatcher>
  <TogglableParagraph text="Third!" />
</ErrorCatcher>
```
and the TogglableParagraph component throws an exception in it's render method, then:
- The ErrorCatcher will catch the exception, but will crash when rendering the error message. (solution)

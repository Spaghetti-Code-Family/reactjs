## Post Comment Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/post-comment/78815)

A page with comments consists of a list of comments and a form for posting a new comment. This is its HTML code:
```
<div>
  <form>
    <input type="text" />
    <input type="button" value="Post" />
  </form>
  <ul>
  </ul>
</div>
```
Write the CommentList component that renders previously shown page with comments and implements the following logic:

Each time a button with the value "Post" is clicked, a new <li> element should be added to the bottom of the ul element, containing the value of the text field from the form.
If the text field is empty, the comment should not be posted.
The value of the text field should be cleared after the comment has been posted.
For example, after the comment "test" has been posted, the list's content should look like this:
  
```
<li>test</li>
```

---
### Solution:
```
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const CommentList = (props) => {
  const [inputValue, setInputValue] = React.useState("");
  const [comments, setComments] = React.useState([]);
  const handleSubmit = (e) => {
    if (!inputValue) return;
    comments.push(inputValue);
    setInputValue("");
  };
  return (
    <div>
      <form>
        <input
          type="text"
          value={inputValue}
          onChange={(e) => setInputValue(e.target.value)}
        />
        <input type="button" value="Post" onClick={handleSubmit} />
      </form>
      <ul>
        {comments.map((item) => (
          <li>{item}</li>
        ))}
      </ul>
    </div>
  );
};

document.body.innerHTML = "<div id='root'> </div>";

const rootElement = document.getElementById("root");
ReactDOM.render(<CommentList />, rootElement);

var input = document.querySelector("input[type='text']");
input.value = "test";
input._valueTracker.setValue("");
input.dispatchEvent(new Event("change", { bubbles: true }));

document.querySelector("input[type='button']").click();
console.log(document.getElementsByTagName("ul")[0].innerHTML);
```

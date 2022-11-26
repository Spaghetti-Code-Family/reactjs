## Pet Form Coding Challenge Using React - [On TestDome](https://app.testdome.com/questions/react-js/pet-form/75325)

A pet talent show is using the following React form on its website:
```
const PetForm = (props) => {
  let [name, setName] = React.useState("");
  let [talents, setTalents] = React.useState("Enter talents here");
    
  return (
    <div>
      <p>Enter pet data below:</p>
      <label htmlFor="petName">Pet name:</label>
      <input id="petName" onChange={(event) => setName(event.target.value)}></input>
      { name.length > 5 ? "" : <p>Name should have more than 5 characters!</p> }
      
      <label htmlFor="petTalents">Pet talents:</label>
      <input id="petTalents" onChange={(event) => setTalents(event.target.value)} value={talents}></input>
      
      <button type="submit">Submit</button>
    </div>
  );
};
```
 Select all the correct answers.
 
---
### Solution:
- When the component is first rendered, the "Name should have more than 5 characters!" message will be visible.
- When the component is first rendered, petTalents input will contain "Enter talents here".

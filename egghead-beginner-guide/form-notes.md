# React Form Notes

## Forms
Form need an onSubmit handler. The
handler should prevent the default browser behavior.

```javascript
handleOnSubmit = (event) => {
  event.preventDefault();
  console.log({target: event.target.elements.firstName.value});
}

<form onSubmit={this.handleOnSubmit}>
```

## Form Elements
Form elements can be controlled or uncontrolled.

### Controlled Components
With controlled components form data is handled by a React Component

### Uncontrolled Components
With uncontrolled components data is handled by the dom itself. You would
do this using refs.

```javascript
handleSubmit(event) {
  alert('A name was submitted: ' + this.input.current.value);
  event.preventDefault();
}

render() {
  return (
    <form onSubmit={this.handleSubmit}>
      <label>
        Name:
        <input type="text" ref={this.input} />
      </label>
      <input type="submit" value="Submit" />
    </form>
  );
}
```



# React for Beginner Notes

Components are the main building blocks in React.

The aim of this document is to show the relationship between Components, Elements, JSX, and functions, and how they can be used to build apps.

## Elements
React Elements are similar to regular DOM elements. 

### Hello World - Plain Javascript
```javascript
const rootElement = document.getElementById("root");
const element = document.createElement("div");
element.textContent = "Hello World";
element.className = "containter";
rootElement.appendChild(element);
```

### Hello World - React.createElement
The 2nd parameter to createElement is and object containing the element props, which simply put are properties that you want on that element.

The third function parameter in the example below is a special kind of props called "children". These are children properties of the element you are creating.

```javascript
const rootElement = document.getElementById("root");
const element = React.createElement(
  'div',
  { className: 'container' },
  'Hello World'
);
ReactDOM.render(element, rootElement);
```

The above code could also be composed with the children props inside the object of the 2nd function parameter.

```javascript
const rootElement = document.getElementById("root");
const element = React.createElement(
  'div',
  {
    className: 'container',
    children: 'Hello World',
  },
);
ReactDOM.render(element, rootElement);
```
The children prop could also be an array of child props.

```javascript
const rootElement = document.getElementById("root");
const element = React.createElement(
  'div',
  {
    className: 'container',
    children: ['Hello World', 'Goodbye World'],
  },
);
ReactDOM.render(element, rootElement);
```

### JSX

While you could create an application with just React elements, composition would
not be optimal. JSX provides "syntactic sugar" to help you compose React elements. JSX is markup that will transpile into React elements.

```javascript
const rootElement = document.getElementById("root");
// JSX looks like markup in your code
const element = <div className="container">Hello World</div>;
ReactDOM.render(element, rootElement);
```

### JSX and Interpolation

JSX allows for interpolation of javascript with the use of curly braces: {}
```javascript
const rootElement = document.getElementById("root")
const content = 'Hello World';
const className = 'container';
const element = <div className={container}>{(() => content)()}</div>;
ReactDOM.render(element, rootElement);
```

### Interpolation of props using the spread operator

```javascript
const rootElement = document.getElementById("root")
const props = {
  children: 'Hello World',
  className: 'container',
}
const element = <div {...props}></div>;
ReactDOM.render(element, rootElement);
```

## Ordering of props, and how its like Object.assign

The order of props on the element is important. The ordering can be used to overwrite values, or provide default values. This works like Object.assign.

In this example props.className will get overwritten with "ps-container"

```javascript
const rootElement = document.getElementById("root")
const props = {
  children: 'Hello World',
  className: 'container',
}
const element = <div {...props} className='ps-container'></div>;
ReactDOM.render(element, rootElement);
```

## Components

The best way to create reusable code is with a function. React.createElment can take a function as parameter.

```javascript
const rootElement = document.getElementById("root");
const message = (props) => <div>{props.msg}</div>;
const element = (
  <div className="container">
    {message({msg: 'Hello World'})}
    {React.createElement(message, {msg: 'Goodbye World'})}
  </div>
);
ReactDOM.render(element, rootElement);
```

Take a look at the message function, and remember that JSX gets transpiled into a React element, which means message is just returning an element.

## Convert functions to JSX

If the method uses capitilization it can be used as an element in JSX. In the below
example we rename the message function to Message. This allows us to use it as the element <Message>

```javascript
const rootElement = document.getElementById("root");
  const Message = (props) => <div>{props.msg}</div>
  const element = (
    <div className="container">
      <Message msg="Hello World" />
      <Message msg="GoodBye World" />
    </div>
  );
  ReactDOM.render(element, rootElement);
```

## Revisting props.children

By taking the msg prop in the above example and converting it
to a child of the element we can use props.children for composition.

```javascript
    const rootElement = document.getElementById("root");
    const Message = (props) => <div>{props.children}</div>
    const element = (
      <div className="container">
        <Message>
          Hello World
        </Message>
        <Message>
          Goodbye World
          <Message>
            See you soon!
          </Message>
        </Message>
      </div>
    );
    ReactDOM.render(element, rootElement);
```

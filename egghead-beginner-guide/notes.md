# React for Beginner Notes

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
Hello world writting with React.createElement

```javascript
const rootElement = document.getElementById("root");
const element = React.createElement(
  'div',
  { className: 'container' },
  'Hello World'
);
ReactDOM.render(element, rootElement);
```

### JSX

While you could create applications with just React.createElement, composition would
not optimal. JSX provides "syntactic sugar" to help you compose React elements. Typically you would set up Babel and Webpack to transpile JSX into React elements.

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
const element = <div className="{container}">{(() => content)()}</div>;
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

The order of props on the element is important. The ordering can be used to overwrite or provide default values. This works like Object.assign.

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






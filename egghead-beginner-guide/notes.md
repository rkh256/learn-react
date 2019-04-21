# React for Beginner Notes

React Elements are just like DOM elements. They are created with the React.createElement Method.

The following javascript:
```javascript
const rootElement = document.getElementById("root");
const element = document.createElement("div");
element.textContent = "Hello World";
element.className = "containter";
rootElement.appendChild(element);
```
Can be written in react like so:

```javascript
const rootElement = document.getElementById("root");
const element = React.createElement(
  'div',
  { className: 'container' },
  'Hello World'
);
ReactDOM.render(element, rootElement);
```

While you could create applications with just React.createElement, composition would
not optimal, so JSX is introduced. JSX is markup in javscript to help you compose
React Elements. Typically you would set up Babel and Webpack to use JSX.

```javascript
const rootElement = document.getElementById("root");
const element = <div className="container">Hello World</div>;
ReactDOM.render(element, rootElement);
```

JSX allows for interpolation of javascript with the use of curly braces: {}
```javascript
const rootElement = document.getElementById("root")
const content = 'Hello World';
const className = 'container';
const element = <div className="{container}">{(() => content)()}</div>;
ReactDOM.render(element, rootElement);
```

You can interpolate props onto an element using an object and the spread operator:

```javascript
const rootElement = document.getElementById("root")
const props = {
  children: 'Hello World',
  className: 'container',
}
const element = <div {...props}></div>;
ReactDOM.render(element, rootElement);
```

The order of props on the element is important. The ordering can be used to overwrite or provide default values. This works exactly like Object.assign.

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






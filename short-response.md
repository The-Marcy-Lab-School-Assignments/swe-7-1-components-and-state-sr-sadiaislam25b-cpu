# Short Response: Intro to React, Components, and useState

Answer each question below. Write in complete sentences (3–5 per answer).

---

## Question 1 — Components and JSX

What is a React component, and what is JSX? Explain how JSX differs from plain HTML. Use a brief code example to support your answer.

**Your answer:**

--- A React component is a reusable piece of UI that returns what should be displayed on the screen. Components let you break a webpage into smaller, independent parts like buttons, forms, or sections. JSX is a syntax extension for JavaScript that lets you write HTML-like code inside JavaScript files. It looks like HTML but is actually transformed into JavaScript by React.

JSX differs from plain HTML because it supports JavaScript expressions and uses className instead of class

```jsx
const Greeting = () => {
  const name = "Sadia";
  return <h1>Hello, {name}!</h1>;
};
```

## Question 2 — The Build Step and Vite

A browser cannot run a `.jsx` file directly. Why not? Explain the role of a build step and what it means to "compile" code in simple terms.

**Your answer:**

---
A browser cannot run .jsx files directly because browsers only understand plain JavaScript, HTML, and CSS. JSX is not valid JavaScript, so it must be converted first. A build step is the process of transforming modern code (like JSX or ES6+) into code the browser can understand.

To “compile” code means to convert it from one format into another usable format. Tools like Vite or Babel take JSX and turn it into regular JavaScript. This allows React code to run properly in the browser. Without this step, the browser would not know how to interpret JSX syntax.

## Question 3 — useState

What does `useState` return, and what are the two things you get back from it? Describe how to use those values to render data and to update that data.

**Your answer:**

useState returns an array with two things: the current state value and a function  to update that value. For example, const [count, setCount] = useState(0) gives you count to display data in the component and setCount to change the data. When the state is updated using the update function, React automatically re-renders the component with the new value.

## Question 4 — Lifting State Up

What does it mean to "lift state up," and when is it necessary? Use a concrete example.

**Your answer:**

---"Lifting state up" means moving state from a child component to a shared parent component so multiple components can use it. This is necessary when two or more components need to access or update the same data. Instead of each component having its own separate state, the shared state is placed in the closest common parent.

For example, if a search bar and a results list both need the search input, the state should live in the parent component and be passed down as props. This ensures both components stay in sync with the same data.

## Question 5 — Bug Fix

The component below has a bug. When the user clicks "Add Cherries," the list never updates on screen. Identify what is wrong, write the corrected code, and explain **why** the original code fails in React.

```jsx
const ShoppingList = () => {
  const [items, setItems] = useState(['apples', 'bananas']);

  const addItem = () => {
    items.push('cherries');
    setItems(items);
  };

  return (
    <>
      <ul>
        {items.map((item, i) => <li key={i}>{item}</li>)}
      </ul>
      <button onClick={addItem}>Add Cherries</button>
    </>
  );
};
```

**Your answer:**

---
The bug is that the original code directly mutates the existing array with `items.push('cherries')` and then passes the same array reference to `setItems`. React detects state changes by comparing the old and new reference — since the array is the same object in memory, React sees no change and skips the re-render. To trigger a re-render, you must pass a new array to `setItems`. The fix is to use the spread operator to create a brand-new array that includes the existing items plus the new one.

```jsx
const ShoppingList = () => {
  const [items, setItems] = useState(['apples', 'bananas']);

  const addItem = () => {
    setItems([...items, 'cherries']);
  };

  return (
    <>
      <ul>
        {items.map((item, i) => <li key={i}>{item}</li>)}
      </ul>
      <button onClick={addItem}>Add Cherries</button>
    </>
  );
};
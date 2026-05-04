# Short Response: Intro to React, Components, and useState

Answer each question below. Write in complete sentences (3–5 per answer).

---

## Question 1 — Components and JSX

What is a React component, and what is JSX? Explain how JSX differs from plain HTML. Use a brief code example to support your answer.

**Your answer:**

---

## Question 2 — The Build Step and Vite

A browser cannot run a `.jsx` file directly. Why not? Explain the role of a build step and what it means to "compile" code in simple terms.

**Your answer:**

---

## Question 3 — useState

What does `useState` return, and what are the two things you get back from it? Describe how to use those values to render data and to update that data.

**Your answer:**

---

## Question 4 — Lifting State Up

What does it mean to "lift state up," and when is it necessary? Use a concrete example.

**Your answer:**

---

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

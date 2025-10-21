# 🧩 Lesson 5 – JavaScript Scope, DOM Manipulation & Events

## 🌟 Learning Objectives

By the end of this lesson, you should be able to:

* Understand **how variable scope works** (`var`, `let`, and `const`).
* **Access, create, and modify** HTML elements using the DOM.
* Use **events** (like `click`, `change`, etc.) to trigger JavaScript functions.

---

## 🧠 1. Variable Scope

### What is Scope?

Scope defines **where a variable lives** and **how long it exists**.

| Keyword | Scope Type      | Visible Where                           | Recommended? |
| ------- | --------------- | --------------------------------------- | ------------ |
| `var`   | Function-scoped | Anywhere inside the same function       | ❌ (Old JS)   |
| `let`   | Block-scoped    | Only inside `{ }` where it’s declared   | ✅            |
| `const` | Block-scoped    | Only inside `{ }`, cannot be reassigned | ✅            |

### Examples

```js
if (true) {
  var a = "I leak outside!";
  let b = "I stay inside!";
}
console.log(a); // ✅ works
console.log(b); // ❌ ReferenceError
```

```js
function demo() {
  let local = "Visible only inside function";
  console.log(local);
}
demo();
console.log(local); // ❌ ReferenceError
```

**Remember:**

* Variables declared with `let` and `const` **die when the block or function ends.**
* `var` variables **ignore block boundaries** (but still vanish when the function ends).

---

## 🗱 2. DOM Manipulation

### What is the DOM?

The **Document Object Model (DOM)** is how JavaScript sees and interacts with your webpage.

### Common Methods

| Task                 | Method                          | Example                                       |
| -------------------- | ------------------------------- | --------------------------------------------- |
| Select element by ID | `document.getElementById("id")` | `const div = document.getElementById("box");` |
| Create new element   | `document.createElement("p")`   | `const p = document.createElement("p");`      |
| Add text             | `.textContent` / `.innerHTML`   | `p.textContent = "Hello";`                    |
| Insert element       | `.appendChild()`                | `container.appendChild(p);`                   |
| Change style         | `.style.property = value`       | `p.style.color = "red";`                      |
| Add class            | `.classList.add()`              | `p.classList.add("highlight");`               |

### Example

```js
const container = document.getElementById("container");
const msg = document.createElement("p");
msg.textContent = "DOM created this!";
msg.style.color = "blue";
container.appendChild(msg);
```

🦩 *You can create, modify, or delete elements dynamically using these tools.*

---

## 🔱 3. Event-Driven JavaScript

### What is an Event?

An **event** is any user action — like clicking a button, typing in a box, or changing a dropdown.

### Common Events

| Event         | Trigger                  | Example                                          |
| ------------- | ------------------------ | ------------------------------------------------ |
| `onclick`     | Mouse click              | `<button onclick="sayHello()">Click me</button>` |
| `onchange`    | Input value changes      | `<input onchange="handleChange()">`              |
| `onmouseover` | Mouse moves over element | `<div onmouseover="highlight()">`                |
| `onkeydown`   | Keyboard key pressed     | `<input onkeydown="keyPressed()">`               |

### Example

```html
<button onclick="changeColor()">🎨 Change Color</button>
<input onchange="showInput(this.value)" placeholder="Type something" />
<div id="output"></div>
```

```js
function changeColor() {
  document.body.style.backgroundColor = "lightyellow";
}

function showInput(value) {
  const output = document.getElementById("output");
  output.textContent = "You typed: " + value;
}
```

Each event **calls a function**, and that function **manipulates the DOM** in response to user actions.

---

## 🧩 Key Takeaways

🔹 **Scope**

* `let` and `const` → block-scoped (preferred)
* `var` → function-scoped (avoid)
* Variables live only as long as their scope exists.

🔹 **DOM Manipulation**

* Create, style, and insert elements dynamically with JS.
* Use `.textContent`, `.innerHTML`, `.appendChild()`, `.style`, and `.classList`.

🔹 **Events**

* Use HTML event attributes (`onclick`, `onchange`, etc.) to trigger JS functions.
* Functions allow interactivity — the page responds when users act.

---

### 💪 Practice Idea

Build a small app that:

* Lets the user enter a number in a textbox.
* On `click`, checks if it’s even or odd.
* Displays the result dynamically using the DOM.

---

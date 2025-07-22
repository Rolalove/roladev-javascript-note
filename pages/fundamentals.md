---
layout: center
transition: slide-up
hideInToc: true
---

# Fundamentals

<div mt-2 />

- <a @click="$slidev.nav.go($nav.currentPage+1)">Variables</a>
- <a @click="$slidev.nav.go($nav.currentPage+4)">Data types</a>
- <a @click="$slidev.nav.go($nav.currentPage+7)">Interaction: `alert`, `prompt`, `confirm` | `console.log`</a>
- <a @click="$slidev.nav.go($nav.currentPage+9)">Type Conversions</a>
- <a @click="$slidev.nav.go($nav.currentPage+10)">Operators: Math, Comparison, Logical, Bitwise, Null Coalescing, Optional Chaining</a>
- <a @click="$slidev.nav.go($nav.currentPage+16)">Conditional Branching: if, '?', switch</a>
- <a @click="$slidev.nav.go($nav.currentPage+22)">Loops: while, for, for..in, for..of</a>
- <a @click="$slidev.nav.go($nav.currentPage+25)">Functions: Declaration, Arrow functions, Function Expressions</a>

---
hideInToc: true
---

# Variables?

- A variable is a container for a value. You can use >var, >let or >const

<div class='mt-6'></div>

#### `var`, `let`, and `const`: What's the Difference?
<div class='mt-6'></div>

| Keyword | Scope         | Reassignable | Redeclarable | Hoisted?                   | Use Case            |
|---------|---------------|--------------|---------------|-----------------------------|----------------------|
| `var`   | Function-wide | ✅ Yes       | ✅ Yes        | ✅ Yes (initialized as `undefined`) | Old JS (avoid now)   |
| `let`   | Block-scoped  | ✅ Yes       | ❌ No         | ✅ Yes (but not initialized) | Modern variable      |
| `const` | Block-scoped  | ❌ No        | ❌ No         | ✅ Yes (but not initialized) | For fixed values     |


---
hideInToc: true
---

### `var`

```js {monaco-run}{autorun: false}
var school = 'Edunity college';
var school = 'Edunity Frontend development college' ; // Redeclared — no error
console.log(school); // Edunity Frontend development college
```

### `let`
```js {monaco-run}{autorun: false}
let age = 30;
let age = 40; // ❌ SyntaxError: Identifier 'age' has already been declared
age = 35; // ✅ Reassignable

```
### `const`
```js
const pi = 3.14;
pi = 3.14159; // ❌ TypeError: Assignment to constant variable
const pi = 3.15; // ❌ SyntaxError: Identifier 'pi' has already been declared
```
---
hideInToc: true
---

###  Global Scope

Declared outside any function or block — accessible everywhere.

```js {monaco-run}
let siteName = "DevTrack";

function showName() {
  console.log(siteName); // ✅ Can access
}
showName();
```

###  Function Scope (with `var`)

Variables declared with `var` are scoped to the **entire function** — not just the block.

```js {monaco-run}
function greet() {
  var msg = "Hi!";
}
console.log(msg); // ❌ ReferenceError: msg is not defined
```

---

###  Block Scope (with `let` and `const`)

Variables declared with `let` or `const` exist only inside the block `{}` they're in.

```js {monaco-run}
if (true) {
  let x = 10;
  const y = 20;
}
console.log(x); // ❌ ReferenceError: x is not defined
console.log(y); // ❌ ReferenceError: y is not defined
```


### Quick Summary: Scope Types

| Scope Type     | Keyword(s)        | Accessible Outside? | Example Block      |
|----------------|-------------------|----------------------|--------------------|
| Global Scope   | `var`, `let`, `const` | ✅ Yes           | Declared outside   |
| Function Scope | `var`              | ❌ No               | Inside a function  |
| Block Scope    | `let`, `const`     | ❌ No               | `{}`, `if`, `loop` |


---
hideInToc: true
---

### 🔼 Hoisting in JavaScript

```js {monaco-run}
console.log(a); // ✅ undefined
var a = 5;

console.log(b); // ❌ ReferenceError
let b = 10;
```

---

::notes

🗣️ Let's talk about **hoisting** — one of the trickiest but most important concepts in JavaScript.

- JavaScript reads your code **before it runs**, and it "lifts" or **hoists** variable declarations to the top of their scope.
  
- With `var`, the variable is **hoisted and initialized** with `undefined`.  
  So when we `console.log(a)`, it doesn’t crash — we just get `undefined`.

- But `let` and `const` are different.  
  They are also hoisted, but they are **not initialized** right away.

- So if you try to use them before their actual declaration, JavaScript throws a **ReferenceError**.

This "weird" period — after hoisting but before initialization — is called the **Temporal Dead Zone**.

⚠️ Just remember:  
> `var` lets you access the variable too early (not ideal),  
> while `let` and `const` protect you from that mistake.

That’s why we prefer `let` and `const` — safer, less buggy!

::endnotes


---
hideInToc: true
---

# Variables Naming  convention 

| Rule   | Description                                                               | ❌ Bad Example     | ✅ Good Example         |
|--------|---------------------------------------------------------------------------|--------------------|-------------------------|
| 1      | The first character must not be a digit                                   | `1name`            | `name1`                 |
| 2      | Use <span style="color:red">CamelCase</span> for multiple words           | `my_variable_name` | `myVariableName`        |
| 3      | Don’t use reserved words (e.g., keywords like `let`, `var`)               | `let`, `class`     | `userClass`, `userRole` |
| 4      | Avoid short or unclear names unless context is clear                      | `a`, `b`, `x1`     | `score`, `userName`     |
| 5      | Names should be descriptive and concise                                   | `data1`, `tempVar` | `totalPrice`, `isLoggedIn` |
| 6      | Use underscore (`_`) only when following a specific style (not common in JS) | `total_value`    | `totalValue`            |

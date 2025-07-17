### **Comprehensive MCQ Review: Web Programming Technologies**

Practice these questions to challenge your in-depth understanding of web development concepts. For best results, attempt to answer them before checking the key.

---

### **Session 1: Architecture of the Web**

1.  **Which HTTP method is defined as "idempotent," meaning multiple identical requests should have the same effect as a single one?**
- [ ] `POST`
- [x] `PUT`
- [ ] `PATCH`
- [ ] `CONNECT`

**Answer:** ||(B) PUT is idempotent because it replaces the entire resource at a target URI. Sending the same PUT request multiple times will result in the same final state. POST is not idempotent as it typically creates a new resource with each call.||
<br>

2.  **A primary performance bottleneck that HTTP/1.1 suffers from, which HTTP/2 addresses with multiplexing, is called:**
- [ ] Connection flooding
- [x] Head-of-line blocking
- [ ] Packet fragmentation
- [ ] Server-side latency

**Answer:** ||(B) Head-of-line blocking in HTTP/1.1 means that if one resource is slow to load, it blocks all other resources from being requested over that single TCP connection. HTTP/2's multiplexing allows multiple requests and responses to be in-flight simultaneously over the same connection.||
<br>

3.  **In the context of the Domain Name System (DNS), what is the role of a Top-Level Domain (TLD) server?**
- [ ] It holds the final IP address for the requested domain name.
- [ ] It is the first point of contact for a recursive resolver and directs it to the appropriate TLD server.
- [x] It manages domains like `.com`, `.org`, and `.net` and directs queries to the correct authoritative name servers.
- [ ] It caches previous DNS lookups to speed up future requests for the same domain.

**Answer:** ||(C) The TLD server manages the last part of a domain name (like .com) and points the resolver to the authoritative name server that has the specific domain's information. The root server points to the TLD server.||
<br>

4.  **What is the primary difference between HTTP and HTTPS?**
- [ ] HTTPS uses a different set of methods (GET, POST) than HTTP.
- [ ] HTTPS is faster than HTTP due to better compression.
- [ ] HTTPS is the protocol for HTTP/2, while HTTP is for HTTP/1.1.
- [x] HTTPS encrypts the communication between the client and server using SSL/TLS, while HTTP sends data in plain text.

**Answer:** ||(D) The 'S' in HTTPS stands for Secure. It's the standard HTTP protocol layered on top of an encrypted SSL/TLS connection, protecting the data from eavesdropping and tampering.||
<br>

### **Sessions 2 & 3: HTML & CSS**

5.  **Which new HTML5 element is most appropriate for containing a blog post, a forum post, or a news story?**
- [ ] `<section>`
- [ ] `<div>`
- [x] `<article>`
- [ ] `<aside>`

**Answer:** ||(C) The \<article> element is semantically designed to represent a self-contained, complete piece of content that could be distributed independently from the rest of the site.||
<br>

6.  **In the CSS Box Model, which property is located between the `padding` and the `margin`?**
- [ ] `content`
- [x] `border`
- [ ] `outline`
- [ ] `display`

**Answer:** ||(B) The CSS Box Model order from inside out is: content -> padding -> border -> margin. The border lies between the padding and the margin.||
<br>

7.  **To apply a style to a single, unique element on a page, which CSS selector should you use?**
- [ ] A class selector (`.my-class`)
- [x] An ID selector (`#my-id`)
- [ ] A type selector (`p`)
- [ ] An attribute selector (`[type="text"]`)

**Answer:** ||(B) An ID is meant to be unique within a page. The ID selector provides a direct way to target that specific element and has high specificity.||
<br>

8.  **What is the difference between an inline and an external stylesheet?**
- [ ] Inline styles are written in a separate file, while external styles are in the `<head>` tag.
- [x] Inline styles are written directly in an element's `style` attribute, while external styles are in a separate `.css` file linked via the `<link>` tag.
- [ ] Inline styles have lower specificity than external styles.
- [ ] There is no difference; they are two names for the same thing.

**Answer:** ||(B) This describes the fundamental difference in how the CSS is applied. Inline styles are highly specific but not reusable, while external stylesheets are highly reusable and better for site-wide consistency.||
<br>

9.  **Which HTML tag is used to create a numbered list?**
- [ ] `<ul>`
- [ ] `<dl>`
- [ ] `<li>`
- [x] `<ol>`

**Answer:** ||(D) \<ol> stands for "ordered list" and creates a numbered list. \<ul> is an unordered (bulleted) list. \<li> is a list item used inside both \<ol> and \<ul>.||
<br>
### **Session 4: Responsive Web Design**

10. **What does the term "Responsive Web Design" primarily refer to?**
- [ ] Designing websites that respond quickly to user input.
- [ ] Building websites with a server that has a fast response time.
- [x] Creating a single web layout that adapts gracefully to different screen sizes and devices.
- [ ] Using JavaScript to make web pages interactive.

**Answer:** ||(C) Responsive Web Design uses techniques like flexible grids, fluid images, and CSS media queries to create a layout that provides an optimal viewing experience across desktops, tablets, and mobile phones.||
<br>

11. **In the Bootstrap grid system, how would you define a column that takes up half the width on medium screens and the full width on small screens?**
- [x] `class="col-md-6 col-sm-12"`
- [ ] `class="col-6-md col-12-sm"`
- [ ] `class="col-half-md col-full-sm"`
- [x] `class="col-sm-12 col-md-6"`

**Answer:** ||(A) Bootstrap uses a "mobile-first" approach, but the class syntax is col-{breakpoint}-{size}. col-md-6 means on medium screens and up, it takes 6 of 12 columns (half). col-sm-12 means on small screens and up, it takes 12 columns (full), but the md class will override it on medium screens. While D also works, A is a more common declaration order.||
<br>
12. **Which CSS feature is the foundation of responsive web design, allowing you to apply styles based on device characteristics like screen width?**
- [ ] Flexbox
- [ ] CSS Grid
- [x] Media Queries
- [ ] CSS Variables

**Answer:** ||(C) Media queries (@media (max-width: 600px) { ... }) are the core mechanism that allows a stylesheet to apply different rules based on the properties of the viewport or device.||
<br>

### **Sessions 5, 6 & 7: Core JavaScript**

13. **What is the output of `"1" + 2 + 3` versus `1 + 2 + "3"` in JavaScript?**
- [ ] "123" and "6"
- [ ] "15" and "33"
- [x] "123" and "33"
- [ ] "15" and "123"

**Answer:** ||(C) JavaScript evaluates left-to-right. "1" + 2 is a string concatenation to "12", then "12" + 3 is another concatenation to "123". In the second case, 1 + 2 is a numeric addition to 3, then 3 + "3" is a string concatenation to "33".||
<br>

14. **Which of the following is true about `let`, `var`, and `const`?**
- [ ] `var` is block-scoped.
- [ ] `let` can be redeclared in the same scope.
- [x] `const` variables cannot be reassigned after declaration.
- [ ] `let` and `const` are hoisted.

**Answer:** ||(C) A variable declared with const must be initialized at the time of declaration, and its value cannot be reassigned. let and const are block-scoped, while var is function-scoped.||
<br>

15. **What JavaScript concept allows an inner function to access variables from its outer (enclosing) function's scope, even after the outer function has returned?**
- [ ] Hoisting
- [ ] Prototype
- [ ] IIFE (Immediately Invoked Function Expression)
- [x] Closure

**Answer:** ||(D) This is the definition of a closure. The inner function maintains a reference to its lexical environment, "closing over" the variables from its parent scope.||
<br>

16. **How does JavaScript's inheritance model primarily work?**
- [ ] Through classical inheritance with classes.
- [x] Through prototypal inheritance, where objects inherit directly from other objects.
- [ ] Through multiple inheritance.
- [ ] JavaScript does not support inheritance.

**Answer:** ||(B) At its core, JavaScript uses prototypal inheritance. The class syntax introduced in ES6 is primarily syntactic sugar over this existing prototype-based mechanism.||
<br>

17. **What is the result of `0.1 + 0.2 === 0.3`?**
- [ ] true
- [x] false
- [ ] undefined
- [ ] It throws a syntax error.

**Answer:** ||(B) This is a classic example of floating-point precision issues in binary computing. The result of 0.1 + 0.2 is a number extremely close to 0.3, but not exactly 0.30000000000000004. Therefore, the strict equality check fails.||
<br>

### **Sessions 8 & 9: JavaScript DOM & Validation**

18. **The Document Object Model (DOM) represents a web page as a:**
- [ ] Flat list of elements.
- [ ] String of HTML text.
- [x] Tree-like structure of nodes.
- [ ] JSON object.

**Answer:** ||(C) The DOM represents the logical structure of an HTML or XML document as a tree of nodes, where each element, attribute, and piece of text is a node. This tree structure allows for easy traversal and manipulation with JavaScript.||
<br>

19. **What is the difference between "event capturing" and "event bubbling"?**
- [ ] They are the same thing.
- [x] Capturing is when the event travels from the `window` down to the target element; bubbling is when it travels back up from the target to the `window`.
- [ ] Bubbling is when the event travels from the `window` down to the target; capturing is when it travels back up.
- [ ] Capturing is for mouse events, and bubbling is for keyboard events.

**Answer:** ||(B) The standard W3C event model has three phases: the capture phase (downwards), the target phase (at the element), and the bubble phase (upwards). By default, most event listeners are attached to the bubbling phase.||
<br>

20. **Which JavaScript method is used to stop an event from propagating further up the DOM tree?**
- [ ] `event.preventDefault()`
- [x] `event.stopPropagation()`
- [ ] `event.stopImmediatePropagation()`
- [ ] `event.end()`

**Answer:** ||(B) event.stopPropagation() prevents the event from continuing its journey through the capture or bubbling phases. preventDefault() is used to stop the browser's default action for an event, like a form submitting.||
<br>

21. **A regular expression `^d` would match what in a string?**
- [ ] The letter 'd' anywhere in the string.
- [ ] Any single digit character.
- [x] The letter 'd' only if it is the first character of the string.
- [ ] The letter 'd' only if it is the last character of the string.

**Answer:** ||(C) The caret ^ is an anchor in a regular expression that asserts the position at the start of the string.||
<br>

### **Sessions 10, 11 & 12: JSON, AJAX & Axios**

22. **Which of the following is an invalid JSON syntax?**
- [ ] `{ "name": "John", "age": 30 }`
- [x] `{ 'name': 'John' }`
- [ ] `{ "tags": ["js", "json"] }`
- [x] `{ "name": "John", }`

**Answer:** ||(B) JSON syntax rules require that all keys (property names) must be enclosed in double quotes. Single quotes are not allowed. A trailing comma (D) is also invalid in strict JSON.||
<br>

23. **What does AJAX stand for?**
- [ ] Action-JavaScript-And-XML
- [x] Asynchronous JavaScript and XML
- [ ] Automated JavaScript and XHTML
- [ ] Active Java and XML

**Answer:** ||(B) AJAX is a technique for making asynchronous HTTP requests from a web page to a server in the background, allowing for dynamic updates without a full page reload.||
<br>

24. **What is the primary advantage of using a Promise-based HTTP client like Axios over the traditional `XMLHttpRequest` with callbacks?**
- [ ] Axios requests are always faster.
- [x] It avoids "Callback Hell" and provides a cleaner, chainable syntax for handling asynchronous operations.
- [ ] It is the only way to make `POST` requests.
- [ ] It automatically parses all data formats.

**Answer:** ||(B) Promises provide a robust way to manage asynchronous operations, with .then() for success cases and .catch() for errors, making the code much easier to read and maintain than deeply nested callbacks.||
<br>

25. **The `JSON.parse()` method in JavaScript is used to:**
- [ ] Convert a JavaScript object into a JSON string.
- [x] Convert a JSON formatted string into a JavaScript object.
- [ ] Check if a string is valid JSON.
- [ ] Send JSON data to a server.

**Answer:** ||(B) JSON.parse() takes a string containing JSON data and transforms it into a native JavaScript object that you can interact with. JSON.stringify() does the opposite.||
<br>

### **Sessions 13, 14 & 15: Node.js Asynchronous Programming**

26. **What is the Node.js event loop?**
- [ ] A `for` loop that runs in every Node.js application.
- [ ] A security feature that loops through incoming requests.
- [x] A mechanism that allows Node.js to perform non-blocking I/O operations by offloading operations and processing their results on a single thread.
- [ ] A tool for debugging loops in JavaScript.

**Answer:** ||(C) The event loop is the heart of Node's concurrency model. It allows a single thread to handle many I/O operations efficiently by processing callbacks from a queue as the operations complete.||
<br>

27. **What is the purpose of `async/await` in JavaScript?**
- [ ] It makes asynchronous functions run synchronously.
- [ ] It is a replacement for `try...catch` blocks.
- [x] It is syntactic sugar built on top of Promises to make asynchronous code look and feel more like synchronous code.
- [ ] It is a way to create new threads.

**Answer:** ||(C) async/await provides a cleaner syntax for working with Promises. await pauses the execution of an async function until a Promise settles, making complex asynchronous workflows easier to write and read.||
<br>

28. **In Node.js, `fs.readFile()` is asynchronous, while `fs.readFileSync()` is synchronous. When would it be appropriate to use the `Sync` version?**
- [ ] When handling a web request in an Express server.
- [ ] In any high-concurrency application.
- [x] During the initial startup of a script, for example, to load a configuration file before the server starts.
- [ ] It should never be used.

**Answer:** ||(C) Synchronous, blocking functions should be avoided in the main part of a server's request-response cycle because they block the event loop. However, they are acceptable for one-time initialization tasks when an application first starts.||
<br>

29. **What does `setTimeout(myFunc, 1000)` do?**
- [ ] It pauses the entire program for 1000 milliseconds.
- [ ] It guarantees that `myFunc` will be executed in exactly 1000 milliseconds.
- [x] It places `myFunc` onto a queue to be executed after a minimum delay of 1000 milliseconds, once the call stack is clear.
- [ ] It calls `myFunc` 1000 times.

**Answer:** ||(C) Timers in JavaScript are not guarantees. setTimeout tells the runtime environment to execute the function after the specified delay has passed and the event loop is free to run it.||
<br>

### **Sessions 16, 17 & 18: Node.js Modules & Express**

30. **In a Node.js module, what is the purpose of `module.exports`?**
- [ ] To import other modules.
- [x] To define the variables and functions that are made available to other modules that `require()` this file.
- [ ] To execute the module's code.
- [ ] To install the module using npm.

**Answer:** ||(B) module.exports is the object that is returned as the result of a require() call. By attaching functions or values to this object, a module exposes its public API.||
<br>

31. **What is Express.js?**
- [ ] A JavaScript runtime environment.
- [ ] A database for Node.js applications.
- [ ] A front-end framework for building user interfaces.
- [x] A minimal and flexible web application framework for Node.js.

**Answer:** ||(D) Express provides a robust set of features for web and mobile applications, such as routing, middleware, and request/response handling, built on top of Node.js's core http module.||
<br>

32. **In an Express route handler `(req, res, next)`, what is the `req` object?**
- [x] An object containing information about the HTTP request, such as parameters, headers, and body.
- [ ] An object used to send a response back to the client.
- [ ] A function to call the next middleware.
- [ ] A reference to the Express application itself.

**Answer:** ||(A) The req (request) object holds all the information about the incoming request that the server needs to process it.||
<br>

33. **What is the purpose of `npm install express --save`?**
- [ ] To install Express globally on the machine.
- [ ] To install Express as a development-only dependency.
- [x] To install Express locally for the project and add it to the `dependencies` list in `package.json`.
- [ ] To save the Express code into a file.

**Answer:** ||(C) This is the standard command for adding a new package to a project. The --save flag (which is the default behavior in modern npm) ensures the dependency is recorded in package.json.||
<br>

### **Sessions 19-28: React & Redux**

34. **In React, what is the difference between "state" and "props"?**
- [ ] They are the same thing.
- [ ] State is passed from parent to child, while props are managed within the component.
- [x] Props are passed from parent to child (read-only), while state is managed within the component itself (mutable).
- [ ] State is for class components, while props are for functional components.

**Answer:** ||(C) This is the fundamental distinction. Props are for external configuration passed down the component tree. State is for internal, mutable data that a component owns and manages, and changes to state trigger a re-render.||
<br>

35. **Which lifecycle method in a class component is the correct place to fetch data from an API?**
- [ ] `render()`
- [ ] `constructor()`
- [x] `componentDidMount()`
- [ ] `componentWillUnmount()`

**Answer:** ||(C) componentDidMount() runs after the component has been rendered to the DOM for the first time. This is the perfect place to initiate side effects like API calls without blocking the initial render.||
<br>

36. **What does "lifting state up" in React mean?**
- [x] Moving state from a child component to its closest common ancestor.
- [ ] Storing state in the global `window` object.
- [ ] Using the Context API instead of local state.
- [ ] Promoting a prop to be a state variable.

**Answer:** ||(A) When multiple components need to share and reflect the same data, the shared state should be moved up to their common parent. The parent then passes the state and functions to update it down to the children as props.||
<br>

37. **In Redux, what must a reducer function be?**
- [ ] An asynchronous function.
- [ ] A class with a `reduce` method.
- [x] A pure function.
- [ ] A function that can mutate the state directly.

**Answer:** ||(C) Reducers must be pure functions. Given the same state and action, they must always return the same new state object and must not have any side effects (like API calls or mutating their arguments).||
<br>

38. **What is the role of an "action" in Redux?**
- [ ] It is a function that directly changes the state.
- [x] It is a plain JavaScript object that describes an event that happened in the application.
- [ ] It connects a React component to the Redux store.
- [ ] It is the same as a Redux store.

**Answer:** ||(B) An action is a payload of information that sends data from your application to your store. It is the only source of information for the store. You send them to the store using store.dispatch().||
<br>

39. **React's `useEffect` hook can return a function. What is the purpose of this returned function?**
- [ ] To update the component's state.
- [x] To perform a cleanup action when the component unmounts or before the effect runs again.
- [ ] To get a reference to a DOM element.
- [ ] To indicate that the effect has completed successfully.

**Answer:** ||(B) The cleanup function is the useEffect equivalent of the componentWillUnmount lifecycle method. It's used to clean up subscriptions, timers, or other resources to prevent memory leaks.||
<br>

40. **What problem does the React Context API primarily solve?**
- [ ] The problem of managing component state.
- [ ] The problem of making API calls.
- [x] The problem of "prop drilling," where props have to be passed down through many levels of intermediate components.
- [ ] The problem of inefficient re-rendering.

**Answer:** ||(C) Context provides a way to share values like the current theme or authenticated user down a component tree without having to explicitly pass a prop through every single level.||
<br>

### **Topic 6: Final Review Questions**

41. **What is the purpose of a `package-lock.json` file?**
- [ ] It serves the same purpose as `package.json` but for development dependencies.
- [ ] It is a human-readable list of all packages in the project.
- [x] It locks the specific versions of all dependencies and sub-dependencies to ensure consistent installations across different environments.
- [ ] It contains scripts for locking and unlocking packages.
<br>

42. **In jQuery, what does the `$` symbol typically represent?**
- [ ] A variable for storing currency values.
- [x] An alias for the `jQuery` function, used to select elements and create jQuery objects.
- [ ] A symbol to indicate the end of a statement.
- [ ] A function for making asynchronous requests.
<br>

43. **What is a "callback function" in JavaScript?**
- [ ] A function that is called immediately when it is defined.
- [ ] A function that calls another function.
- [x] A function that is passed as an argument to another function, to be executed later.
- [ ] A function that belongs to an object.
<br>

44. **What is the `Node.js REPL`?**
- [ ] A tool for managing project dependencies.
- [x] A protocol for real-time client-server communication.
- [ ] An interactive command-line shell for executing JavaScript code.
- [ ] A module for reading and evaluating files.
<br>

45. **Which is a core principle of Redux?**
- [ ] State is mutable and can be changed by any component.
- [x] The entire application state is stored in a single immutable state tree (single source of truth).
- [ ] Each component manages its own separate Redux store.
- [ ] Actions are functions that directly modify the state.
<br>

46. **What does the "Composition vs. Inheritance" principle in React suggest?**
- [ ] Components should inherit styles from their parents.
- [ ] Complex components should be built by inheriting from simpler base components.
- [x] Code reuse should be achieved by nesting components and passing props (composition) rather than by using class inheritance.
- [ ] Functional components use composition, while class components use inheritance.
<br>

47. **What is an "Error Boundary" in React?**
- [ ] A `try...catch` block used inside the `render` method.
- [x] A special component that catches JavaScript errors anywhere in its child component tree, logs those errors, and displays a fallback UI.
- [ ] A browser feature for handling React-specific errors.
- [ ] A Redux middleware for catching errors in actions.
<br>

48. **In Axios, what is an "interceptor"?**
- [ ] A function that catches errors in HTTP responses.
- [x] A function that can intercept and modify requests before they are sent or responses before they are handled by `.then()` or `.catch()`.
- [ ] A security feature to prevent cross-site scripting.
- [ ] A way to cancel an ongoing HTTP request.
<br>

49. **What does the "Lifting State Up" pattern help with?**
- [ ] Improving the performance of a component's render method.
- [ ] Making a component's state global to the entire application.
- [x] Sharing and synchronizing state between sibling components.
- [ ] Storing component state in the browser's local storage.
<br>

50. **In Node.js, `fs` and `http` are examples of:**
- [ ] Global packages installed via npm.
- [ ] Third-party libraries.
- [x] Core modules that are built into the Node.js runtime.
- [ ] JavaScript language keywords.
<br>

**Answer Key (Topic 6)**
41. C: ||While package.json might specify a dependency as ^1.2.3 (meaning any version from 1.2.3 up to, but not including, 2.0.0), package-lock.json records the exact version (1.2.5) that was installed. This ensures that every developer on a team gets the exact same set of dependencies.||
42. B: ||The $ is a shorthand alias for the jQuery object. It's used as a function to select DOM elements (e.g., $('p')) and wrap them in a jQuery object to which you can chain jQuery methods.||
43. C: ||This is the definition of a callback. It's a fundamental pattern for handling asynchronous operations in JavaScript, where you provide a function to be executed once an operation (like an API call or a timer) completes.||
44. C: ||REPL stands for Read-Eval-Print Loop. Typing node in your terminal starts the REPL, which is a simple, interactive environment for quickly testing out JavaScript code snippets and exploring Node.js features.||
45. B: ||This is the first principle of Redux. Having a single source of truth makes the application state easier to debug, inspect, and reason about.||
46. C: ||React's component model strongly favors composition. Instead of creating a SpecialButton that extends Button, you would create a generic Button component and pass it special content or props to customize it.||
47. B: ||Error Boundaries are React components that implement either componentDidCatch() or the static getDerivedStateFromError() method. They act like a catch block for their child components, preventing a UI error in one part of the app from crashing the entire application.||
48. B: ||Interceptors are a powerful feature of Axios. A request interceptor can be used to automatically add an authentication token to every outgoing request. A response interceptor can be used to handle errors globally or to transform response data.||
49. C: ||When two sibling components need to share the same state, that state should be "lifted up" to their closest common parent. The parent then manages the state and passes it down to both children via props, ensuring they are always in sync.||
50. C: ||fs (File System), http, path, and os are core modules provided as part of the Node.js installation. They do not need to be installed via npm and can be used directly with require('fs').||
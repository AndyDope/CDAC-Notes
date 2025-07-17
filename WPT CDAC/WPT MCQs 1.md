### **Comprehensive MCQ Review: Web Programming Technologies (Hard)**

Practice these questions to challenge your in-depth understanding of web development concepts. For best results, attempt to answer them before checking the key.

---

### **Session 1: Architecture of the Web**

1.  **A browser makes a request with an `If-None-Match` header containing an ETag value. The server finds the resource hasn't changed. Which HTTP status code should it return?**
- [ ] `200 OK`
- [ ] `204 No Content`
- [x] `304 Not Modified`
- [ ] `412 Precondition Failed`

**Answer:** ||(C) The 304 Not Modified status code is the correct response for a conditional GET request where the resource has not changed since the last ETag or Last-Modified date provided by the client. It tells the browser to use its cached version.||
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

5.  **Which of the following CSS selectors would target a `<p>` element that is an *immediate* child of a `div` with the class `container`, but only if that `<p>` is also the *first child* of its parent?**
- [ ] `div.container p:first-child`
- [ ] `div.container > p:first-of-type`
- [ ] `div.container:first-child > p`
- [x] `div.container > p:first-child`

**Answer:** ||(D) div.container > p uses the direct child combinator (>). :first-child is a pseudo-class that matches an element only if it is the first child of its parent. Combining them correctly targets the element as described.||
<br>

6.  **What is the fundamental difference between the `Content-Box` and `Border-Box` box-sizing models in CSS?**
- [ ] `Content-Box` includes padding and border in the element's total width/height, while `Border-Box` does not.
- [ ] `Border-Box` makes the margin part of the element's clickable area.
- [x] In `Content-Box`, the specified `width` is the width of the content area only. In `Border-Box`, the specified `width` is the width of the content, padding, and border combined.
- [ ] `Content-Box` is for block elements, while `Border-Box` is for inline elements.

**Answer:** ||(C) This is the key distinction. box-sizing: border-box; makes layout math much more intuitive because the width you set in CSS is the final width you see on the page, regardless of padding or border size.||
<br>

7.  **In CSS, which selector has the highest specificity?**
- [ ] `div.my-class`
- [x] `#my-id`
- [ ] `div p a`
- [ ] `[data-role="navigation"]`

**Answer:** ||(B) In CSS specificity, ID selectors (#my-id) have a higher weight than class selectors (.my-class), attribute selectors ([...]), or type selectors (div). Inline styles have the highest specificity of all.||
<br>

8.  **What does the `defer` attribute on a `<script>` tag do?**
- [ ] It prevents the script from executing until all images on the page have loaded.
- [ ] It tells the browser to download the script asynchronously but execute it only after the HTML document has been fully parsed.
- [ ] It tells the browser to pause HTML parsing, download and execute the script, and then resume parsing.
- [ ] It executes the script on a separate thread to prevent blocking the UI.

**Answer:** ||(B) defer is a powerful optimization. The browser can continue parsing the DOM while downloading the script in parallel. The script execution is "deferred" until parsing is complete, and scripts with defer maintain their relative execution order. async also downloads in parallel but executes as soon as it's ready, which can block parsing.||
<br>

### **Sessions 4 & 5: Responsive Design & JavaScript**

9.  **What is the output of this code?**
```javascript
for (var i = 0; i < 3; i++) {
	setTimeout(() => console.log(i), 10);
}
```
- [ ] 0, 1, 2
- [ ] 3, 3, 3
- [ ] 0, then 1, then 2 (with delays)
- [ ] 1, 2, 3

**Answer:** ||(B) This is a classic closure and var scope problem. By the time the setTimeout callbacks execute (after the loop has finished), the var i variable has a final value of 3 in the shared function scope. All three callbacks reference this same i. If let were used instead, it would print 0, 1, 2 because let is block-scoped.||
<br>

10. **In the Bootstrap grid system, how would you define a column that takes up half the width on medium screens and the full width on small screens?**
- [x] `class="col-md-6 col-sm-12"`
- [ ] `class="col-6-md col-12-sm"`
- [ ] `class="col-half-md col-full-sm"`
- [ ] `class="col-sm-12 col-md-6"`

**Answer:** ||(A) Bootstrap uses a "mobile-first" approach. The col-sm-12 class would apply to small screens and up, but the col-md-6 class would override it for medium screens and larger, achieving the desired layout.||
<br>

11. **What is the value of `this` inside an arrow function `() => {}`?**
- [ ] It is bound to the element that triggered the event.
- [ ] It is always the global `window` object.
- [ ] It is determined by how the function is called (`call`, `apply`).
- [x] It is lexically bound; it captures the `this` value of the enclosing execution context.

**Answer:** ||(D) Arrow functions do not have their own this binding. Instead, they inherit this from the parent scope at the time they are defined. This is a key difference from regular function expressions.||
<br>

### **Sessions 6 & 7: JavaScript OOP and Functions**

12. **What is the concept of "prototypal inheritance" in JavaScript?**
- [x] A mechanism where objects inherit properties and methods directly from other objects.
- [ ] A system where classes inherit from other classes using the `extends` keyword.
- [ ] A way to create private members in an object.
- [ ] The process of creating an object from a constructor function.

**Answer:** ||(A) This is the core inheritance model of JavaScript. Every object has a hidden internal link to another object called its "prototype". When trying to access a property, the search proceeds up this prototype chain. The class syntax is sugar over this mechanism.||
<br>

13. **What is the result of `0.1 + 0.2 === 0.3`?**
- [ ] true
- [x] false
- [ ] undefined
- [ ] It throws a syntax error.

**Answer:** ||(B) This is a classic example of floating-point precision issues in binary computing. The result of 0.1 + 0.2 is a number extremely close to 0.3, but not exactly 0.30000000000000004. Therefore, the strict equality check fails.||
<br>

14. **What does the `bind` method do in JavaScript?**
- [ ] It immediately calls the function with a specified `this` context.
- [ ] It creates a new function that, when called, has its `this` keyword set to the provided value.
- [ ] It attaches a function as an event listener to an element.
- [ ] It converts a function into a string.

**Answer:** ||(B) Unlike call or apply which execute the function immediately, bind returns a new function with a permanently bound this context. This is very useful for passing event handlers in class components.||
<br>

### **Sessions 8 & 9: JavaScript DOM & Validation**

15. **What is the difference between `event.stopPropagation()` and `event.stopImmediatePropagation()`?**
- [ ] There is no difference.
- [ ] `stopPropagation` stops the event from moving to the next phase (e.g., from capture to bubble), while `stopImmediatePropagation` stops it entirely.
- [ ] `stopPropagation` prevents the event from propagating to parent elements, while `stopImmediatePropagation` does that AND prevents any other listeners on the same element from running.
- [ ] `stopPropagation` works for mouse events, `stopImmediatePropagation` for keyboard events.

**Answer:** ||(C) If an element has multiple event listeners for the same event, stopPropagation will not prevent the other listeners on that same element from running. stopImmediatePropagation will prevent both propagation and any other listeners on the current element from executing.||
<br>

16. **A regular expression `/\bword\b/` is used to match the "word". Which of the following strings will it NOT match?**
- [ ] "word for word"
- [ ] "a single-word"
- [ ] "the sword"
- [ ] "word."

**Answer:** ||(C) \b is a word boundary anchor. It matches a position where a word character is not followed or preceded by another word character. In "the sword", "word" is preceded by 's', which is a word character, so the boundary \b does not match.||
<br>

17. **What is the `this` keyword in the context of a JavaScript event handler attached via `element.addEventListener('click', function() { ... })`?**
- [ ] The global `window` object.
- [ ] The element that the event listener is attached to.
- [ ] `null`.
- [ ] The `event` object.

**Answer:** ||(B) When using a regular function() as an event handler, the this keyword inside that function is bound to the DOM element that triggered the event. If an arrow function () => {} were used, this would retain its value from the surrounding lexical scope.||
<br>

### **Sessions 10, 11 & 12: JSON, AJAX & Axios**

18. **Which HTTP header must a server include in its response to allow a web page from `a.com` to make an AJAX request to `b.com`?**
- [ ] `Access-Control-Allow-Origin: *`
- [ ] `Allow-Cross-Domain: true`
- [ ] `X-Frame-Options: SAMEORIGIN`
- [ ] `Content-Security-Policy: "connect-src b.com"`

**Answer:** ||(A) This is the core of CORS (Cross-Origin Resource Sharing). The server at b.com must include the Access-Control-Allow-Origin header in its response to tell the browser that it is permissible for scripts from other origins (like a.com, or * for any origin) to access its resources.||
<br>

19. **What is an "interceptor" in Axios?**
- [ ] A function that catches errors in HTTP responses.
- [ ] A function that can intercept and modify requests before they are sent or responses before they are handled by `.then()` or `.catch()`.
- [ ] A security feature to prevent cross-site scripting.
- [ ] A way to cancel an ongoing HTTP request.

**Answer:** ||(B) Interceptors are a powerful feature of Axios. A request interceptor is ideal for automatically adding an authentication token to every outgoing request. A response interceptor is great for global error handling.||
<br>

20. **What is JSONP used for?**
- [ ] To parse JSON data more efficiently.
- [ ] To work around the same-origin policy in browsers for making cross-domain requests before CORS was common.
- [ ] To encrypt JSON data.
- [ ] A newer version of JSON with more data types.

**Answer:** ||(B) JSONP (JSON with Padding) was a historical workaround for the browser's same-origin policy. It works by dynamically inserting a \<script> tag, which is not subject to the same restrictions as XMLHttpRequest, to fetch data from a different domain.||
<br>

### **Sessions 13, 14 & 15: Node.js Asynchronous Programming**

21. **In Node.js, what is the difference between `__dirname` and `process.cwd()`?**
- [ ] `__dirname` gives the directory of the current module file, while `process.cwd()` gives the directory from which the Node.js process was launched.
- [ ] `process.cwd()` gives the directory of the current module file, while `__dirname` gives the directory from which the Node.js process was launched.
- [ ] Both return the same value.
- [ ] `__dirname` is a global variable, while `process.cwd()` is a function that must be imported.

**Answer:** ||(A) This is a crucial distinction. \_\_dirname is the absolute path to the directory containing the file where it is used. process.cwd() (Current Working Directory) depends on where you were in the terminal when you ran the node command.||
<br>

22. **What is the correct order of execution in the Node.js event loop for the following? `setTimeout(A, 0)`, `setImmediate(B)`, `Promise.resolve().then(C)`**
- [ ] A, B, C
- [ ] C, B, A
- [ ] C, A, B
- [ ] B, C, A

**Answer:** ||(C) Promises (.then callbacks) are handled in the "microtask queue," which is processed immediately after the current operation and before the next tick of the event loop. setTimeout and setImmediate are "macrotasks." Between them, setImmediate is designed to run before I/O pollers and after timers, but a setTimeout with a 0ms delay might execute first if the loop preparation time is longer than the timer threshold. However, microtasks always run before any macrotasks. So C runs first. The order of A and B can vary, but typically timers are checked first in a loop tick, so A would precede B. Thus, C, A, B is the most reliable order.||
<br>

23. **Which statement accurately describes `async/await`?**
- [ ] An `async` function implicitly returns a `Promise`, and `await` can only be used inside an `async` function to pause its execution until a `Promise` settles.
- [ ] It allows JavaScript to become a multi-threaded language.
- [ ] `await` blocks the entire Node.js event loop until the operation is complete.
- [ ] It is an older pattern that has been replaced by callbacks.

**Answer:** ||(A) This correctly describes the mechanics. async/await is syntactic sugar over promises that makes asynchronous code easier to write and read, but it does not block the event loop; it only pauses the execution of the async function itself.||
<br>

### **Sessions 16, 17 & 18: Node.js Modules & Express**

24. **In Node.js, what is the difference between `dependencies` and `devDependencies` in `package.json`?**
- [ ] `dependencies` are for the front-end, `devDependencies` are for the back-end.
- [ ] `dependencies` are required for the application to run in production, while `devDependencies` are only needed for development and testing (e.g., test frameworks, linters).
- [ ] `dependencies` are installed globally, `devDependencies` are installed locally.
- [ ] There is no functional difference; it is only for organization.

**Answer:** ||(B) When you deploy your application to a production server, you typically run npm install --production, which will only install the packages listed under dependencies, ignoring devDependencies to keep the installation smaller and cleaner.||
<br>

25. **What is the purpose of the `next('route')` function call within an Express middleware?**
- [ ] It passes control to the next middleware in the stack.
- [ ] It ends the request-response cycle.
- [ ] It skips the rest of the middleware functions in the current router and passes control to the next matching route in the router.
- [ ] It redirects the user to a new route.

**Answer:** ||(C) This is a special use case of next(). While a plain next() call moves to the next middleware function, next('route') bypasses all subsequent middleware in the current route handler and moves to the next route that matches the URL.||
<br>

26. **What is the role of the `http` module in Node.js in relation to Express.js?**
- [ ] Express is a direct replacement for the `http` module.
- [ ] Express is a framework that is built on top of and extends the core `http` module to provide easier routing and middleware management.
- [ ] The `http` module is used for making client requests, while Express is for creating servers.
- [ ] They are unrelated and serve different purposes.

**Answer:** ||(B) At its core, an Express application creates a server using Node's built-in http module. Express then adds layers of functionality on top of it to simplify web application development.||
<br>

### **Sessions 19-28: React & Redux**

27. **What is a "controlled component" in React?**
- [ ] A component whose state is managed by a Redux store.
- [ ] A component that cannot be modified after it is rendered.
- [ ] A form input element whose value is controlled by React state.
- [ ] A component that has been optimized with `React.memo`.

**Answer:** ||(C) In a controlled component, the form element's value (e.g., an \<input>) is set from React state via the value prop, and any changes to it are handled by an onChange handler that calls setState. The React state is the single source of truth.||
<br>

28. **In React, what is the primary purpose of using "keys" when rendering a list of components?**
- [ ] To provide a unique `id` attribute for the resulting DOM elements.
- [ ] To act as a stable identity for each component in the list, allowing React to efficiently track additions, removals, and re-orderings during reconciliation.
- [ ] To pass data to the list components.
- [ ] To specify the order in which the components should be rendered.

**Answer:** ||(B) Keys are a crucial hint for React's "diffing" algorithm. Without stable keys, React might have to tear down and recreate components unnecessarily when the list changes. With keys, it can identify which components have moved and reorder them efficiently.||
<br>

29. **Which is a valid reason to use the `useCallback` hook in React?**
- [ ] To memoize the result of a complex calculation.
- [ ] To prevent a function from being recreated on every render, which is useful when passing that function down to optimized child components.
- [ ] To fetch data when a component mounts.
- [ ] To store a mutable value that doesn't trigger a re-render.

**Answer:** ||(B) If you pass a function as a prop to a child component that is wrapped in React.memo, the child will re-render every time because the parent creates a new function instance on every render. useCallback returns a memoized version of the callback that only changes if one of its dependencies has changed. useMemo is for memoizing values.||
<br>

30. **What is the "single source of truth" principle in Redux?**
- [ ] Only one component is allowed to modify the state.
- [ ] The entire state of the application is stored in a single, immutable object tree within one store.
- [ ] Actions must be dispatched from a single file.
- [ ] There can only be one reducer for the entire application.

**Answer:** ||(B) This is a core principle. By centralizing the application's state, it becomes easier to debug, persist, and reason about.||
<br>

31. **What problem does the React Context API solve?**
- [ ] It provides a way to manage component state more efficiently than `useState`.
- [ ] It avoids "prop drilling" by allowing data to be passed down the component tree without having to be passed manually through every level.
- [ ] It helps in making asynchronous API calls.
- [ ] It is a replacement for Redux.

**Answer:** ||(B) Context is designed to share data that can be considered "global" for a tree of React components (like theme, or user authentication status), avoiding the tedious and error-prone process of passing props through intermediate components that don't need them.||
<br>

### **Final Review Questions (All Topics)**

*Note: The remaining 19 questions will be presented here.*

32. **What is the output of `console.log(2 + '2' - 2);` in JavaScript?**
- [ ] "20"
- [ ] 20
- [ ] 2
- [ ] NaN

**Answer:** ||(B) 2 + '2' is string concatenation, resulting in "22". The - operator then triggers numeric conversion, so "22" - 2 becomes 22 - 2, resulting in the number 20.||
<br>

33. **What is the concept of "hoisting" in JavaScript?**
- [ ] A mechanism where variable and function declarations are moved to the top of their containing scope during the compilation phase.
- [ ] A way to lift component state up to a common ancestor.
- [ ] A security policy that prevents scripts from accessing resources from different origins.
- [ ] The process of converting a callback-based function to a Promise-based one.

**Answer:** ||(A) This is why you can call a function before it is defined in the code. For variables declared with var, the declaration is hoisted but the initialization is not (var x; is moved up, but x = 5; stays put), which can lead to undefined. let and const are also hoisted but are not initialized, creating a "temporal dead zone".||
<br>

34. **In Node.js, which of the following is a "core module"?**
- [ ] `express`
- [ ] `axios`
- [ ] `path`
- [ ] `nodemon`

**Answer:** ||(C) The path module, along with fs, http, os, etc., is a built-in module provided by the Node.js runtime itself and does not need to be installed via npm.||
<br>

35. **What is the primary role of a "reducer" function in Redux?**
- [ ] To describe that an event has occurred.
- [ ] To hold the application's state.
- [ ] To specify how the application state changes in response to an action, by returning a new state object.
- [ ] To connect the Redux store to React components.

**Answer:** ||(C) A reducer is a pure function with the signature (state, action) => newState. It is the only place where state update logic should reside.||
<br>

36. **In React, what is the difference between a controlled and an uncontrolled component?**
- [ ] Uncontrolled components are faster because they don't cause re-renders.
- [ ] A controlled component's form data is handled by the DOM itself, while an uncontrolled component's data is handled by React state.
- [ ] A controlled component's form data is handled by React state, while an uncontrolled component's data is handled by the DOM itself (often accessed via refs).
- [ ] Uncontrolled components are a deprecated pattern.

**Answer:** ||(C) This is the key distinction. In a controlled component, React state is the single source of truth for the input's value. In an uncontrolled component, you let the DOM manage the input's state and pull the value out when needed, typically using a ref.||
<br>

37. **What is the HTTP status code for "Not Found"?**
- [ ] `200`
- [ ] `500`
- [ ] `404`
- [ ] `301`

**Answer:** ||(C) 404 Not Found is the standard response code when the server cannot find the requested resource.||
<br>

38. **The `...` syntax in JavaScript can be used as both the spread syntax and the rest parameter. What is the difference?**
- [ ] The spread syntax combines multiple elements into an array, while the rest parameter expands an array into individual elements.
- [ ] The spread syntax expands an iterable into individual elements, while the rest parameter collects multiple function arguments into a single array.
- [ ] There is no difference; the name changes based on context.
- [ ] The spread syntax is for objects, while the rest parameter is for arrays.

**Answer:** ||(B) When used in a function call or array literal (e.g., [...myArray]), it's the spread syntax. When used in a function's parameter list (e.g., function(...args)), it's the rest parameter.||
<br>

39. **In Redux, state mutations must be "immutable." What does this mean?**
- [ ] The state object cannot be changed after it is created.
- [ ] Reducers must not modify the existing state object directly; they must return a new state object with the required changes.
- [ ] The Redux store must be declared with `const`.
- [ ] Only strings and numbers can be stored in the state.

**Answer:** ||(B) Immutability is crucial for performance optimizations and time-travel debugging in Redux. By returning a new object, you make it easy for tools and libraries like React to detect that a change has occurred by doing a simple reference check (oldState === newState).||
<br>

40. **What is a "polyfill"?**
- [ ] A tool that transpiles modern JavaScript into older, compatible versions.
- [ ] A piece of code (or plugin) that provides the functionality of a modern web API on older browsers that do not have it natively.
- [ ] A security layer for web applications.
- [ ] A library for creating animations.

**Answer:** ||(B) A polyfill "fills in" a missing feature. For example, before all browsers supported the fetch API, you could include a fetch polyfill that would implement it using the older XMLHttpRequest object.||
<br>

41. **In CSS, what does the `*` selector do?**
- [ ] It selects the first element on the page.
- [ ] It selects all elements on the page.
- [ ] It selects elements with a specific attribute.
- [ ] It is not a valid selector.

**Answer:** ||(B) The * is the universal selector. It is often used in CSS resets to apply a baseline style (like box-sizing: border-box;) to every single element.||
<br>

42. **What does the `Promise.prototype.catch()` method handle?**
- [ ] It handles both resolved and rejected promises.
- [ ] It is executed when a promise is still in the "pending" state.
- [ ] It is syntactic sugar for `.then(null, rejectionHandler)` and handles only rejected promises.
- [ ] It converts a callback-based function to a promise.

**Answer:** ||(C) .catch(onRejected) is specifically for handling errors (rejections) in a promise chain. It makes the code more readable than handling the rejection in the second argument of .then().||
<br>

43. **In Express, `app.use(express.json())` is an example of what?**
- [ ] A route handler.
- [ ] A template engine.
- [ ] A built-in middleware for parsing incoming request bodies with JSON payloads.
- [ ] A function to send a JSON response.

**Answer:** ||(C) This is a common middleware that looks for requests with a Content-Type: application/json header and parses the JSON string in the request body into a JavaScript object, which it then attaches to req.body.||
<br>

44. **What is the concept of "props drilling" in React?**
- [ ] Passing a function as a prop to a child component.
- [ ] The process of passing props down through multiple layers of intermediate components that do not actually need the props themselves.
- [ ] A performance optimization technique.
- [ ] Using props to directly modify the DOM.

**Answer:** ||(B) Prop drilling can make components less reusable and code harder to maintain. It is the primary problem that the Context API and state management libraries like Redux are designed to solve.||
<br>

45. **Which method is used in a React class component to force a re-render, even if state or props haven't changed?**
- [ ] `this.render()`
- [ ] `this.update()`
- [ ] `this.forceUpdate()`
- [ ] `this.setState({})`

**Answer:** ||(C) Calling this.forceUpdate() skips shouldComponentUpdate and tells React to re-render the component. Its use is generally discouraged and often indicates a problem with your state management design.||
<br>

46. **What is an "Immediately Invoked Function Expression" (IIFE) in JavaScript?**
- [ ] A function that is called by an event listener.
- [ ] A function that is defined and executed at the same time, often used to create a private scope.
- [ ] An `async` function.
- [ ] A recursive function with no base case.

**Answer:** ||(B) The syntax (function() { ... })(); creates a function and immediately calls it. This was a common pattern in older JavaScript to prevent variables from polluting the global scope before block-scoping with let and const was introduced.||
<br>

47. **What is the role of a template literal (using backticks `` ` ``) in ES6?**
- [ ] It is a more performant way to declare strings.
- [ ] It allows for embedding expressions inside a string and creating multi-line strings.
- [ ] It automatically escapes special characters in a string.
- [ ] It is a special type of comment.

**Answer:** ||(B) Template literals provide a much cleaner syntax for string interpolation (e.g.,  \`Hello, ${name}!\` ) and allow for strings that span multiple lines without needing to use \n.||
<br>

48. **In Redux, a "selector" is typically:**
- [x] A function that accepts the Redux state as an argument and returns some derived data from that state.
- [ ] A CSS selector used for styling React components.
- [ ] A function that dispatches an action.
- [ ] The combination of all reducers.

**Answer:** ||(A) Selectors are used to decouple components from the exact shape of the Redux state tree. They are functions that extract and compute derived data, and can be memoized for performance.||
<br>

49. **What does the `Object.freeze()` method do in JavaScript?**
- [ ] It prevents new properties from being added to an object.
- [ ] It prevents existing properties from being removed from an object.
- [ ] It prevents the values of existing properties from being changed.
- [x] All of the above.

**Answer:** ||(D) Object.freeze() makes an object immutable. You cannot add, delete, or modify its properties. However, it is a shallow freeze; if a property is itself an object, that nested object can still be modified.||
<br>

50. **What is "server-side rendering" (SSR) in the context of a React application?**
- [ ] The process of running the entire React application on the client's browser.
- [x] An optimization where the server pre-renders the initial HTML for a React page and sends it to the browser, which can improve performance and SEO.
- [ ] A technique for rendering React components inside a Node.js server environment only.
- [ ] A way to render React components to a `<canvas>` element.

**Answer:** ||(B) With SSR, the user receives a fully rendered HTML page immediately, which can be faster for the "first contentful paint" and is easier for search engine crawlers to index. The client-side React app then "hydrates" this HTML to become fully interactive.||
## Session 1: Architecture of the Web

1.  **Which statement best describes the concept of idempotency in HTTP methods?**
    - [ ] The method can only be called once; subsequent calls will result in an error.
    - [ ] The method guarantees that the server's state will not change.
    - [ ] Multiple identical requests with the method will have the same effect as a single request.
    - [ ] The method requires an SSL/TLS connection to be established.

**Answer:** ||(C) An HTTP method is idempotent if a client can make that same call repeatedly while producing the same result. GET, HEAD, PUT, and DELETE are idempotent. POST is not.||
<br>

2.  **In the context of the Domain Name System (DNS), what is the role of a Top-Level Domain (TLD) server?**
    - [ ] It holds the final IP address for the requested domain name.
    - [ ] It is the first point of contact for a recursive resolver and directs it to the appropriate TLD server.
    - [ ] It manages domains like `.com`, `.org`, and `.net` and directs queries to the correct authoritative name servers.
    - [ ] It caches previous DNS lookups to speed up future requests for the same domain.

**Answer:** ||(C) The TLD server manages the last part of a domain name (like .com) and points the resolver to the authoritative name server that has the specific domain's information. The root server points to the TLD server.||
<br>

3.  **A primary performance bottleneck that HTTP/1.1 suffers from, which HTTP/2 addresses with multiplexing, is called:**
    - [ ] Connection flooding
    - [ ] Head-of-line blocking
    - [ ] Packet fragmentation
    - [ ] Server-side latency

**Answer:** ||(B) Head-of-line blocking in HTTP/1.1 means that if one resource is slow to load, it blocks all other resources from being requested over that single TCP connection. HTTP/2's multiplexing allows multiple requests and responses to be in-flight simultaneously over the same connection.||
<br>

4.  **How is state maintained across multiple requests in the inherently stateless HTTP protocol?**
    - [ ] By using the `keep-alive` connection header.
    - [ ] The server uses the client's IP address to track consecutive requests.
    - [ ] Through mechanisms like cookies sent by the server and stored by the client, which are sent back with subsequent requests.
    - [ ] HTTPS encrypts the session, thereby making it stateful.

**Answer:** ||(C) HTTP itself is stateless. State management is an application-layer concept built on top of it, most commonly implemented using server-sent cookies that the browser includes in future requests to identify the user's session.||
<br>

5.  **A web server responds with a `301 Moved Permanently` status code. What is the expected behavior of a search engine bot that receives this response?**
    - [ ] It will temporarily redirect the user and try the original URL again later.
    - [ ] It will report a client-side error and stop crawling the path.
    - [ ] It will update its index to replace the old URL with the new one provided in the `Location` header.
    - [ ] It will ignore the redirect and continue to use the original URL for ranking.

**Answer:** ||(C) A 301 status code is a crucial signal for SEO. It tells clients, including search engine crawlers, that the resource has permanently moved, and they should update their records to point to the new location.||
<br>

### Session 2: HTML

6.  **What is the primary purpose of using ARIA (Accessible Rich Internet Applications) attributes in HTML?**
    - [ ] To provide styling hooks for complex CSS selectors.
    - [ ] To improve the accessibility of web content for people with disabilities by providing more semantic information to assistive technologies.
    - [ ] To enable client-side validation for HTML5 forms without using JavaScript.
    - [ ] To embed rich media like audio and video directly into the webpage.

**Answer:** ||(B) ARIA attributes like role, aria-label, and aria-hidden supplement standard HTML to make web applications more accessible, especially for screen reader users, by clarifying the purpose and state of UI components.||
<br>

7.  **Consider the following HTML snippet: `<video><source src="movie.mp4" type="video/mp4"><source src="movie.ogg" type="video/ogg">Your browser does not support the video tag.</video>`. How will a browser interpret this?**
    - [ ] It will attempt to play both video files simultaneously.
    - [ ] It will throw an error because a `<video>` tag can only have one `<source>`.
    - [ ] It will check if it can play `movie.mp4`. If not, it will try `movie.ogg`. If neither works, it will display the fallback text.
    - [ ] It will display the fallback text and provide links to download both video files.

**Answer:** ||(C) The \<source> element allows you to specify multiple media resources for a media element. The browser uses the first one it supports, providing a robust fallback mechanism for different browser capabilities.||
<br>

8.  **Which of the following best describes the difference between `<article>` and `<section>` semantic tags in HTML5?**
    - [ ] `<article>` is for main page content, while `<section>` is exclusively for sidebars and footers.
    - [ ] `<article>` represents a complete, self-contained piece of content that could be distributed on its own (e.g., a blog post), while `<section>` is a thematic grouping of content within a document.
    - [ ] `<section>` can contain multiple `<article>` tags, but an `<article>` cannot contain a `<section>`.
    - [ ] There is no functional or semantic difference; they can be used interchangeably.

**Answer:** ||(B) This is the core semantic distinction. An \<article> should make sense on its own. A \<section> groups related content; for example, a chapter of a book could be a \<section>. An \<article> can contain \<section>'s for its own internal structure.||
<br>

9.  **What is the effect of the `defer` attribute on a `<script>` tag?**
    - [ ] It pauses HTML parsing, downloads the script, executes it, and then resumes parsing.
    - [ ] It downloads the script in parallel with HTML parsing and executes it as soon as it's downloaded, pausing the parser.
    - [ ] It downloads the script in parallel with HTML parsing but waits to execute it until after the parser has finished building the DOM.
    - [ ] It prevents the script from executing until a specific user event, like a button click.

**Answer:** ||(C) defer ensures the script does not block HTML parsing. It downloads asynchronously and executes in order with other deferred scripts, but only after the DOMContentLoaded event is about to fire. This is different from async, which executes as soon as it's ready, regardless of parsing state.||
<br>

10. **In an HTML form, what is the purpose of the `for` attribute in a `<label>` tag?**
    - [ ] It specifies the form the label belongs to.
    - [ ] It provides a fallback text for the input field.
    - [ ] It creates a programmatic association with an input element whose `id` attribute matches the `for` value, improving accessibility and user experience.
    - [ ] It indicates that the label is part of a `for` loop generated by a server-side language.

**Answer:** ||(C) The for attribute links the label to a specific form control. This allows a user to click the label to focus or activate the control, which is especially helpful for small targets like checkboxes and radio buttons.||
<br>

### Session 3: Cascading Style Sheets (CSS)

11. **Given the CSS rule `div > p`, which of the following `<p>` tags would be selected?**
    - [ ] `<p> inside <body><div><section><p>Text</p></section></div></body>`
    - [ ] `<p> inside <body><div><p>Text</p></div></body>`
    - [ ] `<p> inside <body><section><div><p>Text</p></div></section></body>`
    - [ ] All of the above.

**Answer:** ||(B) The > is the child combinator. It selects only elements that are direct children of the parent. In option A and C, the \<p> is a descendant but not a direct child of the \<div>.||
<br>

12. **Consider the following CSS: `#main-content { color: blue; } div.content { color: red; } div { color: green !important; }`. What color will the text be inside `<div id="main-content" class="content">Hello</div>`?**
    - [ ] blue
    - [ ] red
    - [ ] green
    - [ ] The browser will use its default text color due to the conflict.

**Answer:** ||(C) The !important declaration overrides all other specificity rules. Even though an ID selector (#main-content) is normally more specific than a type selector (div), the !important flag on the div rule gives it the highest precedence.||
<br>

13. **What is the fundamental difference in how total width is calculated for an element with `box-sizing: content-box;` versus `box-sizing: border-box;`?**
    - [ ] `content-box` includes margin in the total width, while `border-box` does not.
    - [ ] With `content-box`, the `width` property applies only to the content area. With `border-box`, the `width` property includes content, padding, and border.
    - [ ] `border-box` is the default value for all HTML elements.
    - [ ] `content-box` makes the element responsive, while `border-box` gives it a fixed size.

**Answer:** ||(B) This is a critical CSS concept. By default (content-box), if you set width: 100px; padding: 10px; border: 1px;, the actual visible width will be 122px (100 + 102 + 12). With border-box, the visible width would be exactly 100px, and the content area would shrink to accommodate the padding and border.||
<br>

14. **An element has `position: absolute;`. If none of its ancestor elements have a `position` property set to `relative`, `absolute`, or `fixed`, what will the element be positioned relative to?**
    - [ ] Its direct parent element, regardless of the parent's position property.
    - [ ] The `<body>` element.
    - [ ] The initial containing block, which is typically the viewport.
    - [ ] The element will behave as if it had `position: static;`.

**Answer:** ||(C) An absolutely positioned element is positioned relative to its nearest positioned ancestor. If no such ancestor exists, it is positioned relative to the initial containing block, which is the viewport (the visible part of the browser window).||
<br>

15. **In what order does the browser apply CSS styles based on their origin, assuming equal specificity and no `!important` flags?**
    - [ ] User Agent (Browser) -> Author (Your CSS) -> User (Custom user styles)
    - [ ] Author (Your CSS) -> User (Custom user styles) -> User Agent (Browser)
    - [ ] User Agent (Browser) -> User (Custom user styles) -> Author (Your CSS)
    - [ ] User (Custom user styles) -> Author (Your CSS) -> User Agent (Browser)

**Answer:** ||(C) The cascade order prioritizes author styles over user styles, and user styles over the browser's default stylesheet. This means your style.css will override the browser's default H1 styling.||
<br>

### Session 4: Responsive Web Design (Bootstrap)

16. **In the Bootstrap 5 grid system, what does the class `col-md-6` instruct the browser to do?**
    - [ ] The element should span 6% of the container's width on medium devices.
    - [ ] The element should span 6 of the 12 available columns, starting from the medium breakpoint (`≥768px`) and applying to larger breakpoints as well.
    - [ ] The element should have a fixed width of 6rem on medium devices only.
    - [ ] The element should be the 6th column in the grid on medium devices.

**Answer:** ||(B) Bootstrap's grid is mobile-first. A class like col-md-6 means "On medium screens and up, make this element take up half the container width (6/12)." On smaller screens (xs, sm), it would stack to take up 100% width unless a col-sm-\* or col-\* class is also specified.||
<br>

17. **Which of the following Bootstrap classes would create a visually prominent call-to-action area with a gray background and large text?**
    - [ ] `.card`
    - [ ] `.alert`
    - [ ] `.badge`
    - [ ] `.jumbotron` (in older versions) or a `div` with `p-5 mb-4 bg-light rounded-3` (in Bootstrap 5)

**Answer:** ||(D) The Jumbotron component was designed for this purpose. In Bootstrap 5, it was removed in favor of using utility classes to achieve the same effect, demonstrating the framework's move towards a utility-first approach. The combination of padding, margin, background, and border-radius creates the "jumbotron" look.||
<br>

18. **What is the primary advantage of a "mobile-first" approach in responsive design, as used by Bootstrap?**
    - [ ] It ensures the desktop version of the site loads faster.
    - [ ] It forces developers to prioritize content and functionality, leading to a cleaner design.
    - [ ] It results in less CSS code because styles for smaller screens are the baseline and are overridden only when needed for larger screens.
    - [ ] It is the only way to achieve a fluid grid layout.

**Answer:** ||(C) In a mobile-first approach, the default CSS targets small screens. Media queries are then used to add complexity for larger screens. This is generally more efficient than a "desktop-down" approach, which would require complex overrides to simplify the layout for mobile. It also aligns with prioritizing the mobile user experience.||
<br>

19. **How would you create a row in Bootstrap where you have one column taking up 1/3 of the width and another taking up the remaining 2/3, on all screen sizes?**
    - [ ] `<div class="row"><div class="col-3">...</div><div class="col-9">...</div></div>`
    - [ ] `<div class="row"><div class="col-4">...</div><div class="col-8">...</div></div>`
    - [ ] `<div class="row"><div class="col-one-third">...</div><div class="col-two-thirds">...</div></div>`
    - [ ] `<div class="row"><div class="col">...</div><div class="col-lg-auto">...</div></div>`

**Answer:** ||(B) The Bootstrap grid is based on a 12-column system. To achieve a 1/3 and 2/3 split, you need columns that sum to 12. 1/3 of 12 is 4, and 2/3 of 12 is 8. Therefore, col-4 and col-8 are the correct classes.||
<br>

### Session 5: JavaScript (Basics)

20. **What is the output of the following JavaScript code? `console.log('5' + 3); console.log('5' - 3);`**
    - [ ] `8`, `2`
    - [ ] `53`, `NaN`
    - [ ] `53`, `2`
    - [ ] `8`, `NaN`

**Answer:** ||(C) This demonstrates JavaScript's type coercion. The + operator performs string concatenation when one of the operands is a string, resulting in '53'. The - operator, however, only has a mathematical meaning, so it coerces both operands to numbers, resulting in the calculation 5 - 3 = 2.||
<br>

21. **Consider the code: `for (var i = 0; i < 3; i++) { setTimeout(() => console.log(i), 10); }`. What will be logged to the console?**
    - [ ] `0`, `1`, `2`
    - [ ] `3`, `3`, `3`
    - [ ] `0`, `1`, `2`, but after a delay.
    - [ ] `undefined`, `undefined`, `undefined`

**Answer:** ||(B) This is a classic closure and scope problem. Because var is function-scoped (not block-scoped), by the time the setTimeout callbacks execute, the loop has already completed. At that point, the single i variable in the scope has the value 3. If let were used instead of var, it would create a new i for each loop iteration, and the output would be 0, 1, 2.||
<br>

22. **Which of the following values is NOT considered "falsy" in JavaScript?**
    - [ ] `0`
    - [ ] `""` (empty string)
    - [ ] `null`
    - [ ] `'false'` (the string "false")

**Answer:** ||(D) In JavaScript, a "falsy" value is a value that translates to false in a boolean context. The falsy values are false, 0, -0, 0n, "", null, undefined, and NaN. Any non-empty string, including 'false', '0', or ' ', is "truthy".||
<br>

23. **What is the difference between the `==` and `===` operators in JavaScript?**
    - [ ] `==` is for comparing values, `===` is for comparing object references.
    - [ ] `==` performs type coercion before comparison, while `===` checks for both value and type equality without coercion.
    - [ ] `===` is a newer syntax for `==` and they function identically.
    - [ ] `==` checks for equality, while `===` checks for inequality.

**Answer:** ||(B) This is a fundamental concept. 5 == '5' is true because the string is coerced to a number. 5 \=== '5' is false because their types are different (number vs. string). It is best practice to always use === to avoid unexpected behavior from type coercion.||
<br>

24. **What does the term "hoisting" refer to in JavaScript?**
    - [ ] The browser's process of lifting heavy image assets to be loaded last.
    - [ ] The JavaScript engine moving all `var` and function declarations to the top of their containing scope before code execution.
    - [ ] A CSS technique for raising an element's z-index.
    - [ ] The automatic conversion of data types during operations.

**Answer:** ||(B) Hoisting means that you can use a variable or function before it has been declared in the code. However, only the declaration is hoisted, not the initialization. For var, this means the variable exists but is undefined until its assignment is reached. let and const are also hoisted but are in a "temporal dead zone" and cannot be accessed before declaration.||
<br>

25. **What is the result of `'hello'.slice(1, 3)`?**
    - [ ] `'el'`
    - [ ] `'ell'`
    - [ ] `'e'`
    - [ ] `['e', 'l']`

**Answer:** ||(A) The slice(startIndex, endIndex) method extracts a section of a string and returns it as a new string. It starts at startIndex (index 1 is 'e') and extracts up to, but not including, endIndex (index 3 is the second 'l'). So it extracts characters at index 1 and 2.||
<br>

### Sessions 6 & 7: JavaScript (Objects, Functions, OOP)

26. **Which of the following is a key characteristic of a closure in JavaScript?**
    - [ ] It prevents an object's properties from being modified.
    - [ ] It is an inner function that has access to the variables of its outer (enclosing) function, even after the outer function has returned.
    - [ ] It is a shorthand syntax for creating a class constructor.
    - [ ] It automatically binds the `this` keyword to the parent object.

**Answer:** ||(B) Closures are a powerful feature resulting from JavaScript's lexical scoping. They allow for data privacy and the creation of functions with persistent state, as seen in the setTimeout loop example earlier.||
<br>

27. **What is the `this` keyword referring to in the following code? `function Pet(name) { this.name = name; } const myPet = new Pet('Fido');`**
    - [ ] The global window object.
    - [ ] The `Pet` function itself.
    - [ ] The newly created object instance, `myPet`.
    - [ ] It is `undefined`.

**Answer:** ||(C) When a function is called with the new keyword (as a constructor), JavaScript creates a new empty object and sets the this keyword to point to that new object for the duration of the function call.||
<br>

28. **How does prototypal inheritance work in JavaScript?**
    - [ ] When creating a new object, you explicitly copy all properties from a parent object.
    - [ ] Objects inherit directly from other objects. When a property is accessed on an object, the engine checks the object itself, and if not found, checks its prototype, and so on up the chain.
    - [ ] It is a class-based system where an object is an instance of a class that inherits from another class.
    - [ ] By using the `extends` keyword, which creates a new prototype link.

**Answer:** ||(B) This describes the "prototype chain." Every JavaScript object has a private property which holds a link to another object called its prototype. This is the core mechanism of inheritance in JavaScript, even with the syntactic sugar of ES6 class.||
<br>

29. **What is the primary difference between a function declaration and a function expression?**
    - [ ] Function expressions cannot be anonymous.
    - [ ] Function declarations are hoisted, while function expressions are not.
    - [ ] Function expressions cannot be used as callbacks.
    - [ ] There is no practical difference; it is a matter of coding style.

**Answer:** ||(B) A function declaration (function myFunction() {}) is fully hoisted, meaning you can call it before it appears in the code. A function expression (const myFunction = function() {}) is not; the variable declaration (myFunction) is hoisted, but the function assignment is not, so you cannot call it before the assignment line.||
<br>

30. **What is the purpose of the `Object.create(null)` method?**
    - [ ] To create a new object that is identical to an empty object literal `{}`.
    - [ ] To create an object that has `null` as the value for all its properties.
    - [ ] To create a "pure" dictionary-like object that does not inherit any properties or methods from `Object.prototype` (like `toString`, `hasOwnProperty`).
    - [ ] It is a deprecated method for creating objects and should not be used.

**Answer:** ||(C) This is a useful technique for creating a clean key-value map. A normal object {} inherits from Object.prototype, so it has built-in properties. Object.create(null) creates an object with no prototype, so it is truly empty, preventing potential conflicts with property names like toString.||
<br>

31. **What will the following code log to the console? `const obj = { name: 'Alice', getName: function() { return this.name; } }; const unboundGetName = obj.getName; console.log(unboundGetName());`**
    - [ ] `Alice`
    - [ ] `undefined` (or an error in strict mode)
    - [ ] A reference to the `getName` function.
    - [ ] `null`

**Answer:** ||(B) This demonstrates how this is determined by the call site. When obj.getName() is called, this is obj. But when the function is assigned to unboundGetName and then called as unboundGetName(), it's just a plain function call. In non-strict mode, this would be the global object (window), which doesn't have a name property. In strict mode, this would be undefined, causing a TypeError.||
<br>

32. **A function that accepts another function as an argument or returns a function is known as a:**
    - [ ] Constructor Function
    - [ ] Pure Function
    - [ ] Generator Function
    - [ ] Higher-Order Function

**Answer:** ||(D) This is the definition of a higher-order function. Array.prototype.map, Array.prototype.filter, and Array.prototype.reduce are classic examples, as they all take a callback function as an argument.||
<br>

33. **What is the role of the `constructor` method within an ES6 `class`?**
    - [ ] It is a special method for creating and initializing an object created with a class. It is called automatically when an object is instantiated.
    - [ ] It is a static method that belongs to the class itself, not to any instance.
    - [ ] It defines the prototype for the class.
    - [ ] It is an optional method for destroying objects and freeing up memory.

**Answer:** ||(A) The constructor is the entry point for object creation via a class. It's where you would set initial properties based on arguments passed to new ClassName(...).||
<br>

34. **How would you use `Function.prototype.call` to invoke a function with a specific `this` context?**
    - [ ] `myFunc.call({ context: newContext }, arg1, arg2);`
    - [ ] `myFunc.call(newContext, arg1, arg2);`
    - [ ] `myFunc.call(newContext, [arg1, arg2]);`
    - [ ] `newContext.call(myFunc, arg1, arg2);`

**Answer:** ||(B) The call method invokes a function with a given this value and arguments provided individually. The first argument to call is the desired this context, followed by a comma-separated list of arguments for the function being called. This is different from apply, which takes an array of arguments as the second parameter.||
<br>

35. **Which of the following statements about JavaScript objects is most accurate?**
    - [ ] Objects can only have strings as property keys.
    - [ ] Objects are value types, and are copied when assigned to a new variable.
    - [ ] Objects are reference types; when assigned to a new variable, both variables point to the same object in memory.
    - [ ] The order of properties in an object is never guaranteed.

**Answer:** ||(C) This is a fundamental concept. If you do let obj2 = obj1;, you are not creating a new object. obj2 is just another pointer to the same memory location as obj1. Modifying obj2 will also modify obj1.||
<br>

36. **What is the output of this code? `let arr = [10, 20, 30]; let newArr = arr.map(num => num / 10); console.log(newArr); console.log(arr);`**
    - [ ] `[1, 2, 3]` and then `[1, 2, 3]`
    - [ ] `[1, 2, 3]` and then `[10, 20, 30]`
    - [ ] `undefined` and then `[10, 20, 30]`
    - [ ] An error, because `.map` modifies the array in place.

**Answer:** ||(B) The map method is non-mutating. It iterates over an array, applies a callback function to each element, and returns a new array with the results. The original array (arr) remains unchanged.||
<br>

37. **What is the purpose of the `super()` call inside the constructor of a subclass in JavaScript?**
    - [ ] To call a method from the parent class.
    - [ ] To call the constructor of the parent (super) class and establish the correct `this` binding and prototype chain.
    - [ ] It is an alias for `this` that refers to the parent class.
    - [ ] To prevent the parent constructor from running.

**Answer:** ||(B) In a subclass constructor, you must call super() before you can use the this keyword. This call executes the parent class's constructor, which sets up the inherited parts of the object.||
<br>

38. **Which method would you use to merge two objects, where properties from the second object overwrite those in the first?**
    - [ ] `Object.merge(obj1, obj2)`
    - [ ] `Object.assign({}, obj1, obj2)`
    - [ ] `obj1.concat(obj2)`
    - [ ] `new Object(obj1, obj2)`

**Answer:** ||(B) Object.assign(target, ...sources) copies all enumerable own properties from one or more source objects to a target object. By providing an empty object {} as the target, you create a new merged object without modifying the originals. The properties are applied in order, so obj2's properties will overwrite obj1's if they share keys.||
<br>

39. **What does the `JSON.stringify()` method do?**
    - [ ] It parses a JSON string, constructing the JavaScript value or object described by the string.
    - [ ] It converts a JavaScript object or value to a JSON string.
    - [ ] It validates if a given string is in correct JSON format.
    - [ ] It creates a deep copy of a JavaScript object.

**Answer:** ||(B) This method is used to serialize JavaScript data into a string format that can be easily transmitted over a network or stored. Its counterpart is JSON.parse().||
<br>

40. **You have an object `user = { name: 'John', address: { city: 'New York' } }`. You want to get the city, but the `address` property might not exist. Which syntax provides a safe way to access `city` without throwing an error?**
    - [ ] `user.address && user.address.city`
    - [ ] `user.address?.city`
    - [ ] `user.try('address.city')`
    - [ ] Both A and B are valid and effective.

**Answer:** ||(D) Option A is the traditional "short-circuiting" way to safely access nested properties. Option B uses the modern Optional Chaining (?.) operator, which was introduced specifically for this purpose. It returns undefined if any link in the chain is null or undefined, preventing a TypeError. Both are correct, with B being the more concise and modern approach.||
<br>
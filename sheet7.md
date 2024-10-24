# 1.What is the DOMContentLoaded event?

Ans : The DOMContentLoaded event in JavaScript is fired when the initial HTML document has been completely loaded and parsed, without waiting for external resources like stylesheets, images, and subframes to finish loading.

.Timing: It fires as soon as the HTML document is fully loaded and parsed, meaning the DOM is ready for manipulation.
.Does not wait for external resources: Unlike the load event, DOMContentLoaded does not wait for external resources (e.g., images, stylesheets, or iframes) to finish loading.
.When to use: It’s often used when you need to interact with the DOM (e.g., adding event listeners, modifying elements) as soon as possible, without waiting for non-essential assets.

DOMContentLoaded: Fired when the HTML is fully loaded and parsed, but before images and other external resources have fully loaded.
load: Fired when everything, including the HTML document, external resources (styles, images, scripts), and subframes, are fully loaded.

Use Case

Attaching event listeners to elements.
Manipulating DOM elements based on their structure.
Initializing plugins or JavaScript libraries that depend on DOM elements being present.

# 2.How can you modify classes of an element in the DOM?

Ans : 1.element.classList.add()
    2.element.classList.remove()
    3.element.classList.toggle()
    4.element.classList.contains()

3.What is the difference between appendChild and innerHTML for adding elements?

Ans : 
.appendChild is more DOM-safe and efficient for adding individual elements or nodes without re-parsing the entire content.
.innerHTML is more versatile for injecting multiple elements or HTML strings but comes with potential performance drawbacks and security concerns if not used carefully

4.How do you clone an element in the DOM?

Ans :
Use cloneNode() to duplicate elements, specifying whether you want to copy only the element or its entire subtree.
cloneNode(true) to clone the element and its subtree.
cloneNode(false) to clone the element but not its subtree.

5.What is Shodow Dom?

Ans : The Shadow DOM is a web standard that allows developers to encapsulate a portion of the DOM and its style rules, creating a separate, hidden "shadow tree" within an element. This shadow tree is isolated from the main document’s DOM (also called the "light DOM") and does not affect or get affected by the global document styles or scripts.

6.performance.now()?

Ans : performance.now() returns a high-resolution timestamp in milliseconds, which can be used to measure the duration of an event or process.

7.What is Reflow?

Ans : It is Process calculating the position or dimension of the element to show in page.
It is an instance talk that take long time to complete.

8.What is Repaint?

Ans : The process of painting content of the elemenets pixel by pixel.It is much faster than reflow.

9.Document Fragment?

Ans : It is light weight doc object. On adddition of element it does not perform reflow and repaint.

So when we add this to main Dom then Only 1 reflow and 1 repaint is performed.

let fragment = document.createDocumentFragment();


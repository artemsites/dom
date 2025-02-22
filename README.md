# Dom Library - a brief summary
1. The library works with a real DOM tree.
> Unlike Vue, which work with a virtual DOM and then render the results to the real DOM!
2. A valid HTML API is used, as a result, the library does not create validation errors https://validator.w3.org
> Unlike Vue, which, when used in the HTML markup of a classic website, creates HTML validation errors!



## Initializing the application in js
```js
// js module for web browser WITHOUT builder
import { createScope, ref } from "./node_modules/dom-reactive/index.mjs";

// js module for web browser WITH builder
import { createScope, ref } from "dom-reactive";

createScope("header", () => {
  let isActive = ref(false);

  function open() {
    isActive.value = true;
  }

  function close() {
    isActive.value = false;
  }

  return {
    isActive,
    open,
    close,
  };
});

```



## Using the application in html
Important: each application is an object called the id for which the application is created, for example, "header":
```html
  <header id="header">

    <button onclick="header.open()">
      open
    </button>

    <button onclick="header.close()">
      close
    </button>

    <div class="target" data-class='{"active": "header.isActive", "active-not": "!header.isActive"}'>
      test data-class Object JSON
    </div>

    <div class="target" data-class='["header.isActive ? active : active-not", "!header.isActive ? test-not : test"]'>
      test data-class Array JSON
    </div>

  </header>
```



## API
* `createScope` - creating an area in the DOM for working with the library
* `ref` - reactive state
* `data-class` is an attribute of an HTML element for dynamic class management

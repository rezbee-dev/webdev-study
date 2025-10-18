# CSS Notes 

_based on ["CSS in Depth"](https://www.manning.com/books/css-in-depth-second-edition)_

======================================================================

## 1. Cascade, Specificity, and Inheritance

**Topics**
- Cascade 6 criteria
- Cascade vs Inheritance
- Controlling which styles apply to which elements
- Shorthand declarations

### Cascade 

<details>
  <summary>a) What color will the `h1` tag be?</summary>

  ```html
  <h1 id="page-title" class="title">Lel</h1>
  ```

  ```css
  h1 {
    color: red;
  }
  
  #page-title {
    color: blue;
  }
  
  .title {
    color: green;
  }
  ```

  <details><summary>Answer</summary>
    
  - Blue
  </details>
</details>

<details>
  <summary>b) What three things are used to determine CSS styling/ resolve CSS conflicts?</summary>

  - Stylesheet origin _(browser defaults aka user-agent styles and your CSS styles)_
  - Seleector Specificity _(inline, ID, class, etc)_
  - Source Order _(order in which styles are declared in the CSS file; whichever appears later in CSS file wins)_
</details>

<details>
  <summary>c) How do you override inline styles from CSS file?</summary>

  - use `!important` in the CSS file
</details>

<details>
  <summary>d) What color will the `h1` tag be?</summary>

  ```html
  <h1 class="title heading">Lel</h1>
  ```

  ```css
  .title {
    color: green;
  }

  .title.heading {
    color: red;
  }
  ```

  <details><summary>Answer</summary>
    
  - Red
  - The more "specific" the selector is or the more IDs, classes, tag names, etc it has means it takes higher precedence
  - See MDN docs - https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_cascade/Specificity for more info on specificity
  </details>
</details>

<details><summary>e) In which order should selectors for styling `a` tag states go in?</summary>

  - From top to bottom: link, visited, hover, active

  ```css
  a:link {
    color: blue;
    text-decoration: none;
  }
  
  a:visited {
    color: purple;
  }
  
  a:hover {
    text-decoration: underline;
  }
  
  a:active {
    color: red;
  }
  ```
</details>

### Inheritance

<details>
  <summary>a) What's the CSS value that can be used to allow an element to override its cascaded value with its parent's value? </summary>

- Ex: Heading #1 & Heading #2 are red due to the `h1` css declaration. What can you use for Heading #2 to override the red color and use the color set by its parent, the `div`?
  ```html
  <h1>Heading #1</h1>
  <div>
    <h1>Heading #2</h2>
    <p>I'm blue</p>
  </div>
  ```

  ```css
  h1 {
    color: red
  }

  div {
    color: blue
  }
  ```

  <details><summary>Answer</summary>
    
  - use `inherit` to override a cascaded value
 
  ```css
  h1 {
    color: red
  }

  div {
    color: blue
  }

  div h1 {
    color: inherit;
  }
  ```
  </details>
</details>

<details><summary>b) What's the one CSS value that lets you override an element's property back to it's default value?</summary>

  - `initial`
</details>



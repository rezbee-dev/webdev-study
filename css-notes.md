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
  <summary>b) What are the three things used to resolve CSS conflicts?</summary>

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


======================================================================

### 2. Working with relative units
_to be filled in later_

### 3. Document Flow & Box Model
_to be filled in later_

### 4. Flexbox
_to be filled in later_

### 5. Grid Layout
_to be filled in later_

### 6. Positioning and stacking contexts
_to be filled in later_

### 7. Responsive Design
_to be filled in later_

### 8. Cascade Layers and Nesting
_to be filled in later_

### 9. Modular CSS and Scope
_to be filled in later_

### 10. Container Queries
_to be filled in later_

### 11. Color and Contrast
_to be filled in later_

### 12. Typography and Spacing
_to be filled in later_

### 13. Gradients, shadows, and blend modes
_to be filled in later_

### 14. Masks, shapes, and clipping
_to be filled in later_

### 15. Transitions
_to be filled in later_

### 16. Transforms
_to be filled in later_

### 17. Animations
_to be filled in later_

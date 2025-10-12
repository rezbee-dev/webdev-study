# Notes

## CSS

_based on ["CSS in Depth"](https://www.manning.com/books/css-in-depth-second-edition)_

======================================================================

### 1. Cascade, Specificity, and Inheritance

Topics covered
- Cascade 6 criteria
- Cascade vs Inheritance
- Controlling which styles apply to which elements
- Shorthand declarations

Cascade
- set of rules that browser uses to resolve CSS conflicts
  <details>
    <summary>Cascade example</summary>
    
    `h1` tag here has multiple conflicts
      <details>
        <summary>which CSS rule applies?</summary>
        the id tag: #page-title
      </details>
    
    ```HTML
    <h1 id="page-title" class="title">Wombat Coffee Roasters</h1>
    ```
  
    ```CSS
    h1 {
      font-family: serif;
    }
    
    
    #page-title {
      font-family: sans-serif;
    }
    
    
    .title {
      font-family: monospace;
    }
    ```
  </details>

Cascade Six Criteria (In order of application)
1. Stylesheet origin
2. Inline styles
3. Layer
4. Selector specificity
5. Scope Proximity
6. Source order
<details>
  <summary>Cascade high-level flowchart</summary>
    
  ![figure 1.3](https://drek4537l1klr.cloudfront.net/grant3/Figures/1-3.png)
</details>

Stylesheet Origin Types
- Author styles (styles you add) - highest priority
- User styles (styles added end user via browser) - medium priority
- User-agent styles (browser defaults) - lowest priority

`!important`
- declarations (css rules) marked `!important` are treated as higher-priority stylesheet origin & overrides normal styles from any origins

Order of preference, from highest to lowest priority 
- `!important` user-agent
- `!important` user
- `!important` author
- normal author
- normal user
- normal user-agent


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

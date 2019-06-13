# CSS
## Concepts, Organization, and Best Practices

---

## Outline
- Key Concepts of CSS  <!-- .element: class="fragment fade-in" -->
- How do we organize our CSS? <!-- .element: class="fragment fade-in" -->
- Workflow <!-- .element: class="fragment fade-in" -->
- Helpful Tools and Resources <!-- .element: class="fragment fade-in" -->

... and maybe some demos <!-- .element: class="fragment fade-right" --> 

---

![css problems](https://i.imgur.com/Q3cUg29.gif)

## #CSS-problems

---

## key Concepts
 (the ones  *_I_*  want to talk about)

- syntax + comments
- at-rules + descriptors
- css selectors 
- cascade + specificity + inheritance
- css functions
- css units and value types

_full reference available on [MDN CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)_

---

## syntax + comments

```css

.selector[s], 
.rule[set] {                /*__         */
                            /*  |        */
	property: value     /*  |- block */
                            /*  |        */
}                           /*__|        */


```

---

## at-rules + descriptors

``` css
    @import url('new-style.css'); /* === @import 'new-style.css' */
    @import 'print-style.css' print;
    @import 'landscape-css' screen and (orientation:landscape);

    @media screen and (min-width 700px) {
        ...
    }

    @supports (display: grid) {
        ...
    }

    @supports (display: flex) and (grid-template-areas) {
        @media screen and (min-width 1200px) {
            ...
        }
    }

    @keyframes fade-in {
        from {...}
        to {...}
    }   
```


*_full list available on [MDN CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS/At-rule)_*

Note:

- an instruction that tells CSS how to CSS 
- starts with `@<rule-name>` and ends with `;` or at the end of a related statement 

---

## selectors + rules + specificity

Effect on Specificity:

```html 

<p class= "class1"> paragraph text... </p>
<p class= "class2 "> paragraph text... </p>
<p class= "class3"> paragraph text... </p>

<p class="class1 class2 class3"></p>

```
```css

p .class1 .class2 .class3 {
    ...
}

p .class1.class2.class3 {
    ...
}

p .class1, .class2, .class3 {
    ...
}

.btn, .orangeBtn {
    <!-- general btn styling -->
}

.orangeBtn {
    background: orange 
}


```
1. ID selectors
2. Class Selectors, Attribute Selectors, Pseudo Selectors 
3. Type Selectors

No Effect on Specificity:

- universal rules
- combinators (+, >, ~, " ", ||)
- `:not()` (arguments do effect specificity)

---

## cascade + specificity + inheritance

### Style Sheets:
1. User Agent 
2. Author
3. User

---

| 	| Origin      |	Importance|
|---|-------------|-------------     |
|1	|user agent   | normal|
|2	|user         |normal|
|3	|author	      | normal|
|4	|animations	  ||
|5	|author	      | !important|
|6	|user	      | !important|
|7	|user agent	  | !important|
|8	|transitions	 |

- in case of equality, selector specificity makes the final call


Note:
- I like this one as a reset: https://css-tricks.com/snippets/css/meyer-reset/
- make sure to read over any CSS reset you use from another source and update any declarations you don't want
- always credit the source!

---

# css units + value types

- `vw` and  `vh` 
- `%`
- `em`
- `rem`
- `vmin + vmax`

*_exhaustive list on [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Values_and_Units)_*

---

# CSS functions + variables

- `url()`
- `rgba()`
- `calc()`
- `attr()`

- `--*` `--some-variable`

---

# Organizing Our CSS

---

## Why do we care...?
### #fake_it_til_you_make_it

Note:
- until now most of us tackle styling as a necessary evil
- spaghetti code 
    - both in the traditional antipattern sense of the term
    - also in the check if it's done way => throw it at the wall and see what sticks
- not going to lie, CSS will continue to be a bit of that, but the side effect we don't think about is the state of code after that process
    - this makes everything more difficult to find
    - so fed up our code is usually hacky, coupled, and hard to refactor
    - it remains a bit too much like witch craft

---

- spaghetti code 
- "creative" selectors 
- specificty hell
- crazypants nesting 
- &#x1F92F; <!-- .element: class="fragment fade-in" -->

Note:
- spaghetti code => way too much time looking for the block you need
- "creative" selectors => way too much time figuring out which elements are being selected (on purpose and by mistake)
- specificty hell => way too much time negotiating with the rest of your code and begging your code to do the thing you want it to do
- crazypants nesting 

---

## How do we organize our CSS?
Note:
- picking up from where we left off yesterday—let's apply some of the thinking we did yesterday to style

---

## Thinking about CSS as OOP 
- Separation of Concerns <!-- .element: class="fragment fade-in" -->
- Single Responsibility Principle <!-- .element: class="fragment fade-in" -->
- Relying on inheritance  <!-- .element: class="fragment fade-in" -->
- Consistent, Predictable, Declarative Nomenclature <!-- .element: class="fragment fade-in" -->

Note:
- flexible, modular, swappable code
- we can apply this these concepts to:
1). the way in which we target and style individual elements in our code
2.) the way in which we structure our files
3.) the way in which we name our classes



- how can we apply OOP cleanliness/predictability/practices to Styling
  - Inheritance, Abstraction, Encapsulation, Polymorphism
  - decoupling -- each block (or object) has it's own set of concerns and doesn't intrude on any others'
  - instead of repetition of state/functionality, we're focussing on repetition of style
  - what is an object in JS isn't always an object in 
- flattening => more efficient CSS

---

## 3 methods to consider
 
- OOCSS (OOP)
- SMACCS (File Structure)
- BEM (Nomenclature)

Note:

  - look for repetition and what is not predictable
  
  - SMACCS - base, layout, modules, other, [shame]

  - BEM block__decendent--modifier

- Selectors and Specificity Hell
  - Flattening your CSS
  - Naming Practices (keep it consistent)
- Helpful Tools/Resources 
  - prefixer
  - scss transpiler
  - minifier [hold off until the end]






---

## Tools + Resources
- [Can I Use](https://caniuse.com/)
- [AutoPrefixer](https://www.npmjs.com/package/autoprefixer#webpack)
- [Organizing CSS: OOCSS, SMACSS, and BEM](https://mattstauffer.com/blog/organizing-css-oocss-smacss-and-bem/)

---




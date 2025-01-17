# 01.4 Full-Time Lesson Plan: Pseudo-Resets

## Overview

In today's class, students will begin by working with styling CSS boxes. The theme of today's class is overwriting browser defaults. Students will implement a CSS reset to zero-out certain styles and then rebuild those styles using advanced CSS concepts like pseudo-classes and pseudo-elements.

## Instructor Notes

* In this lesson, students will complete activities `09-Ins_Box-Styling` through `20-Stu_Custom-Forms`.

* Skim over the following documentation to get familiar with some of the advanced CSS selectors that students will be using:

  * [MDN Web Docs on pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
  
  * [MDN Web Docs on pseudo-elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements)
  
  * [MDN Web Docs on adjacent sibling combinators](https://developer.mozilla.org/en-US/docs/Web/CSS/Adjacent_sibling_combinator) 

* Today's lesson also touches on typography. Students will likely see different fonts on their machines depending on their operating system, so be prepared to discuss web-safe fonts and font fallbacks.

* Remind students to do a `git pull` of the class repo and to have today's activities ready and open in VS Code. 

* If you are comfortable doing so, live-code the solutions to the activities. If not, just use the solutions provided and follow the prompts and talking points for review.

* Let students know that the Bonus at the end of each activity is not meant to be extra coding practice but instead is a self-study on topics beyond the scope of this unit, for those who want to further their knowledge.

## Learning Objectives

By the end of class, students will be able to do the following:

* Enhance the UI of a webpage using box styling.

* Explain why you would use a CSS reset.

* Use typographical CSS properties, like `font-family` and `line-height`.

* Add pseudo-classes and pseudo-elements to HTML elements.

* Explain the default styles that browsers apply to form elements.

## Time Tracker

| Start  | #   | Activity Name                      | Duration |
|---     |---  |---                                 |---       |
| 10:00AM| 1   | Instructor Demo: Box Styling       | 0:05     |
| 10:05AM| 2   | Student Do: Box Styling            | 0:15     |
| 10:20AM| 3   | Instructor Review: Box Styling     | 0:10     |
| 10:30AM| 4   | Instructor Do: Stoke Curiosity     | 0:10     |
| 10:40AM| 5   | Instructor Demo: CSS Resets        | 0:05     |
| 10:45AM| 6   | Student Do: CSS Resets             | 0:15     |
| 11:00AM| 7   | Instructor Review: CSS Resets      | 0:10     |
| 11:10AM| 8   | Instructor Demo: Typography        | 0:05     |
| 11:15AM| 9   | Student Do: Typography             | 0:15     |
| 11:30AM| 10  | Instructor Review: Typography      | 0:10     |
| 11:40AM| 11  | FLEX                               | 0:20     |
| 12:00PM| 12  | BREAK                              | 0:30     |
| 12:30PM| 13  | Instructor Demo: Pseudo-Classes    | 0:05     |
| 12:35PM| 14  | Student Do: Pseudo-Classes         | 0:15     |
| 12:50PM| 15  | Instructor Review: Pseudo-Classes  | 0:10     |
| 1:00PM | 16  | Instructor Demo: Pseudo-Elements   | 0:05     |
| 1:05PM | 17  | Student Do: Pseudo-Elements        | 0:15     |
| 1:20PM | 18  | Instructor Review: Pseudo-Elements | 0:10     |
| 1:30PM | 19  | Instructor Demo: Custom Forms      | 0:05     |
| 1:35PM | 20  | Student Do: Custom Forms           | 0:15     |
| 1:50PM | 21  | Instructor Review: Custom Forms    | 0:10     |
| 2:00PM | 22  | FLEX                               | 0:30     |
| 2:30PM | 23  | END                                | 0:00     |

---

## Class Instruction

### 1. Instructor Demo: Box Styling (5 min)

* Welcome students to class.

* Open `09-Ins_Box-Styling/index.html` in your browser and demonstrate the following:

  * 🔑 We can do many things to transform CSS boxes. Let's open Chrome DevTools and explore a few of them.

  * 🔑 First, we see how we can rotate to the right and left. Positive numbers make it rotate to the right, and negative numbers make it rotate to the left:

    ```css
    .rotate {
      transform: rotate(7deg);
    }

    .rotate {
      transform: rotate(-7deg);
    }
    ```

  * 🔑 Next, we see how we can stretch them vertically and horizontally. The first number specifies the x-axis scaling value and the second number is the y-axis scaling value. When we change the values, like in the following example, we can see it stretch:

    ```css
    .scale {
      transform: scale(1.5, 1);
    }

    .scale {
      transform: scale(1, 1.5);
    }
    ```

  * 🔑 Lastly, we can skew them to the right and left. Again, you can test positive and negative values to see it change:

    ```css
    .skew {
      transform: skew(15deg);
    }

    .skew {
      transform: skew(-15deg);
    }
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How would we build the next activity?

  * 🙋 We will need to research CSS documentation to enhance the UI of the product cards on the online store webpage.

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `10-Stu_Box-Styling/README.md`.

### 2. Student Do: Box Styling (15 min)

* Direct students to the activity instructions found in `10-Stu_Box-Styling/README.md`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 📖 Implement Box Styling on Product Cards

  Work with a partner to implement the following user stories:

  * As the store owner, I want to display the product cards with rounded corners.

  * As the store owner, I want to give the product cards a 3D look by dropping a shadow and rotating it slightly.

  ## Acceptance Criteria

  * It's done when the product cards have rounded corners, drop shadows, and a rotated appearance.

  * The solution does not have to look exactly like the image provided. Play around with the properties and have fun!

  ## 📝 Notes

  Refer to the following documentation:

  [MDN Web Docs on creating fancy boxes](https://developer.mozilla.org/en-US/docs/Learn/CSS/Howto/create_fancy_boxes)

  ## Assets

  The following image demonstrates the web application's appearance:

  ![The product cards have rounded corners with a shadow and are rotated to the right.](./Images/01-css-box-styling.png)

  ## 💡 Hints

  * Look into CSS border and background properties, like `border-radius`, `box-shadow`, and `transform`.

  ## 🏆 Bonus

  If you have completed the activity and want to further your knowledge, work through the following challenge with your partner:

  * What are vendor prefixes, and how are they useful?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 3. Instructor Review: Box Styling (10 min)

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with `CSS box styling`? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points (✔️):

  * ✔️ `border-radius`

  * ✔️ `box-shadow`

  * ✔️ `transform: rotate()`

* Open `10-Stu_Box-Styling/Unsolved/index.html` in your browser and demonstrate the following:

  * Let's say that we are the store owners and we want to display our products nicely so that they are more appealing to our customers.

  * Right now, the product cards are just rectangular boxes with no styling. Let's change that!

* Open `10-Stu_Box-Styling/Solved/assets/css/style.css` in your IDE and explain the following: 

  * First we should identify which element we are targeting. All of our product cards have a class of `.card`, so that's where we will add the code:

    ```css
    /* TODO: Add properties to the cards to achieve the required look */
    .card {
      border-style: solid;
      border-width: 1px;
      padding: 10px;
      margin: 20px;
      flex: 0 0 300px;
    }
    ```

  * 🔑 First, we need to round out the corners by using `border-radius` and giving it a value of `50px`. Your value does not have to match this exactly, just as long as it is rounded! See the following code for an example:

    ```css
    .card {
      border-radius: 50px;
    }
    ```

  * Notice what happens to the header of the card. We need to round those corners out too, but only the top corners, like in the following example:

    ```css
    /* Added border-radius to match the card */
    .card header {
      border-radius: 50px 50px 0px 0px;
    }
    ```

  * 🔑 Next, we add a `box-shadow` to the cards to give it a 3D look:

    ```css
    .card {
      box-shadow: 10px 10px 5px #aaaaaa;
    }
    ```

  * 🔑 Finally, we rotate the cards slightly to the right:

    ```css
    .card {
      transform: rotate(8deg);
    }
    ```

  * Again, your values for these properties do not have to match the solution exactly. Have fun playing around with it!

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What are some other styles we could've tried on these product cards to make them look better?

  * 🙋 (Answers will vary.) We could have changed the `border-style` to dotted lines or dashes; we could have changed the `border-radius` to `100%` to make it into a circle; or we could have simply changed some colors.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [MDN Web Docs on creating fancy boxes](https://developer.mozilla.org/en-US/docs/Learn/CSS/Howto/create_fancy_boxes), and stay for office hours to ask for help.

* Answer any questions before transitioning to the next topic.

### 4. Instructor Do: Stoke Curiosity (10 mins)

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What new CSS tricks have you learned this week?

  * 🙋 Media queries, flexbox, box shadows, rounded corners, etc.

* Explain that a big part of CSS is undoing, or restyling, the default styles that the browser gives you. This is especially true for form elements, which are ubiquitous across the web but not as easy to customize as `<div>` and `<span>` containers.

* Open the [Postcard Form Example](https://mdn.github.io/learning-area/html/forms/postcard-example/) in your browser and explain the following:

  * The MDN Web Docs team built this form as an example of what's possible with CSS.

  * The `<textarea>`, `<input>`, and `<button>` elements have all been customized.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What CSS properties do you recognize as being used in this example?

  * 🙋 `transform`, `border-radius`, `background`, etc.

* Open Chrome DevTools and delete the `<style>` element to remove all of the styles on the page.

* Explain that this is how the form was originally styled by the browser. In today's class, we'll look at additional CSS properties that will help us rebuild our own forms. 

### 5. Instructor Demo: CSS Resets (5 min)

* Open `11-Ins_CSS-Resets/index.html` in your browser and explain the following:

  * 🔑 This page has no style sheet, but the browser already renders elements a certain way.

  * 🔑 Every browser renders these defaults differently, which can cause unwanted discrepancies.

  * Developers find it helpful to reset these defaults before applying their own styles, allowing them to write CSS with peace of mind.

* Open `11-Ins_CSS-Resets/index.html` in your IDE and demonstrate the following:

  * 🔑 Let's add a style sheet that resets these defaults by uncommenting the `<link>` element:

    ```html
    <link rel="stylesheet" href="./assets/css/reset.css" />
    ```

  * 🔑 In the browser, all of the margins, padding, and font sizes have been normalized. Now a developer can rebuild these styles from scratch exactly the way they want.

* Open `11-Ins_CSS-Resets/assets/css/reset.css` in your IDE and explain the following:

  * 🔑 We use a wildcard selector to reset the box size of every element:

    ```css
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }
    ```

  * 🔑 We give the `<html>` element a `height` of `100%` and the `<body>` a `min-height` of `100%` to ensure the document always takes up at least the size of the viewport. This makes it easier to position things like footers:

    ```css
    html {
      height: 100%;
    }

    body {
      min-height: 100%;
      line-height: 1;
      font-family: sans-serif;
    }
    ```

  * 🔑 Several HTML elements like `<input>` and `<button>` have their own font styling, so we reset them to match the rest of the page:

    ```css
    input, select, option, optgroup, textarea, button,
    pre, code {
      font-size: 100%;
      font-family: inherit;
    }
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ Why would you want to reset the browser's default CSS?

  * 🙋 To give yourself a clean starting point and minimize cross-browser differences.

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `12-Stu_CSS-Resets`.

### 6. Student Do: CSS Resets (15 min)

* Direct students to the activity instructions found in `12-Stu_CSS-Resets`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 🐛 Custom Font Styles Aren't Loading

  Work with a partner to resolve the following issues:

  * As a user, I expect headings to be a larger font size.

  * As a user, I expect spacing in between the lines of text.

  ## Expected Behavior

  The blog title and article headings should be a larger font size.

  ## Actual Behavior

  The headings are the same size as the other text on the page.

  ## Assets

  The following image demonstrates the web application's appearance:

  ![The blog layout has larger-sized headers and spacing in between the lines of text.](./Images/01-correct-styles.png)

  ## 💡 Hints

  * How can you fix the styling without writing any new CSS rules?

  ## 🏆 Bonus

  If you have completed the activity and want to further your knowledge, work through the following challenge with your partner:

  * What is Normalize.css and how does it affect different browsers?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 7. Instructor Review: CSS Resets (10 min)

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel using CSS resets? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points (✔️):

  * ✔️ Order of precedence

  * ✔️ Selector specificity

* Open `12-Stu_CSS-Resets/Solved/index.html` in your IDE and explain the following: 

  * We needed to swap the `<link>` elements so that the `reset.css` style sheet loads first:

    ```html
    <link rel="stylesheet" href="./assets/css/reset.css" />
    <link rel="stylesheet" href="./assets/css/style.css" />
    ```

  * 🔑 When style sheets have conflicting CSS rules, like a generic `h1` selector, the style sheet that's loaded second will take precedence.

* Open `12-Stu_CSS-Resets/Solved/assets/css/style.css` in your IDE and explain the following: 

  * 🔑 The CSS rules for `<ul>` elements didn't conflict because the selectors in `style.css` were more specific. For example, a `<ul>` inside of a `<nav>` element:

    ```css
    nav ul {
      display: flex;
      justify-content: space-between;
      min-width: 300px;
    }

    article ul {
      margin-left: 5%;
      font-size: 110%;
      list-style: circle;
    }
    ```

  * 🔑 A more specific selector will always take precedence over a generic selector, regardless of style sheet order.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What other CSS rules conflicted in the two style sheets?

  * 🙋 They both have a rule for `body`.

  * ☝️ Why would you always want to load your CSS reset first?

  * 🙋 To avoid undoing your custom styles.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [MDN Web Docs on the cascade](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance), and stay for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

### 8. Instructor Demo: Typography (5 min)

* Open `13-Ins_Typography/index.html` in your browser. Inspect the `<p class="one">` element with Chrome DevTools to explain the following:

  * 🔑 The class has a `font-family` value of `'Helvetica', 'Arial', sans-serif`.
  
  * 🔑 Multiple fonts are listed in case the user's operating system can't find the first or second one. Helvetica, for instance, is usually not installed on Windows machines.

  * 🔑 The `font-weight` and `font-style` properties can make a font appear bold or slanted, but by how much depends on the font being used. For instance, `oblique` will often look the same as `italic`.

* Inspect the `<p class="four">` element with Chrome DevTools to demonstrate the following:

  * 🔑 Setting the `text-transform` property to `uppercase` or `capitalize` will change how the text is capitalized:

    ```css
    .four {
      font-family: serif;
      font-weight: 100;
      font-style: normal;
      text-transform: uppercase;
      text-decoration: none;
    }
    ```

  * 🔑 Setting the `text-decoration` property to `underline` or `line-through` will apply a line to the text:

    ```css
    .four {
      font-family: serif;
      font-weight: 100;
      font-style: normal;
      text-transform: uppercase;
      text-decoration: underline;
    }
    ```

  * 🔑 There are many ways to alter a font with CSS, but making a font look good usually comes down to adjusting the `margin`, `line-height`, and `font-size`.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ Why should you provide more than one `font-family` value?

  * 🙋 Not every computer will have the first font specified.

  * ☝️ How do you know which font properties are available to use?

  * 🙋 Read the [MDN Web Docs on font](https://developer.mozilla.org/en-US/docs/Web/CSS/font) or experiment with the Chrome DevTools.

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `14-Stu_Typography`.

### 9. Student Do: Typography (15 min)

* Direct students to the activity instructions found in `14-Stu_Typography`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 📖 Implement Typographic Styles

  Work with a partner to implement the following user story:

  * As a user, I want to read a blog that uses visually appealing font styles.

  ## Acceptance Criteria

  * It's done when the body font has the standard size of 16px.

  * It's done when paragraphs have a line height of 1.5 times the font height.

  * It's done when headings are 150–200% of the font size and have a font family of `serif`.

  * It's done when there is a margin of 2–5% on the heading, paragraph, and list.

  * It's done when the list is indented, has square bullet points, and has a font family of `monospace`.

  * Working with CSS should be a creative experience for you! Your end product should look as close to the solution as possible, but feel free to try out other looks!

  ## 📝 Notes

  Refer to the following documentation: 

  [MDN Web Docs on fundamental text and font styling](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Fundamentals)

  ## Assets

  The following image demonstrates the web application's appearance:

  ![The blog page includes a monospaced list and headings with a serif font.](./Images/01-CSS-typography.png)

  --- 

  ## 💡 Hint

  * What values for `font-weight` and `font-style` can you use to give the page a more personal touch?

  ## 🏆 Bonus

  If you have completed the activity and want to further your knowledge, work through the following challenge with your partner:

  * What are some other options for web fonts besides the given basic fonts?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 10. Instructor Review: Typography (10 min)

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with CSS fonts? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points (✔️):

  * ✔️ Default fonts

  * ✔️ Font percentages

* Open `14-Stu_Typography/Solved/assets/css/style.css` in your IDE and explain the following: 

  * We adjusted the `body` CSS rule to include a base `line-height` and `font-size`:

    ```css
    body {
      display: flex;
      flex-direction: column;
      line-height: 1.5;
      font-size: 16px;
    }
    ```

  * 🔑 We added margins to the headers, set the `font-size` to be a percentage of the base font, and set the `font-family` to the operating system's default `serif` font:

    ```css
    h1 {
      margin: 2%;
      font-size: 200%;
      font-family: serif;
    }

    h2 {
      margin: 3% 0;
      font-size: 180%;
      font-family: serif;
    }

    h3 {
      font-size: 150%;
      font-family: serif;
    }
    ```

  * We adjusted the list element's left margin, set the `list-style` to be `square`, and changed the `font-family` to the default `monospace` font:

    ```css
    article ul {
      margin-left: 5%;
      list-style: square;
      font-family: monospace;
    }
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What CSS properties can you use to alter a font?

  * 🙋 `font-family`, `font-size`, `font-weight`, `font-style`, `text-decoration`, etc.

  * ☝️ Why is using a percentage for font sizes helpful?

  * 🙋 We only need to change the base font size to scale other elements accordingly.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [MDN Web Docs on text and font styling fundamentals](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text/Fundamentals), and stay for office hours to ask for help.

* Answer any questions before proceeding to flex time.

### 11. FLEX (20 mins)

* This time can be utilized for reviewing key topics learned so far in this unit.

### 12. BREAK (30 mins)

### 13. Instructor Demo: Pseudo-Classes (5 min) 

* Open `15-Ins_Pseudo-Classes/index.html` in your browser and demonstrate the following:

  * 🔑 With CSS, we can style the different states that an element can be in.

  * When you move the cursor over a button, it's in a **hover** state.

  * When you actively press the cursor down on a button, it's in an **active** state.

  * 🔑 When you've clicked on or tabbed into a button, it's in a **focus** state.

* Open `15-Ins_Pseudo-Classes/assets/css/style.css` in your IDE and explain the following:

  * 🔑 In CSS, we use pseudo-classes like `:hover` to capture these different states:

    ```css
    button:hover {
      background-color: #772014;
      color: #fff;
    }
    ```

  * In the `:focus` pseudo-class, we set the `outline` property to `none` to remove the browser's default highlight border:

    ```css
    button:focus {
      outline: none;
      border-color: #8ac4ff;
    }
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What do pseudo-classes allow you to do?

  * 🙋 Style the different states of an element.

  * ☝️ What are some of the states you could style?

  * 🙋 Hover, active, focus, etc.

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `16-Stu_Pseudo-Classes`.

### 14. Student Do: Pseudo-Classes (15 min) 

* Direct students to the activity instructions found in `16-Stu_Pseudo-Classes`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 🏗️ Implement an Interactive Resources List

  Work with a partner to implement the following user story:

  * As a user, I want additional resource links at the bottom of the article.

  ## Acceptance Criteria

  * It's done when the resource links are initially hidden on page load.

  * It's done when the user moves the mouse over the text "Show Resources," and the resource links display.

  ## Assets

  The following image demonstrates the web application's default appearance and functionality:

  ![The text "Show Resources" appears below an article titled "Building Responsive Layouts."](./Images/01-resources-closed.png)

  The following image demonstrates the web application's appearance and functionality when the cursor is over the "Show Resources" text:

  ![Three links to the MDN Web Docs appear under the text "Show Resources."](./Images/02-resources-open.png)

  You can use the following resource links for the content:

  * [MDN Web Docs on responsive design](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design)

  * [MDN Web Docs on using media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries)

  * [MDN Web Docs on flexbox](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox)
    
  ## 💡 Hints

  * How would the CSS `display` property help?

  * What examples can you find of other developers using the `:hover` pseudo-class in creative ways?

  ## 🏆 Bonus

  If you have completed the activity and want to further your knowledge, work through the following challenge with your partner:

  * How can you force pseudo-class styles to display using Chrome DevTools?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 15. Instructor Review: Pseudo-Classes (10 min) 

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with pseudo-classes? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points below to review the following key (🔑) points:

  * ✔️ `:hover` pseudo-class

  * ✔️ `display: none` vs `display: block`

* Open `16-Stu_Pseudo-Classes/Solved/index.html` in your IDE and explain the following: 

  * We added `<h3>` and `<ul>` elements inside of the resources `<div>`:

    ```html
    <div class="resources">
      <h3>
        Show Resources
      </h3>
      <ul class="links">
        <li>
          <a href="https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design">MDN Web Docs on responsive design</a>
        </li>
        <li>
          <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries">MDN Web Docs on using media queries</a>
        </li>
        <li>
          <a href="https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox">MDN Web Docs on flexbox</a>
        </li>
      </ul>
    </div>
    ```

* Open `16-Stu_Pseudo-Classes/Solved/assets/css/style.css` in your IDE and explain the following: 

  * 🔑 We initially set the `<ul>` element to `display: none` to remove it from the document flow:

    ```css
    .resources .links {
      display: none;
      padding: 1% 0;
    }
    ```

  * 🔑 When the parent `.resources` element is in a hover state, we change the `display` of the child `.links` element to `block`. This returns it to the document flow, but only while the parent is in its hover state:

    ```css
    .resources:hover .links {
      display: block;
    }
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ When is an element in a hover state?

  * 🙋 When the cursor is inside that element.

  * ☝️ What elements can have a `:hover` pseudo-class added to them?

  * 🙋 All the elements!

  * ☝️ What does `display: none` do to an element?

  * 🙋 It removes the element from the document flow.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [MDN Web Docs on pseudo-classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) and the [MDN Web Docs on display](https://developer.mozilla.org/en-US/docs/Web/CSS/display), and stay for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

### 16. Instructor Demo: Pseudo-Elements (5 min)

* Open `17-Ins_Psuedo-Elements/index.html` in your browser. Inspect the `<h1>` element with Chrome DevTools to demonstrate the following:

  * The only text in the `<h1>` element is "CSS".

  * 🔑 An `::after` pseudo-element has been added with CSS to insert extra content after the original content:

    ```css
    h1::after {
      font-family: Impact;
      content: 'Pseudo Elements';
      color: #8ac4ff;
      margin-left: 5px;
    }
    ```

* Inspect one of the `<h3>` elements with the Chrome DevTools to demonstrate the following:

  * 🔑 A `::before` pseudo-element has been added with CSS to insert extra content before the original content:

    ```css
    h3::before {
      font-family: Impact;
      content: '\273A';
      color: #772014;
      margin-right: 5px;
    }
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What are these pseudo-elements doing?

  * 🙋 Inserting extra content before or after the original content.

  * ☝️ How do pseudo-elements differ from pseudo-classes?

  * 🙋 Pseudo-elements change content; pseudo-classes change styles based on an element's state.

  * ☝️ What are some ways you could combine pseudo-classes and pseudo-elements?

  * 🙋 Display new content when an element is focused or hovered over.

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `18-Stu_Pseudo-Elements`.

### 17. Student Do: Pseudo-Elements (15 min) 

* Direct students to the activity instructions found in `18-Stu_Pseudo-Elements`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 📖 Implement a CSS Tooltip

  Work with a partner to implement the following user story:

  * As a user, I want to hover over keywords and read short info on them instead of having all of the text on the page.

  ## Acceptance Criteria

  * It's done when special keywords are underlined and change the cursor to a hand icon when the user hovers over them.

  * It's done when the user hovers over a keyword and a rectangular tooltip appears next to the keyword.

    * For example, if the keyword is "Cascading Style Sheets," the tooltip would say, "Commonly known as CSS."

  * It's done when the tooltip has the same background color and text color as the header and navbar items.

  ## 📝 Notes

  Refer to the following documentation: 

  [MDN Web Docs on ::after](https://developer.mozilla.org/en-US/docs/Web/CSS/::after)

  ## 💡 Hints

  * How can we use the `::after` pseudo-element along with the `:hover` and `:focus` selectors to create the tooltip?

  * How can you designate the keyword to use a `data-descr` custom data attribute for the tooltip text?

  ## 🏆 Bonus

  If you have completed the activity and want to further your knowledge, work through the following challenge with your partner:

  * What are some real-life scenarios for using pseudo-elements?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 18. Instructor Review: Pseudo-Elements (10 min) 

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel with pseudo-elements? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points (✔️):

  * ✔️ `data-*` attributes

  * ✔️ `::after` pseudo-elements

  * ✔️ Relative vs absolute positioning

* Open `18-Stu_Pseudo-Elements/Solved/index.html` in your IDE and explain the following: 

  * 🔑 We added a custom `data-descr` attribute to each `<span>` element to hold the hidden tooltip text:

    ```html
    <span data-descr="Commonly known as CSS">Cascading Style Sheets</span>
    ```

* Open `18-Stu_Pseudo-Elements/Solved/assets/css/style.css` in your IDE and explain the following:

  * 🔑 We selected every `<span>` element that has a `data-descr` attribute and set the `position` to `relative`. This will help us position the tooltip relative to the `<span>`:

    ```css
    span[data-descr] {
      position: relative;
      text-decoration: underline;
      color: #000;
      cursor: grab;
    }
    ```

  * 🔑 We combined the `::after` pseudo-element with `:hover` and `:focus` states to insert the tooltip. The content comes from the value of the `data-descr` attribute. The tooltip is positioned absolutely, but relative to its parent:

    ```css
    span[data-descr]:hover::after,
    span[data-descr]:focus::after {
      content: attr(data-descr);
      position: absolute;
      left: 0px;
      bottom: 24px;
      min-width: 200px;
      border: 1px #aaaaaa solid;
      background-color: #13293d;
      padding: 12px;
      color: #fff;
      font-size: 80%;
      z-index: 1;
    }
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ Why did the `<span>` element need relative positioning?

  * 🙋 Absolute positioning requires a positioned parent element.

  * ☝️ What purpose does the `data-descr` attribute serve?

  * 🙋 It holds hidden content that the pseudo-element will use later.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [MDN Web Docs on pseudo-elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements), and stay for office hours to ask for help.

* Answer any questions before proceeding to the next activity.

### 19. Instructor Demo: Custom Forms  (5 min) 

* Open `19-Ins_Form-Styles/index.html` in your browser. Use Chrome DevTools to demonstrate the following:

  * 🔑 HTML form elements have many default styles applied by the browser.

  * The `<input>` elements have a CSS declaration of `cursor: text`.

  * The `<select>` element has a CSS declaration of `appearance: menulist`.

  * 🔑 The `<button>` element has an `outline` property applied when you use DevTools to toggle the `:focus` state.

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How can you overwrite these browser defaults?

  * 🙋 Target the same element and property names with CSS.

* Answer any questions before proceeding to the next activity.

* In preparation for the activity, ask TAs to start directing students to the activity instructions found in `20-Stu_Custom-Forms`.

### 20. Student Do: Custom Forms (15 min) 

* Direct students to the activity instructions found in `20-Stu_Custom-Forms`.

* Break your students into pairs that will work together on this activity.

  ```md
  # 📐 Add Comments to Implementation of a Custom Form

  Work with a partner to add comments describing the functionality of the code found in [Unsolved/assets/css/style.css](./Unsolved/assets/css/style.css).

  ---

  ## 🏆 Bonus

  If you have completed the activity and want to further your knowledge, work through the following challenge with your partner:

  * What are ARIA attributes, and when would you need to use them?

  Use [Google](https://www.google.com) or another search engine to research this.
  ```

* While breaking everyone into groups, be sure to remind students and instructional staff that questions on Slack or otherwise are welcome and will be handled. It's a good way for your team to prioritize students who need extra help.

### 21. Instructor Review: Custom Forms (10 min) 

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ How comfortable do you feel customizing form elements with CSS? (Poll via Fist to Five, Slack, or Zoom)

* Assure students that we will cover the solution to help solidify their understanding. If questions remain, remind them to use office hours to get extra help!

* Use the prompts and talking points (🔑) below to review the following key points (✔️):

  * ✔️ Sibling selectors

  * ✔️ Vendor prefixes

  * ✔️ Additional pseudo-classes

* Open `20-Stu_Custom-Forms/Solved/assets/css/style.css` in your IDE and explain the following: 

  * 🔑 We set the `<select>` element's `appearance` to `none` and inserted a background image to replace the arrow that originally came with `appearance`. We used `-moz` and `-webkit` vendor prefixes to ensure this works for other browsers besides Chrome:

    ```css
    select {
      -moz-appearance: none;
      -webkit-appearance: none;
      appearance: none;
      background-image: url("../images/arrow.png");
      background-repeat: no-repeat;
      background-position: right;
      background-size: contain;
    }
    ```

  * We styled the focus and empty states of the `<input>` elements. An empty state can be captured with the `:placeholder-shown` pseudo-class:

    ```css
    .text-input:focus {
      border-right-width: 5px;
    }

    .text-input:placeholder-shown {
      border-style: dashed;
    }
    ```

  * 🔑 We used a sibling selector to alter the styles of an element that is next to another element. In this case, the `<label>` element is a sibling of the checkbox. The styles change when the checkbox is in a checked state:

    ```css
    .checkbox:checked + label {
      color: #999999;
      font-style: italic;
    }

    .checkbox:checked + label::after {
      margin-left: 10px;
      font-size: 90%;
      content: "(thanks!)";
    }
    ```

* Ask the class the following questions (☝️) and call on students for the answers (🙋):

  * ☝️ What does `appearance: none` do?

  * 🙋 Removes any special styling added by the browser.

  * ☝️ What did the `+` sign mean in the CSS selector?

  * 🙋 Select the adjacent, sibling element.

  * ☝️ How do you know what is and isn't possible with CSS?

  * 🙋 Read the documentation, look up examples, or experiment with DevTools.

  * ☝️ What can we do if we don't completely understand this?

  * 🙋 We can refer to supplemental material, read the [MDN Web Docs on appearance](https://developer.mozilla.org/en-US/docs/Web/CSS/appearance) and the [MDN Web Docs on combinators](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Combinators), and stay for office hours to ask for help.

* Answer any questions before proceeding.

### 22. FLEX (30 mins)

* This time can be utilized for reviewing key topics learned so far in this unit.

* Answer any questions before ending the class.

### 23. END (0 mins)

How did today’s lesson go? Your feedback is important. Please take 5 minutes to complete this [anonymous survey](https://forms.gle/RfcVyXiMmZQut6aJ6).

---
© 2021 Trilogy Education Services, LLC, a 2U, Inc. brand. Confidential and Proprietary. All Rights Reserved.

# My Portfolio

## Theme Switcher

This repository provides a simple theme switcher with an icon toggle feature using HTML, CSS, and JavaScript. The theme switcher allows users to switch between dark and light themes, and the button icon changes accordingly. The user's theme preference is also persisted using local storage.

## Explanation

The following explanation breaks down the functionality of the theme switcher code:

1. **Select Elements**: The `themeToggle` button and webpage `body` are identified.

   ```javascript
   const themeToggle = document.getElementById("theme-toggle");
   const body = document.body;
   ```

2. **Toggle Theme**: When the button is clicked, the webpage's theme is toggled.

   ```javascript
   themeToggle.addEventListener("click", () => {
     body.classList.toggle("dark");
     const isDarkMode = body.classList.contains("dark");
   });
   ```

3. **Update Button Icon**: The button's SVG icon is changed based on the current theme.
   ```javascript
   const themeToggle = document.getElementById("theme-toggle");
   ```
4. **Adjust Icon Color**: The SVG path color is modified for better visibility in dark mode.

   ```javascript
   function adjustSVGColor(isDarkMode) {
     const iconElement = themeToggle.querySelector("svg");
     iconElement
       .querySelector("path")
       .setAttribute("stroke", isDarkMode ? "#f5f5f5" : "currentColor");
   }
   ```

5. **Persist Theme**: The user's theme choice is stored in local storage.

   ```javascript
   localStorage.setItem("theme", isDarkMode ? "dark" : "light");
   ```

6. **Load Saved Theme**: On page load, the saved theme and icon color are applied.
   ```javascript
   const savedTheme = localStorage.getItem("theme");
   if (savedTheme) {
     body.classList.add(savedTheme);
     themeToggle.innerHTML = savedTheme === "dark" ? svgLight : svgDark;
     adjustSVGColor(savedTheme === "dark");
   }
   ```

## JS Code

Here's the main JavaScript code (from script.js) that powers the theme switcher:

```javascript
const themeToggle = document.getElementById("theme-toggle");
const body = document.body;

themeToggle.addEventListener("click", () => {
  body.classList.toggle("dark");
  const isDarkMode = body.classList.contains("dark");
  themeToggle.innerHTML = isDarkMode ? svgLight : svgDark;
  adjustSVGColor(isDarkMode);
  localStorage.setItem("theme", isDarkMode ? "dark" : "light");
});

function adjustSVGColor(isDarkMode) {
  const iconElement = themeToggle.querySelector("svg");
  iconElement
    .querySelector("path")
    .setAttribute("stroke", isDarkMode ? "#f5f5f5" : "currentColor");
}

const savedTheme = localStorage.getItem("theme");

if (savedTheme) {
  body.classList.add(savedTheme);
  themeToggle.innerHTML = savedTheme === "dark" ? svgLight : svgDark;
  adjustSVGColor(savedTheme === "dark");
}
```

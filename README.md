# Frontend Mentor - Product preview card component solution

This is a solution to the [Product preview card component challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/product-preview-card-component-GO7UmttRfa). Frontend Mentor challenges help you improve your coding skills by building realistic projects.

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
Q     - [Project structure](#project-structure)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
  - [AI Collaboration](#ai-collaboration)
- [Running the project](#running-the-project)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

## Overview

### The challenge

Users should be able to:

- View the optimal layout depending on their device's screen size
- See hover and focus states for interactive elements Like the 'add to cart button'.

### Screenshot

![Screenshot](./design/screenshot.png)

### Links

- Solution URL: Not submitted yet
- Live Site URL: Not published yet

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Fluid `rem` sizing with `clamp()`
- Media query for portrait screens
- [Google Fonts](https://fonts.google.com/) - Montserrat and Fraunces

### Project structure

```text
product-preview-card-component-main/
├── design/            # Desktop and mobile design references
├── images/            # Product photos, cart icon, and favicon
├── index.html         # Page markup
├── style.css          # Layout, typography, colors, and responsive styles
├── style-guide.md     # Colors, fonts, and sizes from the challenge
├── README-template.md
└── README.md
```

### What I learned

**Centering a card in the middle of the screen when a footer is present.**
The `body` is a grid, and the footer counted as a second grid item, so the card was only centered inside the top half of the page. Giving the page three rows and placing the card in the middle one fixed it, while the footer stays at the bottom:

```css
body {
  display: grid;
  place-items: center;
  grid-template-rows: 1fr auto 1fr;
  min-height: 100vh;
}

main {
  grid-row: 2;
}

.attribution {
  grid-row: 3;
  align-self: end;
}
```

**Scaling the whole layout with one value.**
All sizes use `rem`, so changing the root font size scales the card. It stays at 16px up to a 1440px screen, which matches the design, and grows slightly on larger screens:

```css
html {
  font-size: clamp(1rem, 0.5rem + 0.55vw, 1.5rem);
}
```

**Swapping the product image for portrait screens without changing the HTML.**
The card stacks in portrait orientation, and `content: url()` on the image loads the mobile photo. In browsers that ignore it, `object-fit: cover` keeps the desktop photo cropped neatly:

```css
@media (orientation: portrait) {
  main {
    flex-direction: column;
    max-width: 21.875rem;
  }

  .product {
    width: 100%;
    height: 21.375rem;
    content: url(./images/image-product-mobile.jpg);
  }
}
```

**Keeping fonts and colors in variables.**
The colors from the style guide and two font stacks (`--font-body` and `--font-display`) are defined once in `:root` and reused across the stylesheet.

### Continued development

- Use a `<picture>` element for the product image, which is the more reliable and semantic way to serve different images by screen size.
- Add self-hosted font files so the page keeps its fonts offline.
- Switch the layout breakpoint from `orientation: portrait` to a width-based media query, so narrow desktop windows also get the stacked layout.
- Test the full range of screen sizes from 320px up, as the style guide recommends.

### Useful resources

- [MDN: clamp()](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp) - Helped me set a fluid root font size with a minimum and a maximum.
- [MDN: grid-template-rows](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-rows) - Helped me build the three-row page layout that centers the card.
- [MDN: orientation media feature](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/orientation) - Reference for the portrait media query.

### AI Collaboration

I used Claude to help with the CSS mobile responsiveness and fonts.

- **How I used it:** matching the styles to the desktop and mobile designs, converting sizes to `rem`, setting up the font variables.

## Running the project

Open `index.html` in a browser. No build tools or package installation are required. An internet connection is needed to load the fonts from Google Fonts.

## Author

- Frontend Mentor - [@OMS-Create](https://www.frontendmentor.io/profile/OMS-Create)

## Acknowledgments

Thanks to [Frontend Mentor](https://www.frontendmentor.io/) for the challenge and the supplied design assets.
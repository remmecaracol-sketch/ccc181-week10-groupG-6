# CCC181 Week 10: CampusConnect Mobile-First Login Page

React + TypeScript starter for the Week 10 group activity. The page is already
built. Your group's job is the **mobile-first CSS** and the **GitHub teamwork**.

## Run it

```bash
npm install
npm run dev          # open the local URL it prints
npm run dev:phone    # same, but your phone (same Wi-Fi) can open the Network URL
npm run build        # must finish with no errors before you submit
```

## Rules

- Edit only the CSS files in `src/styles/` (one member = one file). Do not edit `reset.css`.
- Plain CSS only. No Tailwind, Bootstrap, Material UI, styled-components, or any UI library.
- Phone styles first (no media query), then `min-width` queries only. Never `max-width`.
- Do not edit the `.tsx` files or rename classes. If you must, tell the group first.

## Group information (fill in)

| Item | Your answer |
| --- | --- |
| Group Number| Group-6 |
| Section | IT3-B |
| Repository URL| https://github.com/remmecaracol-sketch/ccc181-week10-groupG-6.git |

## Members (each member fills in their own row in their own commit)

| Member | Name | GitHub username | CSS file | What I did |
| --- | --- | --- | --- | --- |
| 1 |Remme Caracol |  remmecaracol-sketch| base.css | Added the viewport meta tag, wrote base.css (mobile-first base styles), and did Experiment 0| 
| 2 |Jessabel M. Janolino | jessabeljanolino-hash|  nav.css | Wrote nav.css (Flexbox navbar + CSS Grid footer, responsive at 768px and 1024px)|
| 3 |Gail H. Pagutayao| devbygail| form.css | Wrote form.css|

## Experiment 0: the page without the viewport tag

What did the page look like in DevTools phone mode **before** adding the viewport meta tag?
What changed **after** adding it?

> **Before:** The browser treated the phone as a ~980px-wide screen, so the page was scaled down and looked zoomed out. Reading anything required pinching to zoom.
> 
> **After:** The viewport tag told the browser to use `width=device-width`, so the page rendered at 360px at 100% scale. The text was clear, no zooming was needed, and the layout fit the phone screen.

## DevTools test results

| Width | What must be true | Pass? |
| --- | --- | --- |
| 360 px | 1 column. Nav links stacked and 48px tall. Options and buttons stacked. Footer in 1 column. No sideways scrollbar. | Pass |
| 768 px | Nav in one row (brand left, links right). Checkbox and link in one row. Two buttons side by side. | Pass |
| 1024 px | Brand panel and login card side by side. Footer in 3 columns. Heading is larger. | Pass  |
| 1280 px | Content centered and stops at 1200px. | Pass |

### Breakpoints I observed

Using **Show media queries** and dragging slowly from 360 px to 1280 px, the layout changed at these exact widths:

Using **Show media queries** and dragging slowly from 360 px to 1280 px, the layout changed at these exact widths:

> The layout changed at **768 px**, **1024 px**, and **1280 px**.
> - **768 px:** the container got wider side padding (2rem) and the brand panel got more padding. The navigation moved into one row, and the checkbox row and the bottom buttons sat side by side.
> - **1024 px:** the brand panel and login card moved side by side in 2 columns. The heading grew to 2.5rem, the extra perks list appeared, and the footer changed to 3 columns.
> - **1280 px:** the container stopped at a max-width of 1200 px and stayed centered instead of stretching edge to edge.
>
> No width looked broken, and there was no sideways scrollbar at any width, even when the error messages were showing.

Screenshots are in `screenshots/` as `360.png`, `768.png`, `1024.png`, `1280.png`.




## What our group learned (leader writes this last)

> > We learned that mobile-first means writing the phone layout as the default and only adding `min-width` media queries as the screen gets wider, instead of shrinking a desktop design down. Without the viewport meta tag, the phone treated the page like a wide desktop screen, so none of our mobile styles worked properly. We also learned how Flexbox and Grid fit together: Flexbox for the navbar and form, and Grid for the page layout and footer. Working on one CSS file per member and merging through pull requests meant our code did not clash, and reviewing each other's work helped us catch mistakes before they reached `main`.

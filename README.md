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
| 360 px | 1 column. Nav links stacked and 48px tall. Options and buttons stacked. Footer in 1 column. No sideways scrollbar. | ✔ |
| 768 px | Nav in one row (brand left, links right). Checkbox and link in one row. Two buttons side by side. | ✔ |
| 1024 px | Brand panel and login card side by side. Footer in 3 columns. Heading is larger. | ✔  |
| 1280 px | Content centered and stops at 1200px. | ✔ |

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



## How to run?

backend
> # Part 2: Express backend login

## How to run

You need two terminals open at the same time.

**Terminal 1: backend (folder `server`)**

```bash
cd server
npm install
copy .env.example .env
npm start
```

You should see `API running on http://localhost:3000`.

**Terminal 2: front end (project root)**

```bash
npm install
copy .env.example .env
npm run dev
```

Open http://localhost:5173. The health check is http://localhost:3000/api/v1/health and must return `{"status":"ok"}`.

The real `.env` files are never committed. Only the two `.env.example` files (with fake values) are in the repo.

## API summary

| Method | Path | Success | Errors |
|---|---|---|---|
| GET | `/api/v1/health` | 200 `{"status":"ok"}` | none |
| POST | `/api/v1/sessions` | 200 `{token, user}` | 400 missing fields, 401 `Invalid email or password.` |
| GET | `/api/v1/users/me` | 200 user (needs `Authorization: Bearer <token>`) | 401 `Not logged in.` |

Other answers: unknown route is 404 `{"error":"Not found."}`, a crash is 500 `{"error":"Something went wrong."}`. Full details are in `docs/API-SPEC.md`. The Postman collection is in `docs/postman/CampusConnect.postman_collection.json`.

**Demo account:** `student@campusconnect.test` / `Campus26` (name: Demo Student)

## Who did what (Part 2)

| Member | Name | GitHub | What I did in Part 2 |
|---|---|---|---|
| 1 | Remme Caracol| remmecaracol-sketch | Created the server/ project with Express, dotenv, CORS, and JSON parsing. Implemented POST /api/v1/sessions, including input validation, bcryptjs password verification, a JWT valid for one hour, and the demo user with a hashed password. |
| 2 | Jessabel M. Janolino | jessabeljanolino-hash |Implemented GET /api/v1/users/me along with the token middleware and the 404 and 500 handlers. Wrote docs/API-SPEC.md (including the events design), assembled the Postman collection, and captured the Postman screenshots. Also reviewed Member 1’s pull request. |
| 3 | Gail H. Pagutayao | devbygail |Set up the frontend API address through the root .env and .env.example. Wrote login() and getMe() in src/api/auth.ts using fetch. Updated src/components/LoginForm.tsx to keep the client-side validation, stop invalid input from reaching the API, and handle the Loading, Success, and Error states. Built the Welcome screen that displays the name and email returned by the backend. Stored the token in sessionStorage, restored the login session on refresh via /api/v1/users/me, cleared invalid or expired tokens, and added Log out. Added browser console logging for outgoing request payloads, response statuses and data, and API errors to help with debugging, with passwords and tokens masked. Styled the new messages and Welcome screen in src/styles/auth.css and imported that stylesheet in src/main.tsx.|


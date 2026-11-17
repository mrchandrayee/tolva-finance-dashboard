# Tolva — Finance Workspace Dashboard Animation

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-blue?style=for-the-badge&logo=github)](https://mrchandrayee.github.io/tolva-finance-dashboard/)
[![HTML](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org) [![CSS](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org) [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)

Runnable HTML/CSS/JavaScript reconstruction of the uploaded **5.33-second** screen recording (720 × 1280, 30 fps).

## Run
1. Extract `tolva-finance-dashboard.zip`.
2. Open `index.html` in Chrome, Edge, Firefox or Safari.
3. Click the top navigation tabs to switch screens.
4. Use the buttons to try demo approval, bill, autopay and money-movement dialogs.

No npm install, build step, API key or backend is required.

Optional local server:
```bash
python3 -m http.server 8000
```
Open `http://localhost:8000`.

## What the video shows

A green and warm-ivory finance dashboard branded **tolva**, with a top navigation:
- Overview
- Autopay
- Bills (badge 6)
- Duty & tax (badge 2)
- Cash flow
- Reports
- Projects
- Suppliers

The header also shows add, search, time/activity, notification, user profile `Maren Oksøy · Finance lead`, and settings controls.

### Overview screen
Visible headline: **Morning, Maren**.

Top figures:
- Cash balance: **€223,278**
- Out this month: **€22,885**
- Safe to spend: **€104,351**

Main cards:
- Cash across 4 accounts, with a cash trend line.
- This week, with a weekly payment schedule.
- Pays itself: **77%**.
- Waiting for you: pending bill approvals.
- Where it went: spend categories.

### Autopay screen
Visible heading: **Automatic payments**.

Top figures:
- Cash balance: **€190,134** (84%)
- Paid this month: **€19,488**
- 19 rules a month: **€76,605**

Tabs: Rules, Run log, Pay-from.
Rule categories visible include All, Ingredients, Packaging, Cleaning, Premises, Payroll, Duty & tax, Utilities, Software and Equipment.
Example rule card: **Hop contract 2026**, with payment scheduling and account details.

### Cash flow screen
Visible heading: **Cash flow** and explanatory line about forecast using autopay rules and outstanding bills.

Forecast cards:
- Cash now: **€242,037**
- Lowest point: **€163,699**
- Scheduled out: **€281,616**
- In 13 weeks: **€163,699**

Tabs: Forecast and Accounts. Forecast includes a 13-week in/out chart. Accounts view lists Operating, Reserve, Duty pot and VAT pot.

### Other visible destinations
Bills, Duty & tax, Reports, Projects and Suppliers appear in the top navigation. The short clip does not show their full detailed screens; these have been given reasonable matching demo views, not represented as source-transcribed layouts.

## Readable original TypeScript code from the video

The lower source panel is labelled `src/motion.ts`. The visible function is a GSAP helper for animating a clipped navigation pill. The readable excerpt (formatting normalized) is:

```ts
export function slidePill(pill: HTMLElement, target: HTMLElement) {
  const box = pill.parentElement!, W = box.offsetWidth;
  const H = box.offsetHeight;
  const to: Edges = {
    l: target.offsetLeft, t: target.offsetTop,
    r: W - (target.offsetLeft + target.offsetWidth),
    b: H - (target.offsetTop + target.offsetHeight)
  };
  const st = (pill as PillHost).__st ??= ...;
  const clip = (e: Edges) =>
    `inset(${e.t}px ${e.r}px ${e.b}px ${e.l}px round 13px)`;
  const paint = () => gsap.set(pill, { clipPath: clip(st) });
  const [lead, trail] = to.t > st.t ? ['t', 'b'] : ['b', 't'];
  gsap.to(st, { [lead]: to[lead], duration: 0.36,
    ease: 'power3.out', onUpdate: paint });
  gsap.to(st, { [trail]: to[trail], duration: 0.55,
    ease: 'power3.inOut', onUpdate: paint });
}
```

The line assigning `st` is partially obscured/too small after `??=`; its missing right-hand expression is intentionally not guessed. `Edges`, `PillHost`, and surrounding setup are also not fully visible. The supplied runnable project uses a CSS/JavaScript pill transition inspired by the visible motion helper, rather than requiring GSAP.

## Included functionality
- Interactive top navigation with active pill movement.
- Overview, Autopay, Bills, Cash flow and supporting destination screens.
- 13-week cash forecast chart and account list toggle.
- Bill filters: All, To approve, Scheduled, Paid.
- Autopay rule category chips and tab controls.
- New bill, upload bill, new autopay rule and move-money dialogs.
- Search navigation.
- Responsive layout for smaller screens.
- Toast feedback for demo actions.

## Files
- `index.html` — application shell and navigation.
- `styles.css` — green/ivory dashboard visual system, charts, cards, responsive layout.
- `app.js` — sample financial data, screens, navigation and interactions.
- `README.md` — screen observations, code extraction and run guide.

## Limitations
This is a frontend-only recreation. Financial figures are demo values transcribed from the visible video where legible; secondary records and screens are illustrative. No bank connection, accounting integration, payment execution, invoice OCR, supplier API or real financial data is connected. All approval, upload, autopay and money movement actions are simulated locally.

## 👨‍💻 Author

**mrchandrayee** · [GitHub](https://github.com/mrchandrayee)

## 📄 License

[MIT License](./LICENSE)

# RetireReady — Retirement Savings Calculator

A clean, single-page retirement planning calculator. No backend, no build tools, no dependencies to install. Just one HTML file.

---

## What It Does

- Calculates the total nest egg needed to retire based on your expenses, Social Security, and inflation
- Calculates the required monthly contribution to reach that goal
- Displays a projected portfolio growth chart
- Requires an email address to export a formatted PDF report (collected via Formspree)

---

## Tech Stack

- HTML / CSS / Vanilla JavaScript
- [Chart.js](https://www.chartjs.org/) — portfolio projection chart
- [jsPDF](https://github.com/parallax/jsPDF) — client-side PDF generation
- [Formspree](https://formspree.io) — email collection (no backend required)

---

## Setup

### 1. Configure Formspree

1. Create a free account at [formspree.io](https://formspree.io)
2. Create a new form and copy your form ID
3. In `index.html`, find this line and replace the placeholder:

```js
const FORMSPREE_URL = 'https://formspree.io/f/YOUR_FORM_ID';
```

### 2. Deploy to DigitalOcean Static Apps

1. Push this repo to GitHub
2. In DigitalOcean, go to **App Platform → Create App**
3. Connect your GitHub repo
4. Use these settings:
   - **Build command:** *(leave empty)*
   - **Output directory:** `/`
   - **Environment:** Static Site
5. Click **Deploy**

DigitalOcean will automatically redeploy on every push to your main branch.

---

## Local Development

No build step needed. Just open the file in a browser:

```bash
open index.html
```

Or serve it locally:

```bash
npx serve .
```

---

## Financial Logic

| Variable | Formula |
|---|---|
| Net Monthly Need | Total Expenses − Temporary Expenses − Social Security |
| Future Monthly Need | Net Monthly × (1 + Inflation)^Years |
| Total Needed | Future Monthly × 12 × 25 *(4% rule)* |
| Monthly Contribution | Standard future value of annuity formula |

All outputs are expressed in **future dollars**.

---

## Planned Enhancements

- [ ] Adjustable retirement duration
- [ ] Real vs. nominal return toggle
- [ ] Dark mode
- [ ] Monte Carlo simulation

---

> **Disclaimer:** This tool is for educational purposes only and does not constitute financial advice. Consult a licensed financial advisor for personalized guidance.

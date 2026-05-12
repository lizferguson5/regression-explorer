# BioReg — Linear Regression Explorer

An interactive, browser-based tool for biostatistics students to explore linear regression visually — including residual plots, R² decomposition, sum of squares, and model diagnostics — using real biological datasets.

🔗 **[Access the App](https://lizferguson5.github.io/regression-explorer/)**

---

## Overview

Most introductory statistics courses teach students *how* to run a linear regression, but not *how to critically evaluate* whether the model is appropriate. This tool bridges that gap by making the diagnostic process visual and interactive.

Every statistic — the regression equation, R², p-value, confidence interval, sum of squares breakdown — is computed live in the browser from the selected dataset. Students can toggle visual overlays, click individual data points, and switch between datasets that each demonstrate a different real-world modeling scenario.

---

## Intended Audience

Undergraduate and graduate students in:

- Introductory **Biostatistics**
- **Ecology** and environmental science
- **Biological research methods** or experimental design courses

No statistics software or installation required. Runs entirely in any modern web browser.

---

## Datasets

| Dataset | Biological Context | Key Lesson |
|---|---|---|
| 🦗 **Cricket Chirps** | Chirp rate vs. temperature in *Oecanthus fultoni* | A well-behaved residual plot — what "good" looks like |
| 🌱 **Plant Growth** | Shoot height vs. nitrogen in *Arabidopsis thaliana* | Heteroscedasticity — variance grows with the predictor |
| 🐟 **Fish Allometry** | Body weight vs. length in bluegill sunfish | High R² but a curved residual plot — the model is wrong |

---

## Features

- **Interactive scatter plot** with toggleable residual lines and mean ȳ overlay
- **Residual plot** with automated pattern detection and biological interpretation for each dataset
- **R² decomposition canvas** — click any data point to see SST, SSR, and SSE drawn geometrically with a live formula
- **Full statistics panel** — R², Pearson r, sum of squares table, standard error of estimate, p-value, t-statistic, 95% confidence interval for slope, and sample size
- **Residual plot interpretation guide** — four annotated pattern panels (random scatter, curved/U-shape, fan/funnel, outlier) with biological guidance on next steps
- Responsive layout — works on desktop and tablet

---

## Things to Explore

**Start with Cricket Chirps.** The residual plot shows points scattered randomly above and below zero with constant spread throughout the range — this is the benchmark for a well-fitting linear model. Notice that R² is around 0.75, not 0.99. In ecology, that is realistic and meaningful: temperature drives chirp rate, but humidity, individual variation, and time of day all play a role too.

**Switch to Plant Growth.** The trend looks convincing in the scatter plot, but examine the residual plot. The spread fans out as nitrogen increases — that is heteroscedasticity. The model's uncertainty is not constant; predictions at high nitrogen are far less reliable than at low nitrogen. Ask: would you report a single prediction interval at 130 mg/L with the same confidence as one at 10 mg/L?

**Open Fish Allometry.** R² is high and p is tiny — on paper this looks like an excellent model. But the residual plot shows a clear U-shaped arc: small and large fish are consistently under-predicted while mid-sized fish are over-predicted. The linear model is using the wrong mathematical form. Fish weight scales with the *cube* of length (W ∝ L³), so a log-log transformation is the appropriate fix. This dataset is the central argument for why residual plots are non-negotiable.

**Use the toggles** on the scatter plot to show and hide the residual lines (vertical distance from each point to the line) and the mean ȳ dashed line.

**Click any data point** on the scatter plot to update the R² decomposition diagram. The green band (SSR) and red band (SSE) shift in real time, and the formula R² = SSR ÷ SST recalculates to match.

---


## Technical Notes

- Pure HTML, CSS, and vanilla JavaScript — no frameworks, no build step
- Uses [Chart.js 4.4](https://www.chartjs.org/) (loaded from CDN) for scatter and residual charts
- R² decomposition diagram rendered on an HTML5 Canvas element
- All regression math (slope, intercept, SST/SSR/SSE, SE, t-statistic, p-value via regularized incomplete beta, 95% CI) computed from scratch in-browser
- Google Fonts loaded for typography (Crimson Pro, Mulish, Fira Code)

---

## License

MIT — free to use, adapt, and share for educational purposes.

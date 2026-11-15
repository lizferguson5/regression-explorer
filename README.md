# BioReg — Linear Regression Explorer

An interactive, browser-based tool for biostatistics students to explore linear regression visually — including residual plots, residual distributions, R² decomposition, sum of squares, and model diagnostics — using realistic biological datasets **or data collected by your own class**.

🔗 **[Regression Explorer](https://lizferguson5.github.io/regression-explorer/)**

---

## Overview

Most introductory statistics courses teach students *how* to run a linear regression, but not *how to critically evaluate* whether the model is appropriate. This tool bridges that gap by making the diagnostic process visual and interactive.

Every statistic — the regression equation, R², p-value, confidence interval, sum of squares breakdown, and assumption tests — is computed live in the browser from the selected dataset. Students can toggle visual overlays, click individual data points, switch between datasets that each demonstrate a different modeling scenario, and then load their own class data and step through the complete analysis.

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
| 🦗 **Cricket Chirps** | Chirp rate vs. temperature in the snowy tree cricket *Oecanthus fultoni* (n = 28) | A well-behaved residual plot — what "good" looks like |
| 🌱 **Plant Growth** | Shoot height vs. nitrogen in *Arabidopsis thaliana* (8 levels × 4 plants) | Heteroscedasticity — variance grows with the predictor |
| 🐟 **Fish Allometry** | Body weight vs. length in bluegill sunfish (n = 36) | High R² but a curved residual plot — the model is wrong |
| 📋 **Your Class Data** | Anything your class measures | Apply the full workflow to real data you collected |

The three example datasets are **simulated** from published biological relationships (Dolbear's law for crickets; a log-normal nitrogen response for *Arabidopsis*; the length–weight power law W = 0.0135·L^3.1 for bluegill) with random error added, so the residuals scatter the way real data do rather than following artificial patterns.

---

## Using Your Class Data

1. Click the **📋 Your Class Data** tab.
2. Enter a study title, the **predictor (x)** and **response (y)** variable names, and their units.
3. Add data in any of three ways:
   - **Paste** two or more columns copied straight from Excel or Google Sheets (tab-, comma-, semicolon- or space-separated; a header row is optional), or
   - **Upload** a `.csv`, `.tsv`, `.txt`, `.xlsx`, or `.xls` file (for Excel files with several sheets, choose the sheet), or
   - Click **Download template** to get a blank CSV for students to fill in.
4. Choose which columns are x and y. A preview table shows the selected columns; rows with missing or non-numeric values are skipped and shown struck through.
5. Click **Run analysis** and work through the **Guided Analysis** steps.

Data never leave the student's browser. The last dataset entered is remembered on that device (via local storage) so a page refresh doesn't lose work. Click **Load example** to see a sample hand-span vs. height class dataset.

---

## Features

- **Guided Analysis** — a 7-step walkthrough (look at the data → fit the line → residuals → R² → check assumptions → test the slope → write a conclusion) whose text is filled in with the live numbers for whichever dataset is loaded, ending with a copyable, journal-style results sentence
- **Interactive scatter plot** with toggleable residual lines and mean ȳ overlay
- **Residual plot** with interpretation; outlying or influential points are outlined
- **Distribution of residuals** — histogram of standardized residuals with a normal curve, or a normal Q–Q plot
- **Assumption checks** computed from the residuals: linearity (quadratic-trend test), constant variance (Glejser test), normality (Shapiro–Wilk), outliers and influence (standardized residuals, Cook's distance), plus a reminder about independence
- **R² decomposition canvas** — click any data point to see SST, SSR, and SSE drawn geometrically with a live formula
- **Full statistics panel** — R², Pearson r, sum of squares table, standard error of estimate, p-value, t-statistic, 95% confidence interval for slope, and sample size
- **Residual plot interpretation guide** — four annotated pattern panels (random scatter, curved, fan, outlier) with guidance on next steps
- Responsive layout — works on desktop, tablet, and phone

---

## Things to Explore

**Start with Cricket Chirps.** The residual plot shows points scattered randomly above and below zero with constant spread throughout the range — this is the benchmark for a well-fitting linear model. Notice that R² is about 0.77, not 0.99. In ecology, that is realistic and meaningful: temperature drives chirp rate, but humidity, individual variation, and time of day all play a role too.

**Switch to Plant Growth.** The trend looks convincing in the scatter plot, but examine the residual plot. The spread fans out as nitrogen increases — that is heteroscedasticity. The model's uncertainty is not constant; predictions at high nitrogen are far less reliable than at low nitrogen. Ask: would you report a prediction at 140 mg/L with the same confidence as one at 10 mg/L?

**Open Fish Allometry.** R² is high and p is tiny — on paper this looks like an excellent model. But the residual plot shows a clear U-shaped arc: small and large fish are consistently under-predicted while mid-sized fish are over-predicted. The linear model is using the wrong mathematical form. Fish weight scales with the *cube* of length (W ∝ L³), so a log-log transformation is the appropriate fix. The straight line even predicts *negative* weights for the smallest fish. This dataset is the central argument for why residual plots are non-negotiable.

**Switch the residual distribution** between the histogram and the Q–Q plot. The fish residuals are right-skewed; the cricket residuals look roughly normal.

**Try your own data.** Have students measure something (hand span vs. height, leaf length vs. width, pulse before vs. after exercise), paste it into the Your Class Data tab, and step through the Guided Analysis.

**Use the toggles** on the scatter plot to show and hide the residual lines (vertical distance from each point to the line) and the mean ȳ dashed line.

**Click any data point** on the scatter plot to update the R² decomposition diagram. The green band (SSR) and red band (SSE) shift in real time, and the formula R² = SSR ÷ SST recalculates to match.

---

## How to Host on GitHub Pages

1. Go to your repository at [github.com/lizferguson5/regression-explorer](https://github.com/lizferguson5/regression-explorer)
2. Make sure `index.html` is in the root of the `main` branch
3. Go to **Settings → Pages**
4. Under *Branch*, select **main** and folder **/ (root)**, then click **Save**
5. Your site will be live at `https://yourusername.github.io/repository-name/` within 1–2 minutes

---

## Technical Notes

- Pure HTML, CSS, and vanilla JavaScript — no frameworks, no build step
- Uses [Chart.js 4.4](https://www.chartjs.org/) (loaded from CDN) for scatter, residual, and distribution charts
- Excel files are read with [SheetJS](https://sheetjs.com/), loaded from CDN only when an Excel file is uploaded
- R² decomposition diagram rendered on an HTML5 Canvas element
- All regression math (slope, intercept, SST/SSR/SSE, SE, t-statistic, p-value via regularized incomplete beta, 95% CI) and diagnostics (Shapiro–Wilk via Royston's approximation, Glejser test, quadratic-trend test, leverage, Cook's distance) computed from scratch in-browser; results were checked against SciPy
- Google Fonts loaded for typography (Crimson Pro, Mulish, Fira Code)

---

## License

MIT — free to use, adapt, and share for educational purposes.

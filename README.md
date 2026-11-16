# BioReg — Linear Regression Explorer

An interactive, browser-based tool for biostatistics students to explore linear regression visually — including residual plots, residual distributions, R² decomposition, sum of squares, and model diagnostics — using realistic biological datasets, a data simulator, **or data collected by your own class**.

🔗 **[Open the Regression Explorer](https://lizferguson5.github.io/regression-explorer/)**

---

## Overview

Most introductory statistics courses teach students *how* to run a linear regression, but not *how to critically evaluate* whether the model is appropriate. This tool bridges that gap by making the diagnostic process visual and interactive.

Every statistic — the regression equation, R², p-value, confidence interval, sum of squares breakdown, and assumption tests — is computed live from the data on screen. Students can explore example datasets that each demonstrate a different modeling scenario, generate their own data with sliders, and then load data collected in class and step through the complete analysis.

---

## Intended Audience

Undergraduate and graduate students in:

- Introductory **Biostatistics**
- **Ecology** and environmental science
- **Biological research methods** or experimental design courses

No statistics software, installation, or account is required. The tool runs in any modern web browser on a laptop, tablet, or phone.

---

## Datasets

| Dataset | Biological Context | Key Lesson |
|---|---|---|
| 🦗 **Cricket Chirps** | Chirp rate vs. temperature in the snowy tree cricket *Oecanthus fultoni* (n = 28) | A well-behaved residual plot — what "good" looks like |
| 🌱 **Plant Growth** | Shoot height vs. nitrogen in *Arabidopsis thaliana* (8 levels × 4 plants) | Heteroscedasticity — variance grows with the predictor |
| 🐟 **Fish Allometry** | Body weight vs. length in bluegill sunfish (n = 36) | High R² but a curved residual plot — the model is wrong |
| 🎛️ **Simulator** | Data students generate with sliders | See how noise, curvature, unequal spread, error shape, and outliers change the fit and the residuals |
| 📋 **Your Class Data** | Anything your class measures | Apply the full workflow to real data you collected |

The three example datasets are **simulated** from published biological relationships (Dolbear's law for crickets; a nitrogen response with proportional error for *Arabidopsis*; the length–weight power law W = 0.0135·L^3.1 for bluegill) with random error added, so the residuals scatter the way real data do.

---

## How the Tool Is Organized

- **Dataset tabs** across the top switch between the examples, the Simulator, and Upload Your Class Data.
- **The panel on the right** holds the controls for whichever tab is open — the dataset description, the simulator sliders, or the class-data form — plus a live summary (equation, R², p-value, n, and any assumption warnings). Students change something on the right and watch the plots on the left respond.
- **The analysis runs down the page in 7 numbered steps.** Each step has a "What to look for" guide written with the live numbers, and a **Next** button that scrolls to the following step:
  1. Data & residuals — scatter plot and residual plot side by side
  2. The regression equation
  3. Partitioning variation (R²)
  4. Checking the assumptions — and what to do if one fails
  5. Model statistics and the slope test
  6. Writing a conclusion — a journal-style results sentence students can copy
  7. Reference guide to residual-plot patterns
- **An About pop-up** introduces the tool on a student's first visit and can be reopened any time from the ⓘ button.

---

## Using Your Class Data

1. Click the **📋 Upload Your Class Data** tab.
2. In the panel on the right, enter a study title, the **predictor (x)** and **response (y)** variable names, and their units.
3. Add data in any of three ways:
   - **Paste** two or more columns copied straight from Excel or Google Sheets (a header row is optional), or
   - **Upload** a `.csv`, `.tsv`, `.txt`, `.xlsx`, or `.xls` file (for Excel files with several sheets, choose the sheet), or
   - Click **Download template** to get a blank CSV for students to fill in.
4. Choose which columns are x and y. A preview table shows the selected columns; rows with missing or non-numeric values are skipped and shown struck through.
5. Click **Run analysis** and work down the numbered steps.

Click **Load example** to see a sample hand-span vs. height class dataset.

**Privacy:** data never leave the student's device — nothing is uploaded to a server. The last dataset entered is remembered in that browser so a page refresh doesn't lose work, and **Clear** removes it.

---

## Features

- **Regression Simulator** — sliders for sample size, true slope, noise, curvature, unequal spread, error-distribution shape, and an optional outlier (inside or far beyond the x range). Every plot and statistic updates instantly, the true relationship is drawn alongside the fitted line, and scenario buttons (ideal, very noisy, no relationship, tiny sample, curved, fan, skewed, influential outlier) jump straight to classic cases. A "What to notice" box explains what changed — for example, whether the 95% confidence interval captured the true slope.
- **Side-by-side scatter plot and residual plot** — click a point in either to highlight it in both; toggle residual lines and the mean ȳ line.
- **Distribution of residuals** — histogram of standardized residuals with a normal curve, or a normal Q–Q plot.
- **Assumption checks** computed from the residuals: linearity, constant variance, normality (Shapiro–Wilk), outliers and influence (standardized residuals, Cook's distance), plus a reminder about independence.
- **What to do if an assumption fails** — two specific options tailored to the data: a model-based approach first (e.g., nonlinear power, exponential, or Michaelis–Menten curves; Poisson, negative-binomial, or gamma GLMs; weighted least squares; Spearman correlation with a Theil–Sen slope; robust regression), and a specific transformation second (e.g., log–log, semi-log, log x, √y), with example R code. A summary table appears in Step 7.
- **R² decomposition** — click any data point to see SST, SSR, and SSE drawn geometrically with a live formula.
- **Full statistics** — R², Pearson r, sum of squares table, standard error of the estimate, t-statistic, p-value, 95% confidence interval for the slope, and sample size.
- **Residual-pattern guide** — four example residual plots (random scatter, curved, fan, outlier) with guidance on next steps.

---

## Things to Explore

**Start with Cricket Chirps.** The residual plot shows points scattered randomly above and below zero with constant spread throughout the range — the benchmark for a well-fitting linear model. Notice that R² is about 0.77, not 0.99. In ecology, that is realistic and meaningful: temperature drives chirp rate, but individual variation and other conditions play a role too.

**Switch to Plant Growth.** The trend looks convincing in the scatter plot, but the residual plot fans out as nitrogen increases — heteroscedasticity. Predictions at high nitrogen are far less reliable than at low nitrogen. Ask: would you report a prediction at 140 mg/L with the same confidence as one at 10 mg/L?

**Open Fish Allometry.** R² is high and p is tiny — on paper this looks like an excellent model. But the residual plot shows a clear U-shaped arc: small and large fish are under-predicted while mid-sized fish are over-predicted. Fish weight scales with roughly the *cube* of length (W ∝ L³), so a straight line is the wrong shape; a nonlinear power-curve model (or, alternatively, a log–log regression) fits properly. The straight line even predicts *negative* weights for the smallest fish. This dataset is the central argument for why residual plots are non-negotiable.

**Compare the residual distributions** using the histogram and Q–Q plot. The fish residuals are right-skewed; the cricket residuals look roughly normal.

**Play with the Simulator.** Drag the noise slider and watch R² fall while the true slope stays the same. Add curvature or a fan and see how quickly the residual plot reveals it. Add an outlier far beyond the x range and watch it drag the fitted line away from the true one.

**Try your own data.** Have students measure something (hand span vs. height, leaf length vs. width, body mass vs. wingspan), upload it, and work through the seven steps.

---

## Classroom Worksheet

A ready-to-use **[student worksheet](worksheets/BioReg_Student_Worksheet.docx)** (Word, 4 pages) guides students through the tool with eight short questions — two for each example dataset and two using the Simulator. Each question gives exact click-by-click steps, a small table to record values, and a simple question to answer from the results. It is designed for introductory biology students and takes about 30–40 minutes.

| Part | Questions | Concept |
|---|---|---|
| Cricket Chirps | 1–2 | Reading a good residual plot; interpreting the slope |
| Plant Growth | 3–4 | Spotting unequal spread; choosing a remedy |
| Fish Allometry | 5–6 | Why a high R² isn't enough; impossible predictions |
| Simulator | 7–8 | How noise affects R²; how one outlier can change the slope |

The worksheet is an editable Word file, so you can adapt questions to your course. An **answer key** with the expected values is available to instructors on request. Every student sees the same numbers, because the example datasets are fixed and the Simulator scenario buttons always load the same sample.

---

## Requirements

- Any modern web browser (Chrome, Edge, Firefox, Safari)
- An internet connection when the page loads (for the charting library and fonts)

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

Copyright (c) 2026 Liz Ferguson

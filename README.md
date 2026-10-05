# ISCTE Nowcasting — Unemployment Rate

Final project at ISCTE (2021). A six-person group was asked by Instituto Nacional de Estatística (INE) to build a **nowcasting model for the Portuguese unemployment rate** — estimating the current rate before official figures are published, using higher-frequency signals.

Group: Ivan Gonzalez, Miguel Palmeira, Afonso Bessone, Manuel Oom, Miguel Teodoro, Gonçalo Almeida.

## Approach
1. **Literature** — reviewed prior nowcasting studies (e.g. Ettredge et al. 2005; Koop 2013; Bańbura et al. 2013).
2. **Data** — because the official unemployment series is short, we used **Google Trends** query volumes (notably searches for *"desemprego"*) as leading indicators (`Get_Data.ipynb`).
3. **Cleaning & analysis** — stationarity testing (Augmented Dickey-Fuller) and transformations, plus exploratory analysis of the "desemprego" series and its top related queries (`Project_Main.ipynb`).
4. **Modelling** — a **Dynamic Factor Model (DFM)** (estimated with a Kalman filter, `fkf` in R) and a **VAR**, benchmarked against an **AR** baseline.

## Results
Out-of-sample fit of the benchmark models (deck, "resultados finais"):

| Model | R² | MSE |
|---|---|---|
| AR (baseline) | 0.183 | 0.043 |
| VAR | 0.428 | 0.029 |
| DFM | see final results slide |

VAR more than doubled the AR baseline's R² and roughly halved its MSE. The DFM comparison is shown as a chart on the final results slide of `Presentation.pptx`.

## Contents
| Path | What |
|---|---|
| `Get_Data.ipynb` | Pulls Google Trends series and saves to `Data/`. |
| `Project_Main.ipynb` | Cleaning, ADF tests, analysis, and the DFM/VAR/AR models. |
| `Data/` | Fetched data (Google Trends indicators, INE unemployment series, DFM estimates). |
| `Presentation.pptx` | Deck presented to the teacher and the INE representative. |

## Stack
Python (pandas, statsmodels, matplotlib) + Jupyter for data and analysis; R (`fkf`) for the Kalman-filter DFM estimation.

## Notes
- Group academic project; data is public (Google Trends, INE).
- Some notebook and deck commentary is in Portuguese.

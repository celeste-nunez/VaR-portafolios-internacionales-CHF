# VaR-portafolios-internacionales-CHF
VaR, CVaR y VaR Estresado al 97.5% de dos portafolios de índices globales valuados en CHF, por Simulación Histórica, Monte Carlo y método Paramétrico. Modelo en Excel.

# Valor en Riesgo (VaR) de portafolios internacionales en CHF

Medición del riesgo de mercado de dos portafolios de índices bursátiles internacionales, valuados en francos suizos (CHF), mediante tres metodologías de VaR y su versión estresada. Todo el modelo está construido en Excel con fórmulas (sin macros), de modo que cada cálculo es rastreable celda por celda.

## Herramientas

  - Microsoft Excel

## Portafolios

Cada portafolio tiene un valor de **P = 100,000,000 CHF**.

| Posición | Portafolio 1 | Portafolio 2 | Monto (CHF) |
|---|---|---|---|
| 1 | Nikkei 225 (`N225`) | S&P500 (`GSPC`) | 15,000,000 |
| 2 | Hang Seng (`HSI`) | DAX (`GDAXI`) | 20,000,000 |
| 3 | Shenzhen (`399001.SZ`) | FTSE 100 (`FTSE`) | 25,000,000 |
| 4 | ASX200 (`AXJO`) | Nikkei 225 (`N225`) | 40,000,000 |

Los precios de cada índice se convierten a CHF con los tipos de cambio diarios `AUDCHF=X`, `CNYCHF=X`, `EURCHF=X`, `GBPCHF=X`, `HKDCHF=X`, `JPYCHF=X` y `USDCHF=X`.

## Datos

| Ventana | Periodo | Rendimientos | Uso |
|---|---|---|---|
| Reciente | 12/10/2023 – 03/03/2026 | 500 | VaR |
| Histórica | 29/12/2009 – 26/04/2019 | 3,405 | VaR Estresado |

Se trabaja con rendimientos logarítmicos diarios: `r_t = ln(P_t / P_{t-1})`.

## Metodología

Nivel de confianza **α = 97.5%** en todos los métodos.

1. **Simulación Histórica.** Se revalúa el portafolio con cada rendimiento observado y se toma el cuantil empírico de la distribución de pérdidas y ganancias.
2. **Monte Carlo.** Se simulan precios en t+1 a partir de la media (μ) y desviación estándar (σ) de cada índice, y se obtiene el cuantil de la distribución simulada de ΔP.
3. **Paramétrico (Varianza-Covarianza).** Se construyen la matriz de correlaciones y la matriz de varianza-covarianza; la volatilidad del portafolio es `σP = √(aᵀ Σ a)` y el VaR es `VaR = −Z(1−α) · σP`, con `Z(1−α) = −1.96`.

Para cada método se calcula:

- VaR a 1 día
- CVaR (Expected Shortfall) a 1 día
- VaR a 10 días, escalado con `VaR₁₀ = VaR₁ · √10`
- Capital de riesgo de mercado, `Capital = 3 · VaR₁₀`

## Resultados

### VaR (ventana reciente), al 3 de marzo de 2026

**Portafolio 1**

| Concepto | Sim. Histórica (CHF) | %P | Monte Carlo (CHF) | %P | Paramétrico (CHF) | %P |
|---|---:|---:|---:|---:|---:|---:|
| VaR 97.5%, 1 día | 2,257,216 | 2.26% | 1,548,226 | 1.55% | 2,423,826 | 2.42% |
| CVaR 97.5%, 1 día | 4,019,742 | 4.02% | 1,751,417 | 1.75% | 1,861,372 | 1.86% |
| VaR 97.5%, 10 días | 7,137,943 | 7.14% | 4,895,920 | 4.90% | 7,664,812 | 7.66% |
| Capital Riesgo de mercado | 21,413,829 | 21.41% | 14,687,760 | 14.69% | 22,994,437 | 22.99% |

**Portafolio 2**

| Concepto | Sim. Histórica (CHF) | %P | Monte Carlo (CHF) | %P | Paramétrico (CHF) | %P |
|---|---:|---:|---:|---:|---:|---:|
| VaR 97.5%, 1 día | 1,887,578 | 1.89% | 1,429,156 | 1.43% | 2,170,245 | 2.17% |
| CVaR 97.5%, 1 día | 3,895,118 | 3.90% | 556,095 | 0.56% | 1,666,634 | 1.67% |
| VaR 97.5%, 10 días | 5,969,046 | 5.97% | 4,519,388 | 4.52% | 6,862,916 | 6.86% |
| Capital Riesgo de mercado | 17,907,137 | 17.91% | 13,558,163 | 13.56% | 20,588,749 | 20.59% |

### VaR Estresado (ventana histórica 2009–2019)

**Portafolio 1**

| Concepto | Sim. Histórica (CHF) | %P | Monte Carlo (CHF) | %P | Paramétrico (CHF) | %P |
|---|---:|---:|---:|---:|---:|---:|
| VaR 97.5%, 1 día | 2,608,690 | 2.61% | 1,768,887 | 1.77% | 2,557,273 | 2.56% |
| CVaR 97.5%, 1 día | 4,011,777 | 4.01% | 2,102,645 | 2.10% | 1,963,852 | 1.96% |
| VaR 97.5%, 10 días | 8,249,401 | 8.25% | 5,593,713 | 5.59% | 8,086,808 | 8.09% |
| Capital Riesgo de mercado | 24,748,203 | 24.75% | 16,781,138 | 16.78% | 24,260,424 | 24.26% |

**Portafolio 2**

| Concepto | Sim. Histórica (CHF) | %P | Monte Carlo (CHF) | %P | Paramétrico (CHF) | %P |
|---|---:|---:|---:|---:|---:|---:|
| VaR 97.5%, 1 día | 2,337,332 | 2.34% | 1,715,986 | 1.72% | 2,404,014 | 2.40% |
| CVaR 97.5%, 1 día | 3,878,662 | 3.88% | 720,327 | 0.72% | 1,846,157 | 1.85% |
| VaR 97.5%, 10 días | 7,391,292 | 7.39% | 5,426,423 | 5.43% | 7,602,160 | 7.60% |
| Capital Riesgo de mercado | 22,173,877 | 22.17% | 16,279,268 | 16.28% | 22,806,479 | 22.81% |

## Hallazgos principales

- **El Portafolio 1 (Asia-Pacífico) es más riesgoso que el Portafolio 2 (EE.UU./Europa/Japón)** en los tres métodos y en ambas ventanas.
- **El VaR Estresado supera al VaR de la ventana reciente** en todos los casos, por lo que la ventana 2009–2019 exige más capital.
- **Los rendimientos no son normales.** Todos los índices muestran asimetría negativa y curtosis muy alta (por ejemplo, 30.9 en el ASX200 y 62.3 en el FTSE 100), lo que explica por qué el CVaR por Simulación Histórica es mucho mayor que el de los métodos que asumen normalidad.
- **Monte Carlo arroja el VaR más bajo**, ya que simula con una distribución normal y no captura las colas pesadas observadas.

## Estructura del archivo

| Hoja | Contenido |
|---|---|
| `Precios diarios` | Precios de los índices y tipos de cambio (ventana reciente) |
| `Precios diarios en CHF` | Precios convertidos a CHF |
| `Rendimientos log diarios` | Rendimientos logarítmicos diarios |
| `Estadísticas descriptivas` | Media, desviación, curtosis, asimetría e histogramas |
| `VaR Sim Hist` | VaR y CVaR por Simulación Histórica |
| `VaR Sim MC` | VaR y CVaR por Monte Carlo |
| `VaR Párametrico` | Correlaciones, varianza-covarianza, VaR y CVaR paramétrico |
| `Resumen VaR` | Tabla comparativa de los tres métodos |
| `Precios diarios historicos` | Precios y tipos de cambio (ventana 2009–2019) |
| `Precios hist en CHF` | Precios históricos en CHF |
| `Rendimientos log historicos` | Rendimientos logarítmicos históricos |
| `VaR Estresado Sim Hist` | VaR Estresado por Simulación Histórica |
| `VaR Estresado Sim MC` | VaR Estresado por Monte Carlo |
| `VaR Estresado Párametrico` | VaR Estresado paramétrico |
| `Resumen VaR Estresado` | Tabla comparativa del VaR Estresado |

## Cómo usarlo

1. Descarga `VaR-portafolios-internacionales-CHF.xlsx`.
2. Ábrelo en Excel 365 o 2021 (algunas fórmulas usan `XLOOKUP`).
3. Para cambiar la composición del portafolio, modifica los montos en `VaR Sim Hist` (Simulación Histórica y Monte Carlo los toman de ahí) y también los vectores `aT` y `a` en `VaR Párametrico`, que están capturados directamente.
4. Las simulaciones de Monte Carlo usan números aleatorios, así que sus resultados cambian ligeramente cada vez que Excel recalcula.


# ITAEE y Tipo de Cambio: Un Análisis VAR

## Descripción

Proyecto de investigación econométrica que analiza el efecto del tipo de cambio de 11 divisas sobre el **Indicador Trimestral de Actividad Económica Estatal (ITAEE)** para cinco estados de la región centro-norte de México, utilizando modelos de **Vectores Autorregresivos (VAR)**.

El análisis abarca 70 trimestres (T2 2007 – T4 2024) y emplea funciones de impulso-respuesta (IRF), descomposición de varianza del error de pronóstico (FEVD) y pruebas de causalidad de Granger para evaluar la transmisión de choques cambiarios a la actividad económica estatal.

## Principales resultados

- Los tipos de cambio **no Granger-causan de manera significativa** la actividad económica estatal en 54 de 55 combinaciones divisa-estado.
- El **ITAEE Nacional** es el principal determinante de la variación estatal (26%–52% de la varianza).
- La contribución conjunta de los 11 tipos de cambio a la varianza del ITAEE estatal oscila entre 33% y 47%, distribuida sin dominancia clara de una sola divisa.
- Los estados manufactureros (Aguascalientes, Querétaro, San Luis Potosí) están más sincronizados con el ciclo nacional; los estados con mayor diversificación productiva (Durango, Zacatecas) exhiben mayor autonomía cíclica.

## Estados analizados

- Aguascalientes
- Durango
- Querétaro
- San Luis Potosí
- Zacatecas

## Divisas (tipo de cambio vs MXN)

| Código | Moneda                    | Cotización       |
|--------|---------------------------|------------------|
| USD    | Dólar estadounidense      | Directa          |
| CAD    | Dólar canadiense          | Directa          |
| BRL    | Real brasileño            | Directa          |
| JPY    | Yen japonés               | Directa          |
| CNY    | Yuan chino                | Cruce vía USD    |
| COP    | Peso colombiano           | Cruce vía USD    |
| CLP    | Peso chileno              | Cruce vía USD    |
| RUB    | Rublo ruso                | Cruce vía USD    |
| ILS    | Shekel israelí            | Cruce vía USD    |
| EUR    | Euro                      | Cruce vía USD    |
| INR    | Rupia india               | Cruce vía USD    |

## Metodología

1. **Obtención de datos**: ITAEE vía INEGI; tipos de cambio diarios vía Yahoo Finance (`yfinance`), convertidos a promedios trimestrales.
2. **Pruebas de estacionariedad**: ADF y KPSS en niveles y log-diferencias. Series transformadas a log-diferencias (tasas de crecimiento trimestral).
3. **Modelo VAR**: 13 variables endógenas por estado (ITAEE Nacional + ITAEE estatal + 11 FX). Selección de rezagos óptimos por AIC (p=3 para los cinco estados). Diagnósticos de estabilidad, autocorrelación (Durbin-Watson) y normalidad (Jarque-Bera).
4. **Análisis**: Causalidad de Granger (FX → ITAEE estatal), funciones de impulso-respuesta ortogonalizadas (horizonte 20 trimestres, bandas de confianza al 95% vía Monte Carlo) y FEVD.

## Estructura del proyecto

```
ITAEE/
├── README.md
├── requirements.txt
├── reporte_capitulo.md          # Reporte académico (capítulo en español)
├── data/
│   ├── dataset.csv              # Dataset procesado (70 trimestres × 17 variables)
│   └── tabulados_ITAEE/         # Datos crudos ITAEE (INEGI, archivos Excel)
├── scripts/
│   └── create_dataset.py        # Pipeline de construcción del dataset
├── notebooks/
│   ├── exploration.ipynb        # Exploración inicial de datos
│   ├── itaee.ipynb              # Análisis descriptivo del ITAEE
│   └── var_model.ipynb          # Estimación VAR, IRF, FEVD, Granger
├── figures/                     # Visualizaciones generadas (20 figuras PNG)
├── results/
│   └── var_results_log.txt      # Log completo de resultados VAR
└── references/                  # Literatura académica de referencia
```

## Requisitos

```bash
pip install -r requirements.txt
```

Dependencias: `yfinance`, `pandas`, `numpy`, `matplotlib`, `seaborn`, `statsmodels`, `scipy`, `jupyter`.

## Fuentes de datos

- **ITAEE**: [INEGI - Indicador Trimestral de Actividad Económica Estatal](https://www.inegi.org.mx/temas/itaee/)
- **Tipos de cambio**: [Yahoo Finance](https://finance.yahoo.com/) vía librería `yfinance`

## Reproducibilidad

```bash
# 1. Instalar dependencias
pip install -r requirements.txt

# 2. Construir dataset (descarga datos de Yahoo Finance)
python scripts/create_dataset.py

# 3. Ejecutar análisis en Jupyter
jupyter notebook notebooks/var_model.ipynb
```

# ITAEE y Tipo de Cambio: Un Análisis VAR

## Descripción

Proyecto de econometría que analiza el efecto del tipo de cambio de distintas divisas sobre el **Indicador Trimestral de Actividad Económica Estatal (ITAEE)** para estados seleccionados de México, utilizando un modelo de **Vectores Autorregresivos (VAR)**.

## Estados analizados

- Aguascalientes
- Durango
- Querétaro
- San Luis Potosí
- Zacatecas

## Divisas (tipo de cambio vs MXN)

| Código | Moneda                    |
|--------|---------------------------|
| USD    | Dólar estadounidense      |
| CAD    | Dólar canadiense          |
| CNY    | Yuan chino                |
| COP    | Peso colombiano           |
| CLP    | Peso chileno              |
| RUB    | Rublo ruso                |
| BRL    | Real brasileño            |
| ILS    | Shekel israelí            |
| EUR    | Euro                      |
| INR    | Rupia india               |
| JPY    | Yen japonés               |

## Metodología

1. **Obtención de datos**: ITAEE vía INEGI; tipos de cambio vía Yahoo Finance (`yfinance`).
2. **Tratamiento de series**: Alineación temporal a frecuencia trimestral, pruebas de estacionariedad (ADF/KPSS), transformaciones si es necesario.
3. **Modelo VAR**: Selección de rezagos óptimos (AIC/BIC), estimación, diagnóstico de residuales.
4. **Análisis**: Funciones de impulso-respuesta (IRF), descomposición de varianza (FEVD), causalidad de Granger.

## Estructura del proyecto

```
ITAEE/
├── README.md
├── requirements.txt
├── data/               # Datos crudos y procesados
└── notebooks/          # Jupyter notebooks del análisis
```

## Requisitos

```bash
pip install -r requirements.txt
```

## Fuentes de datos

- **ITAEE**: [INEGI - Indicador Trimestral de Actividad Económica Estatal](https://www.inegi.org.mx/temas/itaee/)
- **Tipos de cambio**: [Yahoo Finance](https://finance.yahoo.com/) vía librería `yfinance`

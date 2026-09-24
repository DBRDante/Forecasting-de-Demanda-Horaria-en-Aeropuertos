<img width="921" height="269" alt="image" src="https://github.com/user-attachments/assets/38e789a9-e7b1-43f6-89c5-bf452d374b52" />

# Forecasting de Demanda Horaria en Aeropuertos para Servicios de Ridesharing: Modelado Predictivo y Optimización de Flota

## Problema
En la industria de movilidad y servicios de *ridesharing* en nodos de transporte masivo como los aeropuertos, la demanda de viajes presenta fluctuaciones severas a lo largo del día. Garantizar una cobertura adecuada de conductores es crucial para minimizar los tiempos de espera de los pasajeros y evitar la pérdida de viajes.  
El objetivo de este proyecto es construir un modelo predictivo capaz de anticipar el volumen de solicitudes de transporte (`num_orders`) para la siguiente hora, permitiendo al equipo operativo gestionar incentivos a conductores, ajustar tarifas dinámicas y optimizar la distribución de la flota en las terminales aéreas.

---

## Datos
El análisis utilizó el conjunto de datos histórico `taxi.csv` (año 2018), procesado mediante las siguientes etapas:
- **Granularidad original:** 26,496 registros recopilados en intervalos de 10 minutos.
- **Re-muestreo temporal:** Agregación de la serie a frecuencia horaria (`1H`), resultando en 4,416 registros consolidados y sin valores faltantes.

---

## Enfoque
El proyecto siguió una metodología estructurada de ciencia de datos para series temporales:
- Carga, indexación temporal y re-muestreo a nivel horario (`1H`).
- Análisis exploratorio de datos (EDA) y descomposición de la serie en tendencia, estacionalidad y residuos.
- Ingeniería de características: extracción de variables de calendario (`hour`, `dayofweek`, `month`), 24 valores rezagados (*lags*) y media móvil de 24 horas.
- Prevención de fuga de datos (*data leakage*) mediante la aplicación de `.shift(1)` en las estadísticas móviles.
- Partición cronológica estricta: 90% para entrenamiento y 10% para prueba sin mezcla (`shuffle=False`).
- Entrenamiento y evaluación de **Random Forest Regressor**.

---

## Resultados
El modelo **Random Forest Regressor** cumplió y superó satisfactoriamente los criterios de éxito establecidos:
- **RMSE (Test):** 43.06 (superando el umbral requerido de $\le 48$).

### Otros resultados clave:
- **Captura de estacionalidad:** Las variables de calendario y los rezagos permitieron modelar con precisión los ciclos diarios y semanales de alta demanda.
- **Generalización:** El rendimiento en la muestra de prueba independiente confirmó la solidez del pipeline predictivo ante datos no observados.

---

## Conclusión
El modelado predictivo demostró ser una herramienta altamente eficaz para anticipar la demanda de transporte en aeropuertos.  
Implementar este flujo proporciona a las plataformas de movilidad una base automatizada para optimizar la logística de flotas, reducir tiempos de espera y mejorar la eficiencia operativa en horas pico.

---

## Herramientas y Tecnologías
- Python  
- Pandas  
- NumPy  
- Scikit-Learn  
- Statsmodels  
- Matplotlib  
- Seaborn  

---

## Conclusión Clave
Este proyecto demuestra la aplicación práctica de ingeniería de características en series temporales y modelos de regresión avanzados para resolver un desafío operativo de alta relevancia en el sector de movilidad urbana.

---
---

# Airport Hourly Demand Forecasting for Ridesharing Services: Predictive Modeling and Fleet Optimization

## Problem
In the mobility and ridesharing industry within mass transit hubs such as airports, travel demand fluctuates severely throughout the day. Ensuring adequate driver coverage is crucial to minimize passenger wait times and avoid missed trips.  
The goal of this project is to build a predictive model capable of anticipating the volume of transport requests (`num_orders`) for the next hour, enabling the operations team to manage driver incentives, adjust dynamic pricing, and optimize fleet distribution across airport terminals.

---

## Data
The analysis used the historical dataset `taxi.csv` (year 2018), processed through the following stages:
- **Original granularity:** 26,496 records collected at 10-minute intervals.
- **Temporal resampling:** Aggregation of the series to an hourly frequency (`1H`), resulting in 4,416 consolidated records with no missing values.

---

## Approach
The project followed a structured data science methodology for time series:
- Loading, temporal indexing, and hourly resampling (`1H`).
- Exploratory Data Analysis (EDA) and time series decomposition into trend, seasonality, and residuals.
- Feature engineering: extraction of calendar variables (`hour`, `dayofweek`, `month`), 24 lagged values (*lags*), and a 24-hour rolling mean.
- Data leakage prevention by applying `.shift(1)` to rolling statistics.
- Strict chronological split: 90% for training and 10% for testing without shuffling (`shuffle=False`).
- Training and evaluation of **Random Forest Regressor**.

---

## Results
The **Random Forest Regressor** model successfully met and exceeded the established success criteria:
- **RMSE (Test):** 43.06 (surpassing the required threshold of $\le 48$).

### Other Key Results:
- **Seasonality Capture:** Calendar variables and lags allowed for precise modeling of daily and weekly high-demand cycles.
- **Generalization:** Performance on the independent test sample confirmed the robustness of the predictive pipeline on unseen data.

---

## Conclusion
Predictive modeling proved to be a highly effective tool for anticipating transport demand at airports.  
Implementing this workflow provides mobility platforms with an automated foundation to optimize fleet logistics, reduce wait times, and improve operational efficiency during peak hours.

---

## Tools and Technologies
- Python  
- Pandas  
- NumPy  
- Scikit-Learn  
- Statsmodels  
- Matplotlib  
- Seaborn  

---

## Key Takeaway
This project demonstrates the practical application of time series feature engineering and advanced regression models to solve a high-relevance operational challenge in the urban mobility sector.

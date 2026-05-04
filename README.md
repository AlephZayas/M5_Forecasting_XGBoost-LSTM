# M5 Forecasting: XGBoost vs LSTM  
### Predicción de ventas a 28 días (multi-output time series)

---

## Descripción del Proyecto

Este proyecto aborda el problema de **predicción de ventas diarias por SKU** utilizando el dataset de la competencia M5 de Kaggle.

Se implementaron y compararon dos enfoques:

- **XGBoost (modelo tabular)**
- **LSTM (modelo secuencial)**

El objetivo es predecir **los próximos 28 días de ventas**, formulando el problema como un **modelo multi-output**.

---

## Problema de Negocio

En retail, la correcta predicción de demanda permite:

- Optimizar inventarios  
- Reducir costos logísticos  
- Evitar quiebres de stock  
- Mejorar planeación operativa  

Este proyecto simula un entorno real de forecasting a gran escala (miles de SKUs).

---

## Enfoque Metodológico

### Naturaleza del Problema
- Serie de tiempo jerárquica (por producto y tienda)
- Predicción multi-step (horizonte de 28 días)
- Enfoque multi-output

---

## Pipeline del Proyecto

### 1. Procesamiento de Datos
- Uso de **DuckDB** para joins eficientes
- Integración de múltiples tablas:
  - ventas
  - precios
  - calendario
- Exportación a formato **Parquet** para eficiencia

---

### 2. Análisis Exploratorio (EDA)
- Identificación de patrones:
  - estacionalidad
  - tendencias
  - autocorrelación
- Análisis por:
  - producto
  - tienda
  - eventos

---

### 3. Feature Engineering

#### 🔹 Para XGBoost
- Lags (ventas históricas)
- Rolling statistics
- Variables de calendario:
  - día de la semana
  - mes
  - eventos
- Variables de precio:
  - cambios
  - rezagos
- Encoding dinámico (target encoding temporal)

---

#### 🔹 Para LSTM
- Transformación de datos tabulares → secuenciales
- Ventanas temporales (sliding windows)
- Normalización
- Estructuración 3D:  
  `(samples, timesteps, features)`

---

### 4. Modelado

#### XGBoost
- Uso de `MultiOutputRegressor`
- Predicción directa de los 28 días
- Manejo de datos tabulares

---

#### LSTM
- Red neuronal recurrente
- Captura de dependencias temporales
- Arquitectura secuencial

---

## Evaluación

Se utilizaron métricas de error:

- RMSE (Root Mean Squared Error)  
- MAE (Mean Absolute Error)  

Comparación entre:
- modelo tabular (XGBoost)
- modelo secuencial (LSTM)

---

## Estructura del Proyecto

- **DuckdbProcessing.ipynb**: procesamiento inicial, joins y exportación a Parquet  
- **EDA/**: análisis exploratorio de datos  
- **FeatureEngineering_XGBoost.ipynb**: construcción de variables para modelo XGBoost  
- **Modelado_XGBoost.ipynb**: entrenamiento y evaluación del modelo  
- **LSTM.ipynb**: feature engineering secuencial y entrenamiento de red LSTM  

---

## Dataset

El dataset no se incluye en el repositorio debido a su tamaño.

Puede descargarse desde Kaggle:
https://www.kaggle.com/competitions/m5-forecasting-accuracy/data

---

## Tecnologías Utilizadas

- Python  
- Pandas / NumPy  
- DuckDB  
- Scikit-learn  
- XGBoost  
- TensorFlow / Keras  
- Matplotlib / Seaborn  

---

## Documentación

El análisis completo, justificación metodológica y resultados detallados se encuentran en:

`Proyecto_Módulo_IV.pdf`

---
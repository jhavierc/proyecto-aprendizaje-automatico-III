# Proyecto de Análisis Predictivo de Ventas - Series de Tiempo

### Universidad ICESI

#### Mestría en Inteligecia Artificial Aplicada

#### **Presentado por:** Carlos Javier Cepeda

## 📋 Descripción del Proyecto

Este proyecto implementa un sistema completo de análisis predictivo para pronosticar las ventas mensuales de dos productos estrella de una compañía de comestibles. El objetivo principal es desarrollar modelos de series de tiempo que permitan predecir con precisión el comportamiento de las ventas del siguiente mes para cada producto, facilitando la planificación estratégica y la gestión de inventario.

## 🎯 Objetivo del Negocio

Una compañía de comestibles requiere predecir el comportamiento de las ventas (en unidades) de sus dos productos estrella para optimizar:
- **Planificación de inventario**: Evitar sobrestock y faltantes
- **Gestión de recursos**: Optimizar la cadena de suministro
- **Estrategia comercial**: Anticipar tendencias y ajustar estrategias de marketing
- **Presupuestación**: Proyecciones financieras más precisas

## 📊 Dataset

### Características del Dataset

- **Archivo**: `data-set.csv`
- **Período**: Junio 2014 - Diciembre 2024
- **Frecuencia**: Mensual
- **Observaciones**: 127 períodos
- **Variables**:
  - `producto1`: Ventas mensuales del primer producto estrella (unidades)
  - `producto2`: Ventas mensuales del segundo producto estrella (unidades)

### Estadísticas Descriptivas

**Producto 1:**
- Media: ~343.57 unidades
- Desviación estándar: ~100.23 unidades
- Rango: 137.05 - 500.00 unidades
- Tendencia: Decreciente a lo largo del período

**Producto 2:**
- Media: ~581.04 unidades
- Desviación estándar: ~167.50 unidades
- Rango: 200.00 - 806.44 unidades
- Tendencia: Creciente a lo largo del período

## 🏗️ Estructura del Proyecto

El proyecto está organizado en 12 notebooks secuenciales que cubren desde el análisis exploratorio hasta la comparación final de modelos:

### 1. Análisis Exploratorio de Datos (`1. Analisis-exploratorio-datos.ipynb`)
- Carga y exploración inicial de datos
- Preparación y limpieza de datos
- Manejo de valores faltantes y nulos
- Análisis exploratorio de datos (EDA)
- Análisis de estacionariedad
- Identificación de patrones temporales
- Descomposición de series de tiempo
- Análisis de autocorrelación (ACF/PACF)

### 2-6. Modelos de Suavización Exponencial

#### 2. Promedio Móvil Simple - SMA (`2. Modelo-SE-Promedio-movil-SMA.ipynb`)
- Implementación de promedio móvil simple
- Validación temporal con múltiples estrategias

#### 3. Promedio Móvil Ponderado - WMA (`3. Modelo-SE-Promedio-movil-WMA.ipynb`)
- Implementación de promedio móvil ponderado
- Asignación de pesos a observaciones recientes

#### 4. Suavización Exponencial Simple - SES (`4. Modelo-SE-simple-SES.ipynb`)
- Modelo de suavización exponencial simple
- Optimización del parámetro de suavización

#### 5. Holt - Doble Suavización Exponencial - DES (`5. Modelo-SE-Holt-DES.ipynb`)
- Modelo de Holt para capturar tendencia
- Componentes de nivel y tendencia

#### 6. Holt-Winters - Triple Suavización Exponencial - TES (`6. Modelo-SE-Holt-Winters-TES.ipynb`)
- Modelo de Holt-Winters para capturar estacionalidad
- Componentes de nivel, tendencia y estacionalidad

### 7. Modelo ETS (`7. Modelo-ETS.ipynb`)
- Error, Trend, Seasonality (ETS)
- Selección automática de componentes
- Optimización bayesiana de hiperparámetros

### 8. Modelo ARIMA (`8. Modelo-ARIMA.ipynb`)
- AutoRegressive Integrated Moving Average
- Identificación de órdenes (p, d, q)
- Optimización bayesiana de parámetros
- Diagnósticos de residuos

### 9. Modelo Auto-ARIMA (`9. Modelo-AutoARIMA.ipynb`)
- Selección automática de parámetros ARIMA
- Búsqueda exhaustiva de mejores órdenes
- Validación cruzada temporal

### 10. Modelo Prophet (`10. Modelo-Prophet.ipynb`)
- Framework de pronóstico desarrollado por Facebook
- Manejo automático de estacionalidad
- Componentes aditivos y multiplicativos
- Detección de puntos de cambio

### 11. Modelo VAR (`11. Modelo-VAR-extra.ipynb`)
- Vector Autoregression (VAR)
- Modelo multivariado que captura relaciones entre productos
- Análisis de interdependencias entre series

### 12. Comparación de Modelos (`12. Comparación-Modelos.ipynb`)
- Compilación de resultados de todos los modelos
- Análisis comparativo de métricas
- Visualizaciones comparativas
- Identificación del mejor modelo
- Rankings y recomendaciones finales

## 🔬 Metodología

### Validación Temporal

Todos los modelos fueron evaluados utilizando tres estrategias de validación temporal para garantizar robustez:

1. **Walk-Forward Validation**
   - Entrenamiento incremental con validación en cada paso
   - Simula el proceso de pronóstico en producción

2. **Rolling Window**
   - Ventana deslizante de tamaño fijo
   - Mantiene un tamaño constante de datos de entrenamiento

3. **Expanding Window**
   - Ventana expandible que incluye todo el historial
   - Aprovecha toda la información disponible

### Métricas de Evaluación

Para cada modelo se calcularon las siguientes métricas:

- **RMSE (Root Mean Squared Error)**: Raíz del error cuadrático medio
  - Penaliza más los errores grandes
  - Unidades en la escala original de los datos

- **MAE (Mean Absolute Error)**: Error absoluto medio
  - Interpretación directa del error promedio
  - Menos sensible a valores atípicos

- **MAPE (Mean Absolute Percentage Error)**: Error porcentual absoluto medio
  - Error relativo expresado en porcentaje
  - Permite comparación entre productos con escalas diferentes

## 🤖 Modelos Implementados

### Modelos de Suavización Exponencial

1. **SMA (Simple Moving Average)**
   - Promedio aritmético de los últimos N períodos
   - Simple pero efectivo para series estables

2. **WMA (Weighted Moving Average)**
   - Promedio ponderado con mayor peso a observaciones recientes
   - Captura mejor las tendencias recientes

3. **SES (Simple Exponential Smoothing)**
   - Suavización exponencial simple
   - Ideal para series sin tendencia ni estacionalidad

4. **Holt-DES (Double Exponential Smoothing)**
   - Extiende SES para capturar tendencia
   - Componentes: nivel y tendencia

5. **Holt-Winters-TES (Triple Exponential Smoothing)**
   - Extiende Holt para capturar estacionalidad
   - Componentes: nivel, tendencia y estacionalidad

### Modelos Estadísticos Avanzados

6. **ETS (Error, Trend, Seasonality)**
   - Modelo de estado espacial
   - Selección automática de componentes
   - Optimización bayesiana

7. **ARIMA (AutoRegressive Integrated Moving Average)**
   - Modelo autorregresivo integrado de medias móviles
   - Captura dependencias temporales complejas
   - Optimización bayesiana de hiperparámetros

8. **Auto-ARIMA**
   - Selección automática de parámetros ARIMA
   - Búsqueda exhaustiva de mejores órdenes

### Modelos de Machine Learning

9. **Prophet**
   - Framework desarrollado por Facebook
   - Manejo automático de estacionalidad y tendencias
   - Robusto ante valores faltantes y outliers

### Modelos Multivariados

10. **VAR (Vector Autoregression)**
    - Modelo multivariado que captura relaciones entre productos
    - Considera interdependencias entre series temporales
    - Útil cuando las series están correlacionadas

## 📈 Resultados Principales

### Resumen de Rendimiento

Los modelos fueron evaluados en ambos productos y se obtuvieron los siguientes resultados destacados:

**Mejores Modelos por Producto:**

- **Producto 1**: Modelos con menor RMSE incluyen ARIMA, Holt-DES, y ETS
- **Producto 2**: Modelos con menor RMSE incluyen ARIMA, Holt-DES, y ETS

**Modelos Excluidos:**
- Auto-ARIMA mostró valores de RMSE anómalamente altos (>1000), sugiriendo problemas en la configuración o implementación

### Predicciones Finales

Las predicciones del próximo período (enero 2025) para cada producto fueron generadas utilizando el mejor modelo identificado en el análisis comparativo.

## 📁 Estructura de Archivos

```
Proyecto/
│
├── 0. README.md     # Este archivo
├── data-set.csv     # Dataset principal
├── 1. Analisis-exploratorio-datos.ipynb
├── 2. Modelo-SE-Promedio-movil-SMA.ipynb
├── 3. Modelo-SE-Promedio-movil-WMA.ipynb
├── 4. Modelo-SE-simple-SES.ipynb
├── 5. Modelo-SE-Holt-DES.ipynb
├── 6. Modelo-SE-Holt-Winters-TES.ipynb
├── 7. Modelo-ETS.ipynb
├── 8. Modelo-ARIMA.ipynb
├── 9. Modelo-AutoARIMA.ipynb
├── 10. Modelo-Prophet.ipynb
├── 11. Modelo-VAR-extra.ipynb
├── 12. Comparación-Modelos.ipynb

```

## 🛠️ Dependencias y Requisitos

### Librerías Principales

```python
# Análisis de datos
pandas >= 1.5.0
numpy >= 1.23.0

# Visualización
matplotlib >= 3.6.0
seaborn >= 0.12.0

# Series de tiempo
statsmodels >= 0.14.0

# Machine Learning
scikit-learn >= 1.2.0
prophet >= 1.1.0

# Optimización
optuna >= 3.0.0

# Utilidades
scipy >= 1.10.0
warnings
```

### Instalación

```bash
# Instalar dependencias básicas
pip install pandas numpy matplotlib seaborn

# Instalar librerías de series de tiempo
pip install statsmodels

# Instalar Prophet (requiere compilador C++)
pip install prophet

# Instalar optimización
pip install optuna

# Instalar scikit-learn
pip install scikit-learn
```

## 🚀 Uso del Proyecto

### Ejecución Secuencial

Los notebooks están diseñados para ejecutarse en orden:

1. **Iniciar con el análisis exploratorio** (`1. Analisis-exploratorio-datos.ipynb`)
   - Comprender los datos y sus características

2. **Ejecutar modelos individuales** (Notebooks 2-11)
   - Cada notebook es independiente y puede ejecutarse por separado
   - Genera métricas y predicciones para cada modelo

3. **Comparar resultados** (`12. Comparación-Modelos.ipynb`)
   - Compila todos los resultados
   - Identifica el mejor modelo
   - Genera visualizaciones comparativas

### Generación de Predicciones

Para generar predicciones del próximo período:

1. Ejecutar el notebook del modelo seleccionado
2. Utilizar la función de pronóstico con los datos completos
3. El modelo generará la predicción para el siguiente período

## 📊 Visualizaciones

El proyecto incluye visualizaciones comprehensivas:

- **Series de tiempo históricas**: Evolución de las ventas a lo largo del tiempo
- **Descomposición temporal**: Separación de tendencia, estacionalidad y residuos
- **Autocorrelaciones**: ACF y PACF para identificación de modelos
- **Comparación de modelos**: Gráficos comparativos de rendimiento
- **Predicciones**: Visualización de predicciones vs valores reales
- **Heatmaps de métricas**: Comparación visual de RMSE entre modelos

## 🔍 Análisis y Hallazgos

### Características de las Series

**Producto 1:**
- Muestra una tendencia decreciente a lo largo del período
- Variabilidad moderada
- Posible presencia de estacionalidad

**Producto 2:**
- Muestra una tendencia creciente pronunciada
- Mayor variabilidad que el Producto 1
- Patrones estacionales más evidentes

### Selección del Mejor Modelo

El modelo óptimo fue seleccionado considerando:
- **RMSE promedio** entre ambos productos
- **Consistencia** en el rendimiento
- **Balance** entre precisión y estabilidad
- **Score combinado** de rankings múltiples

## 📝 Notas Técnicas

### Consideraciones Importantes

1. **Validación Temporal**: Todos los modelos utilizan validación temporal para evitar data leakage
2. **Optimización**: Los modelos avanzados utilizan optimización bayesiana para hiperparámetros
3. **Diagnósticos**: Se realizan pruebas de residuos para validar supuestos de los modelos
4. **Estacionariedad**: Se aplican transformaciones cuando es necesario

### Limitaciones

- El dataset tiene 127 observaciones, lo cual puede limitar modelos complejos
- Algunos modelos requieren más datos para capturar patrones estacionales completos
- Auto-ARIMA mostró problemas de convergencia en algunos casos

## 🎓 Aplicación del Checklist

El proyecto sigue un checklist estructurado:

- ✅ **Punto 1-6**: Análisis de datos (EDA, limpieza, estacionariedad)
- ✅ **Punto 7**: División de datos (validación temporal)
- ✅ **Punto 8**: Selección de métricas (RMSE, MAE, MAPE)
- ✅ **Punto 9**: Validación temporal (Walk-Forward, Rolling, Expanding)

## 📚 Referencias

- Hyndman, R.J., & Athanasopoulos, G. (2021). *Forecasting: principles and practice*
- Box, G. E. P., Jenkins, G. M., & Reinsel, G. C. (2015). *Time Series Analysis: Forecasting and Control*
- Prophet Documentation: https://facebook.github.io/prophet/
- Statsmodels Documentation: https://www.statsmodels.org/

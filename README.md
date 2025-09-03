# Google Ads Data Cleaning & Visualization  

📊 **Proyecto académico – CoderHouse Data Science I**  
Este proyecto consiste en la **limpieza, exploración y visualización** de un dataset de **Google Ads**, aplicando técnicas de **data cleaning y análisis exploratorio (EDA)** con Python.  

---

# Google Ads Data Cleaning & Visualization  

📌 Este repositorio contiene un proyecto de **Data Cleaning y Exploración de Datos (EDA)** aplicado a un dataset de **Google Ads**, realizado como parte de la carrera de Data Science en CoderHouse.  

---

## ▶️ Cómo abrir el notebook  

Puedes revisar el proyecto de dos maneras:  

1. **Ver en GitHub**:  
   🔗 [Notebook en GitHub](https://github.com/meliluc/google-ads-data-cleaning-visualization/blob/main/ProyectoDSParteI_Lucero_Antonietti.ipynb)  

2. **Abrir y ejecutar en Google Colab** (recomendado):    
   [![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/meliluc/google-ads-data-cleaning-visualization/blob/main/ProyectoDSParteI_Lucero_Antonietti.ipynb)  

---

## 🛠️ Herramientas Utilizadas
- Python  
- Pandas  
- NumPy  
- Seaborn  
- Matplotlib  
- Jupyter / Google Colab

---

## 🎯 Objetivos
- Realizar **data cleaning** y detección de valores perdidos.  
- Definir **preguntas de investigación** e hipótesis iniciales.  
- Generar **visualizaciones univariadas, bivariadas y multivariadas**.  
- Interpretar los resultados vinculándolos con el negocio.  

---

## 🔎 1. Exploración inicial
- Cargamos el dataset en un **DataFrame de Pandas**.  
- Revisamos dimensiones, tipos de datos y valores nulos (`.info()`, `.isnull().sum()`).  
- Identificamos problemas típicos de datos crudos:  
  - Fechas con formatos mezclados.  
  - Variables monetarias con símbolos (`$`, `,`).  
  - Valores faltantes (`NaN`).  
  - Categorías duplicadas por mayúsculas/minúsculas (ej: *Mobile, mobile, MOBILE*).  

---

## 🧹 2. Limpieza de datos

**a) Fechas**  
- Creamos una función para parsear múltiples formatos (`2024/11/16`, `16-11-2024`, `2024-11-04`).  
- Convertimos `Ad_Date` a tipo `datetime64[ns]`.  

**b) Variables monetarias**  
- Quitamos símbolos y separadores en `Cost` y `Sale_Amount`.  
- Convertimos esas columnas a `float`.  

**c) Tipos de datos**  
- Columnas categóricas (`Campaign_Name`, `Location`, `Device`, `Keyword`) → `string`.  
- Variables numéricas (`Clicks`, `Impressions`, `Conversions`, `Leads`) → `float`.  

**d) Valores faltantes**  
- Detectamos nulos en columnas clave.  
- Los rellenamos con la **mediana** de cada columna numérica (más robusta que la media).  

**e) Normalización de categorías**  
- Unificamos categorías de `Device` en minúsculas (`desktop`, `mobile`, `tablet`).  

---

## 📊 3. Control de calidad
- Verificamos nulos tras la limpieza (`.isnull().sum()`).  
- Revisamos valores atípicos (ej: ceros en columnas monetarias).  
- Confirmamos consistencia de tipos de datos finales.  

---

## 📈 4. Análisis y visualizaciones
- Creamos gráficos multivariados para explorar relaciones:  
  - **Ejemplo 1**: `Cost vs Sale_Amount`, tamaño proporcional a `Clicks`, color por `Device`.  
  - **Ejemplo 2**: Figura **FacetGrid** separando métricas por dispositivo.  
- Acompañamos cada visualización con análisis descriptivo de patrones.  

---

## 📊 5. Estadísticos descriptivos
- Calculamos resúmenes numéricos (`mean`, `median`, `std`) para variables clave (`Cost`, `Clicks`, `Sale_Amount`).  
- Estos respaldaron lo observado en los gráficos.  

---

## 📝 6. Conclusiones preliminares
- Los datos sin limpiar generaban **patrones artificiales** (ej: forma de cruz en scatterplots).  
- Tras la limpieza, las relaciones **Cost → Sale_Amount** fueron más consistentes.  
- El dataset quedó preparado para futuros **modelos predictivos** (ej: predecir ventas a partir de inversión, clics, dispositivo, etc.).  

---

## 📂 Estructura del Repositorio

├── ProyectoDS_ParteI_LuceroAntonietti.ipynb   # Notebook principal ├── dataset_google_ads.csv                     # Dataset utilizado └── README.md                                  # Descripción del proyecto


---

## 🚀 Próximos pasos: Predicción en el Proyecto  

Tras la limpieza y el análisis exploratorio, el siguiente objetivo es avanzar hacia la **modelización predictiva** para estimar el monto de ventas (`Sale_Amount`) en función de otras variables.  

### 🎯 1. Definir el objetivo de predicción  
👉 **Predecir `Sale_Amount` (variable continua)** a partir de variables como `Cost`, `Clicks`, `Impressions`, `Device`, `Location`, etc.  
➡️ Se trata de un **problema de regresión**.  

---

### 🛠️ 2. Preparación de los datos para Machine Learning  
- **Features (X)**: `Cost`, `Clicks`, `Impressions`, `Leads`, `Device`, `Location`.  
- **Target (y)**: `Sale_Amount`.  
- **Codificación de variables categóricas** (`Device`, `Location`, etc.) con *OneHotEncoding*.  
- **Escalado de datos** para algoritmos sensibles a la escala (ej. Regresión lineal, SVM).  
- **División Train/Test** con `train_test_split` (ej: 80/20).  

---

### 🤖 3. Entrenamiento de modelos de regresión  
Se evaluarán diferentes algoritmos:  
- **Regresión Lineal** (baseline, interpretable).  
- **Árboles de Decisión / Random Forest** (captura de relaciones no lineales).  
- **Gradient Boosting / XGBoost** (modelos más potentes y precisos).  

---

### 📊 4. Evaluación de modelos  
Se utilizarán métricas clave:  

- **R² (Coeficiente de determinación)** → mide qué tan bien el modelo explica la variabilidad de las ventas (`Sale_Amount`).  
- **RMSE (Error cuadrático medio)** → indica cuánto se equivoca en promedio el modelo en sus predicciones.  

Estas métricas permitirán comparar la performance de los distintos algoritmos (Regresión Lineal, Random Forest, Gradient Boosting).  

---

### 🔮 5. Interpretación y conclusiones  
- Identificar las **variables con mayor influencia** en las ventas (`feature importance`).  
- Responder preguntas de negocio:  
  - ¿El **costo** es el factor más determinante?  
  - ¿El número de **clicks** predice mejor las ventas que las impresiones?  
  - ¿El **dispositivo o la ubicación** generan diferencias significativas?  
- Determinar si el modelo tiene **precisión suficiente** para ser utilizado en un entorno real de toma de decisiones.  

---

## 👩‍💻 Autora  

**Melina Lucero Antonietti**  

🔗 [LinkedIn](https://www.linkedin.com/in/melina-lucero/) 
💻 [GitHub](https://github.com/meliluc)  

---

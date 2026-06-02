
# Del clic a la fidelización: Modelado predictivo del CLV en e-commerce

  

[![Python 3.9+](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)


[![Code style](https://img.shields.io/badge/code%20style-black-black)](https://github.com/psf/black)

  
**Autor:** Pau Bestard Satorra
## Descripción del Proyecto

  

Este repositorio contiene el código fuente completo del Trabajo Final de Máster (TFM) titulado *"Del clic a la fidelización: modelado predictivo del comportamiento y valor del cliente en plataformas de e-commerce"*.

  

El proyecto aborda la transformación de datos brutos de navegación (vistas, carritos, compras) en conocimiento predictivo para estimar el **Customer Lifetime Value (CLV)** y comprender el comportamiento de los clientes en entornos de comercio electrónico.

  

### Principales contribuciones

  

-  **Pipeline de preprocesamiento en dos pasadas** para enriquecer eventos de compra con contexto de navegación (vistas y carritos previos).

-  **Modelos de regresión** (Random Forest y XGBoost) para estimación numérica del CLV.

-  **Modelos probabilísticos** (BG/NBD + Gamma-Gamma) para modelar abandono y recurrencia.

-  **Segmentación de clientes** mediante K-Means.

-  **Análisis de interpretabilidad** con importancia de variables y SHAP.

-  **Visualizaciones** para la toma de decisiones de negocio.

  
  

### Requisitos previos

  

-  **Python 3.9 o superior**

-  **8GB de RAM mínimo** (recomendado: 16GB)

-  **20GB de espacio en disco** (para datos procesados)

  

### Clonar el repositorio

  

```bash

git  clone  https://github.com/wertons/clic_a_fidelizacion.git

cd  clic_a_fidelizacion
```
  

## Descarga de Datasets

  

Este  proyecto  utiliza  dos  datasets  públicos.  Debes  descargarlos  manualmente  y  ubicarlos  en  la  estructura  correcta:

  

### Dataset 1: Comportamiento E-commerce (Kaggle)

  

-  **Fuente:** [eCommerce Behavior  Data  from  Multi-category  Store](https://www.kaggle.com/datasets/mkechinov/ecommerce-behavior-data-from-multi-category-store/data)

-  **Archivos  necesarios:**  `2019-Oct.csv`,  `2019-Nov.csv`

-  **Ubicación:**  `data/online+retail/`

  

### Dataset 2: Online Retail (UCI)

  

-  **Fuente:** [Online Retail  Data  Set](https://archive.ics.uci.edu/dataset/352/online+retail)

-  **Archivo:**  `Online Retail.xlsx`

-  **Ubicación:**  `data/online+retail/`

  

### Estructura final esperada
```text
data/

└──  online+retail/

├──  2019-Oct.csv

├──  2019-Nov.csv

├──  Online  Retail.xlsx

└──  split/ (se crea  automáticamente)
```
  
  ### Fase 1: Preprocesamiento de datos
```
# Convertir Excel a CSV y dividir archivos grandes


python  notebooks/1_split_csv.py

# Ejecutar el procesamiento en dos pasadas (Jupyter)

jupyter  notebook  notebooks/2_preprocess_csv.ipynb
```
  

### Fase 2: Análisis Exploratorio (EDA)

  

```bash
jupyter  notebook  notebooks/3_EDA_online_retail.ipynb

jupyter  notebook  notebooks/4_EDA_ecommerce_1.ipynb

jupyter  notebook  notebooks/4_EDA_ecommerce_2.ipynb

jupyter  notebook  notebooks/4_EDA_ecommerce_3.ipynb

jupyter  notebook  notebooks/5_EDA_purchases_enrich.ipynb
```
  

### Fase 3: Modelado predictivo

  

```bash

# Modelos de regresión (Random Forest, XGBoost)

jupyter  notebook  notebooks/7_CLV_modeling_RandomForest_clean.ipynb

# Modelos probabilísticos (BG/NBD + Gamma-Gamma)

jupyter  notebook  notebooks/9_CLV_modeling_bg_nbd.ipynb
```
  

### Fase 4: Visualización y segmentación

  

Los  notebooks  de  modelado  ya  incluyen  visualizaciones  y  segmentación  K-Means.

  

----------

  

## Principales Resultados

  
| Modelo | MAE | RMSE | R² | Tiempo entrenamiento |
|--|--| --| --| --|
| Random Forest (sin limpieza) | 504.14 | 1462.34 | - | - |
| Random Forest (con limpieza) | 300.86 | 429.59 | 0.199 | 45.73 seg |
| **XGBoost (con limpieza)** | **285.76**| **404.31** | **0.291** | **5.65 seg** |
  

### Hallazgos clave

  

-  **La  recurrencia  predice  mejor  el  CLV  que  el  ticket  medio** (correlación 0.64  vs  0.52)

-  **XGBoost  es  8  veces  más  rápido**  que  Random  Forest  con  mejor  precisión

-  **La  limpieza  de  outliers** (percentiles 5-95) reduce el RMSE en un **70.6%**

-  **Solo  el  28.6%  de  los  clientes**  tienen  probabilidad >0.5  de  seguir  activos

  

----------

  

## Tecnologías Utilizadas

  
| Categoría | Librerías |
|--|--|
| **Procesamiento de datos** | Pandas, NumPy, CSV |
| **Modelado** | Scikit-learn, XGBoost, Lifetimes |
| **Visualización** | Matplotlib, SHAP |
| **Entorno** | Jupyter Notebook, Python 3.9+ |


  

----------

  

## Visualizaciones Generadas

  

El  código  genera  automáticamente  las  siguientes  visualizaciones:

  

-  Distribución  de  tipos  de  evento (views/carts/purchases)

-  Tiempos  de  conversión (vista →  compra,  carro  →  compra)

-  Importancia  de  variables (Random Forest  vs  XGBoost)

-  Predicciones  vs  valores  reales (scatter plots)

-  Heatmaps  de  correlación

-  Evolución  del  gasto  acumulado  por  cliente

-  Segmentación  de  clusters (K-Means)

-  Forecast  de  CLV  semanal (4 semanas)

  


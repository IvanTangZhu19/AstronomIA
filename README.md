# AstronomIA

Este proyecto utiliza **modelos de aprendizaje automático** para clasificar objetos astronómicos (estrellas, galaxias y cuásares) a partir de datos del **Sloan Digital Sky Survey (SDSS)**.  
Los datos provienen del conjunto disponible en [Kaggle - Stellar Classification Dataset - SDSS17](https://www.kaggle.com/datasets/fedesoriano/stellar-classification-dataset-sdss17).

---

## 🧠 Objetivo  

Desarrollar, entrenar y desplegar un modelo de **inteligencia artificial** capaz de predecir el tipo de objeto celeste (Star, Galaxy o QSO) a partir de mediciones fotométricas y espectroscópicas.  

---

## 📊 Descripción del Dataset  

El conjunto de datos contiene observaciones astronómicas con las siguientes variables principales:

| Variable | Descripción |
|-----------|--------------|
| **obj_ID** | Identificador único del objeto. |
| **alpha** | Ascensión recta (Right Ascension) — posición en el cielo. |
| **delta** | Declinación — posición en el cielo. |
| **u, g, r, i, z** | Magnitudes en diferentes filtros del espectro electromagnético (ultravioleta a infrarrojo cercano). |
| **run_ID, rerun_ID, cam_col, field_ID** | Identificadores de la corrida, versión, columna de cámara y campo de observación. |
| **spec_obj_ID** | Identificador del objeto en el catálogo espectroscópico. |
| **class** | Tipo de objeto celeste: `GALAXY`, `STAR`, o `QSO` (Quasar). |
| **redshift** | Desplazamiento al rojo — indica la distancia y velocidad de alejamiento del objeto. |
| **plate, mjd, fiber_ID** | Parámetros técnicos relacionados con la observación espectral. |

📦 **Fuente:** [https://www.kaggle.com/datasets/fedesoriano/stellar-classification-dataset-sdss17](https://www.kaggle.com/datasets/fedesoriano/stellar-classification-dataset-sdss17)

---

## ⚙️ Metodología  

1. **División de los datos:**  
   - 70% de los datos se utilizan para **entrenamiento y validación cruzada**.  
   - 30% restante para **evaluación final**.  

2. **Validación cruzada:**  
   - Se aplica una **validación cruzada k-fold** para asegurar la robustez del modelo y evitar sobreajuste.  

3. **Preprocesamiento con Pipelines:**  
   - Estandarización de variables numéricas.  
   - Codificación de variables categóricas (si aplica).  
   - Integración del modelo en un **pipeline de scikit-learn** para automatizar el flujo de entrenamiento y predicción.  

---

## 🤖 Modelos Utilizados  

Se implementaron y compararon los siguientes algoritmos de clasificación:

| Tipo de modelo | Descripción |
|----------------|--------------|
| 🌳 **Árbol de Decisión** | Modelo interpretable basado en reglas jerárquicas. |
| 📍 **K-Nearest Neighbors (KNN)** | Clasifica según la cercanía a los ejemplos más similares. |
| 🧩 **Red Neuronal Artificial (MLPClassifier)** | Modelo de capas densas para capturar relaciones no lineales. |
| 🧱 **Métodos de Ensamble** | Combina varios clasificadores (Random Forest, Gradient Boosting) para mejorar la precisión. |

Se comparan métricas como **accuracy**, **precision**, **recall** y **F1-score** para determinar el mejor desempeño.

---

## 🚀 Despliegue  

El modelo final se integró y desplegó en una aplicación interactiva con **Streamlit**, permitiendo al usuario ingresar valores de las variables fotométricas y obtener la predicción del tipo de objeto.  

El flujo de despliegue incluye:  

- Pipeline de preprocesamiento + modelo entrenado.  
- Interfaz visual con campos de entrada para las magnitudes.  
- Visualización de resultados de predicción y métricas.  

# Proyecto: Análisis y Clasificación de Cáncer de Mama (Wisconsin)

Este repositorio contiene un análisis exploratorio de datos (EDA) completo y la implementación de múltiples modelos de machine learning para clasificar el dataset "Breast Cancer Wisconsin (Diagnostic)". El objetivo es comparar el rendimiento de 8 algoritmos de clasificación diferentes, cada uno evaluado con 5 configuraciones de hiperparámetros mediante validación cruzada.

---

## 📊 Dataset

El análisis se realiza sobre el archivo `data.csv`, que contiene las características numéricas de los núcleos celulares de tumores mamarios.

-   **Variable Objetivo:** `diagnosis` (Maligno 'M' o Benigno 'B').

---

## 📚 Librerías Principales

-   `pandas`
-   `numpy`
-   `matplotlib`
-   `seaborn`
-   `scikit-learn` (para preprocesamiento, métricas y modelos)
-   `PaqEda` (Un paquete personalizado para el Análisis Exploratorio de Datos, importado en el notebook)

---

## ⚙️ Flujo del Proyecto

El notebook `EDA_JUNIOR.ipynb` está estructurado en las siguientes partes:

### 1. Importación y Carga
-   Importación de todas las librerías necesarias para el análisis, visualización y modelado.
-   Carga del dataset (`data.csv`).

### 2. Análisis Exploratorio de Datos (EDA)
-   Se utiliza el paquete `analisisEDA` para un análisis inicial.
-   **Limpieza de Datos:**
    -   Eliminación de columnas irrelevantes (ej. `Unnamed: 32`).
    -   Búsqueda y eliminación de filas duplicadas.
    -   Búsqueda y eliminación de valores nulos.
-   **Análisis de la Variable Objetivo:**
    -   Distribución de las clases (`diagnosis`) para identificar el balance.
-   **Visualizaciones (realizadas en celdas posteriores):**
    -   Boxplots para detectar outliers.
    -   Histogramas para entender la distribución de cada característica.
    -   Matriz de correlación (heatmap) para identificar multicolinealidad.
    -   Pairplots para visualizar relaciones entre las características más relevantes.

### 3. Preprocesamiento de Datos
-   **Codificación:** La variable objetivo `diagnosis` se transforma de categórica ('M'/'B') a numérica (1/0).
-   **División de Datos:** El dataset se divide en conjuntos de entrenamiento y prueba (`train_test_split`).
-   **Escalado:** Las características se estandarizan usando `StandardScaler` para asegurar que todos los modelos funcionen correctamente.

### 4. Evaluación Comparativa de Modelos
Se definen, entrenan y evalúan 8 algoritmos de clasificación distintos:

1.  Regresión Logística (`LogisticRegression`)
2.  K-Vecinos más Cercanos (`KNeighborsClassifier`)
3.  Máquinas de Vectores de Soporte (`SVC`)
4.  Árbol de Decisión (`DecisionTreeClassifier`)
5.  Random Forest (`RandomForestClassifier`)
6.  Gradient Boosting (`GradientBoostingClassifier`)
7.  Gaussian Naive Bayes (`GaussianNB`)
8.  Perceptrón Multicapa (`MLPClassifier`)

Para cada algoritmo, se realiza lo siguiente:
-   Se definen 5 configuraciones de hiperparámetros para ser probadas.
-   Se utiliza `GridSearchCV` para encontrar la mejor configuración mediante validación cruzada.
-   Se calculan las métricas clave en el conjunto de prueba: **Accuracy, Precision, Recall, F1-Score** y **ROC-AUC**.
-   Se generan y visualizan la **Matriz de Confusión** y la **Curva ROC**.

### 5. Análisis de Resultados
-   Todos los resultados de las 40 ejecuciones (8 modelos * 5 configuraciones) se consolidan en un `DataFrame` de `pandas`.
-   Se analiza este dataframe para identificar:
    -   El mejor modelo basado en el Accuracy promedio.
    -   El algoritmo más consistente (menor desviación estándar en Accuracy).
    -   El rango general de Accuracy (mínimo y máximo) obtenido.
-   Finalmente, los resultados detallados se exportan a `resultados_modelos.csv`.

---

## 🚀 Cómo Usar

1.  Clona este repositorio.
2.  Asegúrate de tener el paquete `PaqEda.py` (referenciado en el notebook) en el mismo directorio si deseas ejecutar el EDA desde cero.
3.  Coloca el dataset `data.csv` en la carpeta raíz.
4.  Instala las dependencias listadas abajo.
5.  Ejecuta el notebook `EDA_JUNIOR.ipynb`.

**Dependencias (ejemplo):**
```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter

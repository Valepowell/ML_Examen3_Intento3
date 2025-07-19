# ML_Examen3_Intento3
# Análisis y Modelado de Predicción de Diabetes

## Descripción del Proyecto
Este proyecto tiene como objetivo analizar un conjunto de datos sobre diabetes y desarrollar modelos de clasificación para predecir la probabilidad de que un paciente tenga diabetes basándose en diversas métricas de salud. El análisis incluye la limpieza y exploración de los datos, la implementación y evaluación de modelos de Machine Learning (Random Forest y XGBoost), y la optimización de hiperparámetros para mejorar el rendimiento del modelo.

## Fuente de Datos
El conjunto de datos utilizado en este proyecto es `diabetes.csv`. Contiene información sobre diversas variables médicas y un indicador de si el paciente tiene diabetes (Outcome).

## Metodología

El análisis se realizó en las siguientes etapas:

1.  **Limpieza de Datos:**
    *   Identificación y manejo de valores atípicos (outliers), especialmente aquellos registrados como cero en columnas donde fisiológicamente no es posible (como Glucosa, Presión Arterial, etc.).
    *   Imputación de valores cero con la mediana para preservar la mayor cantidad de datos posible sin introducir sesgos significativos.
    *   Verificación de duplicados y valores nulos (no se encontraron duplicados ni nulos después de la limpieza).

2.  **Exploración de Datos (EDA):**
    *   Análisis de estadísticas descriptivas para entender la distribución de las variables.
    *   Visualización de distribuciones univariadas (histogramas y boxplots) para identificar sesgos y outliers.
    *   Análisis de la matriz de correlación para entender las relaciones entre las variables predictoras y con la variable objetivo. Las variables `glucose`, `bmi` y `age` mostraron las correlaciones más fuertes con la variable `outcome`.
    *   Visualización del desbalance de clases en la variable objetivo.

3.  **Implementación de Modelos de Clasificación:**
    *   Se implementaron dos modelos de clasificación: Random Forest y XGBoost.
    *   Se utilizó un pipeline de preprocesamiento que incluyó la estandarización de las características numéricas.
    *   Se dividieron los datos en conjuntos de entrenamiento y prueba.
    *   Se entrenaron los modelos utilizando el conjunto de entrenamiento. Se consideró el desbalance de clases en Random Forest utilizando `class_weight='balanced'`.

4.  **Evaluación de Modelos:**
    *   Los modelos se evaluaron utilizando métricas comunes de clasificación: Accuracy, Precision, Recall, F1-score y Matriz de Confusión.
    *   Se generaron curvas ROC y se calculó el Área bajo la Curva (AUC) para visualizar y cuantificar el rendimiento de los modelos, especialmente en la capacidad de distinguir entre las clases.

5.  **Optimización de Hiperparámetros:**
    *   Se utilizó `GridSearchCV` para encontrar los mejores hiperparámetros para el modelo Random Forest, optimizando el F1-score, una métrica adecuada para conjuntos de datos desbalanceados.

6.  **Comparación de Rendimiento:**
    *   Se comparó el rendimiento del Random Forest inicial, Random Forest optimizado y XGBoost inicial utilizando una tabla de métricas.

## Conclusiones Clave

*   Los datos presentaban valores cero en columnas relevantes que fueron manejados mediante imputación con la mediana.
*   La exploración de datos reveló que `glucose`, `bmi` y `age` son los predictores más fuertemente correlacionados con la diabetes.
*   La optimización del modelo Random Forest resultó en una ligera mejora en el Recall y F1-score para la clase positiva (diabetes), lo cual es importante para minimizar los falsos negativos en un contexto médico.
*   Entre los modelos evaluados en sus configuraciones iniciales y optimizadas, el **Random Forest optimizado** mostró el mejor equilibrio general de métricas, particularmente un buen Recall para la clase positiva, lo que lo convierte en el modelo más adecuado para este problema de predicción de diabetes en este dataset.

## Recomendaciones

*   Considerar la optimización de hiperparámetros para el modelo XGBoost para potencialmente mejorar su rendimiento.
*   Explorar técnicas adicionales de manejo de desbalance de clases si es necesario.
*   Validar el modelo final en un conjunto de datos independiente si está disponible para asegurar su generalización.

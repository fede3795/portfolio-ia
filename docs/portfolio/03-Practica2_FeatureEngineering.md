---
title: "Cómo mejorar predicciones en el Titanic con ingeniería de características"
date: 2025-08-25
---

# Cómo mejorar predicciones en el Titanic con ingeniería de características

Esta práctica avanza desde el análisis exploratorio hacia la construcción de nuestro primer modelo predictivo para el dataset del Titanic.

## Contexto
Después de explorar los datos en la Práctica 1, el siguiente paso es prepararlos para un algoritmo de Machine Learning. Esto involucra dos procesos clave: la **limpieza de datos** (imputación de valores faltantes) y el **Feature Engineering** (creación de nuevas variables predictivas). Finalmente, se construye y evalúa un modelo simple de Regresión Logística, comparándolo contra un modelo base para medir su efectividad.

## Objetivos
- Aplicar técnicas de imputación de datos para manejar valores faltantes en `Age`, `Fare` y `Embarked`.
- Crear nuevas características (`FamilySize`, `IsAlone`, `Title`) para mejorar el poder predictivo del dataset.
- Entrenar un modelo `DummyClassifier` como baseline y un modelo `LogisticRegression`.
- Evaluar y comparar el rendimiento de ambos modelos utilizando `accuracy`, `classification_report` y la `matriz de confusión`.

## Actividades (con tiempos estimados)

| Actividad | Tiempo | Resultado Esperado |
| :--- | :---: | :--- |
| **Investigación de Scikit-learn** | 10 min | Comprensión de los componentes clave. |
| **Preprocesamiento y Features** | 15 min | Dataset limpio y con nuevas columnas. |
| **Entrenamiento de Modelos** | 15 min | Modelos baseline y de Regresión Logística entrenados. |
| **Evaluación y Análisis** | 10 min | Métricas de rendimiento y conclusiones. |

## Desarrollo
El flujo de trabajo se centró en transformar el dataset crudo en un formato adecuado para el modelado.

1.  **Imputación de Datos Faltantes:** Se rellenaron los valores nulos con estrategias específicas para cada columna: la **moda** para `Embarked` (categórica), la **mediana** para `Fare` (numérica con outliers), y una **mediana agrupada** por `Sex` y `Pclass` para `Age`, siendo esta última una técnica más precisa.
2.  **Ingeniería de Características (Feature Engineering):** Se crearon tres nuevas variables a partir de las existentes:
    * `FamilySize`: Unificando `SibSp` y `Parch` para cuantificar el tamaño de la familia.
    * `IsAlone`: Una variable binaria para capturar la condición de viajar solo.
    * `Title`: Extrayendo el título del pasajero desde la columna `Name`, lo que resultó ser un predictor muy potente.
3.  **Preparación para el Modelo:** Las variables categóricas como `Sex`, `Embarked` y `Title` fueron convertidas a un formato numérico mediante One-Hot Encoding (`pd.get_dummies`).
4.  **Modelado y Evaluación:** El dataset procesado se dividió en conjuntos de entrenamiento (80%) y prueba (20%) de forma estratificada. Se entrenaron y evaluaron un `DummyClassifier` (que predice la clase más frecuente) y un modelo de `LogisticRegression`.

## Evidencias
La evidencia principal de esta práctica son los resultados del modelo, que demuestran una mejora significativa sobre el baseline.

???+ info "Resultados del Modelo: Accuracy"

    La `accuracy` (precisión global) muestra una mejora drástica del modelo de Regresión Logística sobre el baseline. El modelo entrenado es **20 puntos porcentuales** más preciso que una simple suposición basada en la clase más frecuente. 🚀

    ```text
    Baseline acc: 0.6145
    LogReg acc  : 0.8156
    ```

???+ info "Reporte de Clasificación (Regresión Logística)"

    Este reporte desglosa el rendimiento del modelo para cada clase (0=No sobrevivió, 1=Sobrevivió), mostrando que el modelo es bastante balanceado, aunque ligeramente mejor prediciendo la clase mayoritaria (0).

    ```text
    Classification report (LogReg):
                  precision    recall  f1-score   support

               0       0.82      0.89      0.86       110
               1       0.80      0.70      0.74        69

        accuracy                           0.82       179
       macro avg       0.81      0.79      0.80       179
    weighted avg       0.81      0.82      0.81       179
    ```

???+ info "Matriz de Confusión (Regresión Logística)"

    La matriz de confusión nos muestra exactamente en qué se equivoca el modelo, siendo los Falsos Negativos (predecir que alguien no sobrevivió cuando sí lo hizo) el error más común.

    ```text
    [[98 12]
     [21 48]]
    ```
    **Interpretación de la Matriz:**

    | | Predijo: No sobrevivió | Predijo: Sobrevivió |
    | :--- | :---: | :---: |
    | **Real: No sobrevivió** | 98 (VN) | 12 (FP) |
    | **Real: Sobrevivió** | 21 (FN) | 48 (VP) |

## Reflexión
- **Qué aprendí:** Comprendí el flujo de trabajo completo para preparar datos y construir un primer modelo. La ingeniería de características no es solo una técnica, es un arte que mejora drásticamente el rendimiento. Entendí que un modelo simple pero bien evaluado es mucho más valioso que uno complejo sin un punto de comparación.
- **Qué mejorarías:** Experimentaría con otras variables creadas. Por ejemplo, se podría intentar crear "bins" o categorías para la edad (`Niño`, `Adulto`, `Mayor`) para ver si el modelo captura mejor esas relaciones.
- **Próximos Pasos:** El siguiente paso es intentar mejorar el rendimiento del modelo. Esto se puede hacer probando otros algoritmos (como Árboles de Decisión o Random Forest) o ajustando los hiperparámetros del modelo actual de Regresión Logística.

## Referencias
- **Documentación Scikit-learn:**
    - [`LogisticRegression`](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html)
    - [`DummyClassifier`](https://scikit-learn.org/stable/modules/generated/sklearn.dummy.DummyClassifier.html)
    - [`train_test_split`](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)
- **Notebook de Análisis:** [Práctica 2 - Titanic Feature Engineering](https://colab.research.google.com/drive/1e--1F7BANFxsP4bUh_OyEjL2Zd2qSOBB?usp=sharing)

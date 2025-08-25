---
title: "Práctica 4: Regresión Lineal y Logística"
date: 2025-08-25
---

# Práctica 4: Regresión Lineal y Logística

Implementación de dos de los modelos más fundamentales del Machine Learning supervisado para resolver problemas de predicción numérica y de clasificación.

## Contexto
Esta práctica consistió en un ejercicio guiado para construir, entrenar y evaluar dos modelos básicos:
1.  **Regresión Lineal:** Para predecir un valor numérico continuo (el precio de una casa en Boston).
2.  **Regresión Logística:** Para clasificar un diagnóstico en una de dos categorías (tumor benigno o maligno).

El objetivo fue comprender el flujo de trabajo completo para cada tipo de problema y aprender a interpretar sus respectivas métricas de evaluación.

## Objetivos
- Implementar un modelo de `LinearRegression` de principio a fin y evaluar su rendimiento con métricas como RMSE y R².
- Implementar un modelo de `LogisticRegression` y evaluarlo con métricas de clasificación como Accuracy, F1-Score y la Matriz de Confusión.
- Entender las diferencias prácticas entre un problema de regresión y uno de clasificación.
- Consolidar el uso de la librería `scikit-learn` para tareas de modelado.

## Actividades (con tiempos estimados)

| Actividad | Tiempo | Resultado Esperado |
| :--- | :---: | :--- |
| **Regresión Lineal** | 20 min | Modelo entrenado y métricas de error calculadas. |
| **Regresión Logística** | 20 min | Modelo entrenado y métricas de clasificación calculadas. |
| **Análisis y Comparación** | 10 min | Respuestas a las preguntas de reflexión. |
| **Documentación** | 15 min | Entrada del portafolio completada. |

## Desarrollo
El desarrollo se dividió en dos partes independientes, cada una abordando un tipo de problema distinto.

Para la **Regresión Lineal**, se utilizó el dataset "Boston Housing". Se cargaron los datos, se definieron la variable objetivo (`medv`) y las predictoras, se dividieron los datos en conjuntos de entrenamiento y prueba (80/20), y finalmente se entrenó un modelo `LinearRegression`.

Para la **Regresión Logística**, se usó el dataset "Breast Cancer" incluido en `scikit-learn`. El proceso fue similar: se identificaron la variable objetivo (diagnóstico) y las predictoras, se dividieron los datos y se entrenó un modelo `LogisticRegression`. La principal diferencia radicó en el tipo de predicción (una categoría en lugar de un número) y las métricas utilizadas para la evaluación.

## Evidencias
Los resultados de cada modelo demuestran su efectividad en la tarea para la que fueron diseñados.

???+ info "Resultados del Modelo de Regresión Lineal (Precios de Casas)"

    El modelo fue capaz de explicar una porción significativa de la variabilidad de los precios de las casas, con un error promedio interpretable.

    - **Error Promedio (RMSE):** $4.93k (El modelo se equivoca en promedio en $4,930).
    - **Coeficiente de Determinación (R²):** 0.711 (El modelo explica el **71.1%** de la varianza en los precios de las casas).

???+ info "Resultados del Modelo de Regresión Logística (Diagnóstico Médico)"

    El modelo de clasificación alcanzó un altísimo nivel de precisión, demostrando ser muy efectivo para esta tarea de diagnóstico.

    - **Exactitud (Accuracy):** 95.6% (El modelo acierta el diagnóstico en más de 95 de cada 100 casos).
    - **F1-Score:** 0.965 (Un excelente balance entre la precisión y la capacidad de detectar todos los casos).
    - **Matriz de Confusión:**
        | | Predijo: Maligno | Predijo: Benigno |
        | :--- | :---: | :---: |
        | **Real: Maligno** | 39 | 4 |
        | **Real: Benigno** | 1 | 70 |
    
    - **Observación Clave:** El modelo solo cometió un error grave (Falso Negativo), prediciendo "benigno" cuando era "maligno".

## Reflexión
- **Qué aprendí:** La diferencia fundamental entre predecir un número (regresión) y una categoría (clasificación). Aprendí que cada tipo de problema requiere un tipo de modelo y, crucialmente, un conjunto de métricas de evaluación diferentes.
- **Qué mejorarías:** Aunque los modelos base funcionaron bien, se podría explorar el impacto del escalado de características (`StandardScaler`) en el rendimiento, especialmente para la Regresión Logística.
- **Próximos Pasos:** Aplicar estos modelos a nuevos datasets y comenzar a explorar algoritmos más complejos (como Árboles de Decisión o Random Forest) para comparar su rendimiento con estos modelos base.

## Referencias
- **Datasets:** Boston Housing y Breast Cancer Wisconsin (UCI).
- **Documentación:** [`LinearRegression`](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html) y [`LogisticRegression`](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html).
- **Notebook de Análisis:** [Práctica 4 - Regresión Lineal y Logística](https://colab.research.google.com/drive/1e--1F7BANFxsP4bUh_OyEjL2Zd2qSOBB?usp=sharing)

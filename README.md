# Clasificación de Fármacos con Árboles de Decisión

## 📝 Descripción del Proyecto

Este proyecto utiliza un modelo de **Árbol de Decisión** para clasificar y predecir qué tipo de fármaco (`Drug`) es el más adecuado para un paciente en función de sus características demográficas y médicas. Se comparan dos criterios de división, **Gini** y **Entropía**, para evaluar su efectividad en la construcción del árbol.

---

## 📊 Datos Utilizados

El conjunto de datos, cargado desde el archivo `drugs.csv`, contiene información sobre 200 pacientes. Las características utilizadas para el modelo son:

- `Age`: Edad del paciente.
- `Sex`: Sexo del paciente (F/M).
- `BP`: Nivel de presión arterial (BAJA, NORMAL, ALTA).
- `Cholesterol`: Nivel de colesterol (NORMAL, ALTO).
- `Na_to_K`: Proporción de sodio a potasio en sangre.

La variable objetivo a predecir es:

- `Drug`: El tipo de fármaco recomendado (drugA, drugB, drugC, drugX, drugY).

---

## 🛠️ Técnicas y Metodología

El proyecto se desarrolló siguiendo los siguientes pasos:

### **1. Preprocesamiento de Datos**

- **Codificación de Variables Categóricas:** Las características no numéricas (`Sex`, `BP`, `Cholesterol`) se convirtieron a valores numéricos utilizando `LabelEncoder` de Scikit-learn para que pudieran ser procesadas por el modelo.

### **2. División del Conjunto de Datos**

- Los datos se dividieron en un conjunto de **entrenamiento (80%)** y un conjunto de **prueba (20%)** para entrenar y evaluar el modelo de manera objetiva.

### **3. Modelado y Comparación de Criterios**

Se entrenaron y evaluaron dos modelos de Árbol de Decisión:

1.  **Criterio Gini:** Utiliza el índice de impureza de Gini para seleccionar el mejor punto de división en los nodos del árbol.
2.  **Criterio de Entropía:** Utiliza la ganancia de información (basada en la entropía) para decidir las divisiones.

---

## 📈 Resultados

Ambos modelos, tanto el que utilizó el criterio **Gini** como el de **Entropía**, lograron un rendimiento perfecto en el conjunto de datos de prueba.

- **Accuracy, Precision, Recall y F1-Score:** Todas las métricas de evaluación para ambos modelos fueron del **100%**.
- **Matriz de Confusión:** Las matrices de confusión mostraron que no hubo ninguna clasificación incorrecta, con todos los valores fuera de la diagonal principal siendo cero.
- **Visualización del Árbol:** Se generaron visualizaciones de los árboles de decisión, las cuales revelaron que ambos criterios produjeron una estructura de decisión idéntica.

## ⭐ Conclusiones

Para este conjunto de datos específico, tanto el criterio **Gini** como el de **Entropía** resultaron ser igualmente efectivos, construyendo un árbol de decisión perfecto que clasifica correctamente todos los casos de prueba.

El árbol de decisión generado sigue una lógica clara para la recomendación del fármaco:

1.  La primera y más importante decisión se basa en la **proporción de Sodio a Potasio (`Na_to_K`)**.
2.  Si esta proporción es superior a 14.829, se recomienda **drugY**.
3.  Si es inferior, la decisión pasa a depender de la **Edad (`Age`)** y la **Presión Arterial (`BP`)** para determinar si se debe administrar **drugA**, **drugB**, **drugX** o **drugC**.

### Predicción sobre un Caso Hipotético

Se probó el modelo con un paciente hipotético. El modelo predijo que el fármaco adecuado para este paciente era **Drug_Y**, demostrando la aplicabilidad del árbol para tomar decisiones basadas en nuevos datos.

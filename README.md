# 📊 Análisis Predictivo de Churn de Clientes en Telecomunicaciones

Este repositorio contiene el análisis completo y el desarrollo de un modelo de **Machine Learning** para predecir la cancelación (**churn**) de clientes en una empresa de telecomunicaciones.  
El flujo de trabajo sigue un enfoque profesional: **preparación de datos → modelado → optimización → evaluación**.

---

## 📌 Índice
1. [Propósito del proyecto](#-propósito-del-proyecto)
2. [Estructura del repositorio](#-estructura-del-repositorio)
3. [Preparación de los datos](#-preparación-de-los-datos)
4. [Pipeline y decisiones de modelado](#-pipeline-y-decisiones-de-modelado)
5. [Manejo del desbalance de clases](#-manejo-del-desbalance-de-clases)
6. [Optimización de hiperparámetros](#-optimización-de-hiperparámetros)
7. [Insights y visualizaciones](#-insights-y-visualizaciones)
8. [Ejecución del proyecto](#️-ejecución-del-proyecto)
9. [Autor](#-autor)

---

## 🎯 Propósito del proyecto
Construir y optimizar un modelo de clasificación que prediga con alta precisión la probabilidad de que un cliente cancele su servicio.  
Beneficios clave:
- 📉 Reducir la tasa de cancelación.
- 💰 Maximizar el *Customer Lifetime Value*.
- 🎯 Optimizar estrategias de retención enfocándose en clientes con mayor riesgo.

---


## 🧹 Preparación de los datos
- **Clasificación de variables:**
  - Numéricas: `tenure`, `MonthlyCharges`, `TotalCharges`, `SeniorCitizen`.
  - Categóricas: `gender`, `Partner`, `Dependents`, `Contract`, `InternetService`, etc.
- **Preprocesamiento en pipeline:**
  - `StandardScaler` para variables numéricas.
  - `OneHotEncoder(drop='first')` para categóricas (evita multicolinealidad).
- **División del dataset:**
  - `train_test_split` con `stratify=y` (80% entrenamiento / 20% prueba).

---

## 🧠 Pipeline y decisiones de modelado
- Uso de `Pipeline` para encapsular preprocesamiento, balanceo y modelado.
- Selección de características en dos fases:
  1. **RFECV** con `RandomForestClassifier`.
  2. Validación estadística con `statsmodels.Logit`.
- Modelos evaluados: `RandomForestClassifier`, `LogisticRegression`, `GradientBoosting`, etc.
- Métrica principal: **ROC AUC** (más robusta que accuracy en clases desbalanceadas).

---

## ⚖️ Manejo del desbalance de clases
- Aplicación de **SMOTE** dentro del pipeline para sobremuestrear la clase minoritaria.
- Objetivo: mejorar el *recall* en clientes que cancelan.

---

## 🛠 Optimización de hiperparámetros
- Búsqueda exhaustiva con `GridSearchCV` (cv=10, scoring='roc_auc').
- Combinaciones optimizadas según el modelo seleccionado.

---

## 🔍 Insights y visualizaciones
Algunos hallazgos clave del EDA:
- 📅 Clientes con contratos mes a mes → mayor probabilidad de churn.
- ⏳ A mayor antigüedad (*tenure*), menor tasa de cancelación.
- 🔒 Servicios adicionales como `OnlineSecurity` y `TechSupport` → mayor lealtad.

**Visualizaciones disponibles:**
- `/visualizaciones/matriz_confusion_final.png`
- `/visualizaciones/importancia_features_final.png`

---

## ▶️ Ejecución del proyecto

**1️⃣ Clonar el repositorio**
```bash
git clone https://github.com/NannoFloresCif/Telecom_X_Parte_2_Hernan_Flores.git
```
2️⃣ Instalar dependencias
```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn statsmodels
```
3️⃣  Ejecutar el notebook
```bash
jupyter notebook analisis_churn.ipynbcd proyecto-churn
```

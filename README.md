# 📡 TelecomX LATAM — Parte 2: Predicción de Cancelación (Churn)

## 📌 Descripción

Segunda fase del proyecto **Challenge Data Science de Alura LATAM** para Telecom X. A partir del análisis exploratorio de la Parte 1, se construye un pipeline completo de **Machine Learning** para predecir qué clientes tienen mayor probabilidad de cancelar sus servicios, permitiendo al equipo tomar decisiones estratégicas de retención de forma anticipada.

---

## 🎯 Objetivos

- ✅ Preparar los datos para modelado (codificación, normalización, manejo del desbalance)
- ✅ Analizar la correlación entre variables y el churn
- ✅ Entrenar y comparar 4 modelos de clasificación
- ✅ Evaluar métricas: Exactitud, Precisión, Recall, F1-Score y AUC-ROC
- ✅ Interpretar la importancia de variables en cada modelo
- ✅ Generar un informe con conclusiones y recomendaciones estratégicas

---

## 📁 Estructura del Proyecto

```
telecomx-latam/
│
├── TelecomX_LATAM_Completo.ipynb     # Parte 1: ETL + EDA
├── TelecomX_LATAM_Parte2.ipynb       # Parte 2: Machine Learning (este notebook)
├── README.md                          # Este archivo
├── TelecomX_diccionario.md            # Diccionario de datos
└── datos/
    └── TelecomX_Data.json             # Dataset original
```

---

## ⚙️ Pipeline de Machine Learning

### 1. Preprocesamiento
| Paso | Detalle |
|---|---|
| Eliminación de columnas | `ID_Cliente` y columnas auxiliares removidas |
| One-Hot Encoding | Variables categóricas con `pd.get_dummies` |
| Desbalance de clases | `class_weight='balanced'` en todos los modelos |
| Normalización | `StandardScaler` aplicado solo para Regresión Logística |
| División de datos | 80% entrenamiento / 20% prueba con `stratify=y` |

### 2. Modelos Entrenados

| Modelo | Normalización | Justificación |
|---|---|---|
| **Regresión Logística** | ✅ Sí | Sensible a la escala de los datos |
| **Árbol de Decisión** | ❌ No | Basado en umbrales, invariante a escala |
| **Random Forest** | ❌ No | Ensemble de árboles, robusto sin escalar |
| **Gradient Boosting** | ❌ No | Boosting secuencial, invariante a escala |

### 3. Métricas de Evaluación
- Exactitud (Accuracy)
- Precisión (Precision)
- Recall (Sensibilidad)
- F1-Score
- AUC-ROC
- Matriz de Confusión

---

## 🏆 Resultados Principales

**Mejor modelo: Gradient Boosting** — mayor F1-Score y AUC-ROC, mejor balance entre precisión y recall.

### Variables más influyentes en el Churn:

| Variable | Efecto |
|---|---|
| Tipo de contrato (mes a mes) | 🔴 Aumenta churn |
| Meses de contrato (antigüedad) | 🟢 Reduce churn |
| Servicio de Fibra Óptica | 🔴 Aumenta churn |
| Cargo mensual alto | 🔴 Aumenta churn |
| Pago por cheque electrónico | 🔴 Aumenta churn |
| Cargo total acumulado | 🟢 Reduce churn |

---

## 🚀 Cómo Ejecutar el Proyecto

### Opción 1 — Google Colab (recomendado)
1. Abre [Google Colab](https://colab.research.google.com)
2. Ve a **Archivo → Subir notebook**
3. Selecciona `TelecomX_LATAM_Parte2.ipynb`
4. Ejecuta todas las celdas: `Runtime → Run all`

> Los datos se cargan automáticamente desde la API, sin necesidad de subir archivos.

### Opción 2 — Local
```bash
git clone https://github.com/tu-usuario/telecomx-latam.git
cd telecomx-latam
pip install pandas numpy matplotlib scikit-learn
jupyter notebook TelecomX_LATAM_Parte2.ipynb
```

---

## 🧰 Tecnologías Utilizadas

| Herramienta | Uso |
|---|---|
| **Python 3** | Lenguaje principal |
| **Pandas / NumPy** | Manipulación de datos |
| **Matplotlib** | Visualización |
| **Scikit-learn** | Modelos ML, métricas y preprocesamiento |
| **Google Colab** | Entorno de desarrollo |

---

## 💡 Recomendaciones Estratégicas

- 🎯 Descuentos para migrar clientes a contratos anuales o bianuales
- 🚀 Programa de acompañamiento en los primeros 6 meses de contrato
- 💡 Revisar el servicio de Fibra Óptica (precio vs. experiencia percibida)
- 💳 Incentivar métodos de pago automático sobre cheque electrónico
- 📦 Crear paquetes de servicios con beneficios por fidelidad
- 🤖 Implementar Gradient Boosting en producción para scoring mensual de riesgo

---

## 👤 Autor

Desarrollado como parte del **Challenge 2 (Parte 2) — Data Science Alura LATAM**

*📅 2025 — TelecomX LATAM | Machine Learning — Churn Prediction*

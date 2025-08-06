# 📊 Proyecto de Minería de Datos - Clima de Australia  



## ⚡ TL;DR

Este proyecto predice si lloverá mañana en Australia usando datos meteorológicos históricos. Se aplicó la metodología CRISP-DM con Python y Random Forest, priorizando el `Recall` sobre la exactitud para decisiones agrícolas. El modelo final detecta correctamente 3 de cada 4 días de lluvia, ayudando a optimizar el riego en cooperativas agrícolas.


## 📌 Introducción

Este proyecto aplica técnicas de **minería de datos** utilizando el enfoque **CRISP-DM** para analizar y predecir si lloverá al día siguiente, a partir de datos meteorológicos históricos de Australia. Está desarrollado con herramientas como **Python, Pandas, Scikit-Learn y visualización con Seaborn/Matplotlib**.

El propósito de este análisis es demostrar competencias propias de un **analista de datos**, enfocándome en la exploración, preparación y modelado estadístico, sin entrar en tareas propias del rol de ingeniero de datos.

## 🏢 Contexto Empresarial

Este proyecto fue desarrollado para **ClimaSmart Analytics S.A.**, una empresa dedicada a proveer soluciones de inteligencia de datos para el sector agroclimático. El cliente principal es una **cooperativa agrícola australiana** interesada en mejorar su capacidad de **predicción de lluvias** para optimizar decisiones de riego.

Actualmente, los agricultores dependen de informes diarios de estaciones meteorológicas, pero no cuentan con un modelo analítico que les permita anticipar si **lloverá mañana**. Este proyecto busca llenar ese vacío mediante un modelo de clasificación predictivo basado en datos históricos.

### 🎯 Objetivos del Proyecto

- Predecir si lloverá al día siguiente (`RainTomorrow`) usando variables meteorológicas.
- Mejorar la planificación agrícola y reducir pérdidas por riego innecesario.

### ✅ Criterios de Éxito

- Alcanzar una precisión mínima del **80%** en la predicción de lluvia.
- Visualizar el comportamiento histórico de lluvias de forma clara y accesible.
- Entregar un prototipo funcional en un plazo de **8 semanas**.
- Permitir que el cliente tome decisiones de riego basadas en el modelo.



## 💡 El Hallazgo Clave: Más Allá de la Exactitud

El descubrimiento más importante de este proyecto no fue técnico, sino estratégico: una **exactitud (accuracy) del 81% puede ser engañosa**. El primer modelo, a pesar de su alta exactitud, fallaba en detectar más de la mitad de los días de lluvia reales. Para un agricultor, esto representa un riesgo inaceptable.

Por ello, la métrica decisiva fue el **`Recall` (Sensibilidad)**. Para el negocio, es mucho más costoso no regar un día que se necesitaba (un falso negativo) que omitir el riego en un día que finalmente fue seco (un falso positivo).

El modelo final, un **Random Forest**, fue seleccionado por su capacidad para **detectar correctamente 3 de cada 4 días de lluvia (Recall del 74%)**, ofreciendo una herramienta verdaderamente útil y fiable para el cliente.

![Matriz de Confusión del Modelo Random Forest](Gráficos/Matriz%20de%20confusión%20RF.png)

- Como muestra la matriz, el modelo identifica correctamente 3,311 días de lluvia (Verdaderos Positivos) y solo falla en detectar 1,161 (Falsos Negativos), lo que demuestra su alto `Recall` y su valor para el negocio.

## 🔍 Fases del Proyecto (Metodología CRISP-DM)

El notebook [simple.ipynb](simple.ipynb) sigue un flujo de trabajo estructurado:

1.  **Comprensión del Negocio y de los Datos**:
    *   Se definió el objetivo, los riesgos y los criterios de éxito del proyecto.
    *   Se realizó un **Análisis Exploratorio de Datos (EDA)** para entender las relaciones entre las variables meteorológicas.
    *   Se identificaron desafíos clave: valores nulos, distribuciones sesgadas y un fuerte desbalance de clases.

2.  **Preparación de Datos**:
    *   **Limpieza**: Imputación de valores nulos usando la media para variables numéricas y la moda para categóricas.
    *   **Transformación**: Aplicación de una transformación logarítmica a variables con alto sesgo para normalizar su distribución.
    *   **Codificación y Escalado**: Se usó `OneHotEncoder` para variables categóricas y `StandardScaler` para las numéricas, asegurando que los modelos funcionen correctamente.

3.  **Modelado y Evaluación**:
    *   Se entrenaron y evaluaron tres algoritmos: **Naive Bayes**, **Árbol de Decisión** y **Random Forest**.
    *   Se utilizó `GridSearchCV` para optimizar los hiperparámetros de los modelos, buscando el mejor **F1-Score** para balancear precisión y recall.
    *   El **Random Forest** demostró ser el modelo superior, logrando el mejor equilibrio entre detectar la lluvia y evitar falsas alarmas.

4.  **Implementación**:
    *   Se construyó un `Pipeline` final en Scikit-Learn que encapsula todo el proceso (preprocesamiento y modelo).
    *   Este pipeline se exportó al archivo `modelo_lluvia_australia.pkl` para su uso futuro.

## 📂 Estructura del Repositorio

```
/Mineria-de-datos---Clima-de-Australia
│
├── 📊 Gráficos/
│   └── 🖼️ Matriz de confusión RF.png        # Visualizaciones generadas
│
├── 📘 README.md                             # Este archivo, la documentación del proyecto
├── 📦 requirements.txt                      # Librerías de Python necesarias
├── 📓 simple.ipynb                          # Notebook con todo el análisis (EDA, preprocesamiento, modelado)
├── 🌦️ Weather Test Data.csv                 # Datos de prueba para evaluar el modelo
└── 🌤️ Weather Training Data.csv             # Datos de entrenamiento para construir el modelo
```

## 🛠️ Tecnologías Usadas

- Python 🐍  
- Pandas & NumPy 📊  
- Scikit-Learn 🤖  
- Matplotlib & Seaborn 🎨  

## 📌 Cómo Usar Este Proyecto

1. **Clonar el repositorio:**

   ```bash
   git clone https://github.com/YaredLevi/MineriaDeDatos-ClimaAustralia.git
   ```

2. **Instalar dependencias:**

   ```bash
   pip install -r requirements.txt
   ```

3. **Ejecutar el Notebook:**

   ```bash
   jupyter notebook simple.ipynb
   ```

## 📎 Recursos

📂 **Dataset utilizado**: https://www.kaggle.com/datasets/arunavakrchakraborty/australia-weather-data  
📌 **Notebook en Kaggle**: https://www.kaggle.com/code/yaredlevi/clima-de-australia

## 👤 Sobre mí

Soy **egresado de enseñanza superior**, actualmente desarrollando mi portafolio profesional con foco en el **análisis de datos**. Me interesa aplicar conocimientos en limpieza, visualización y modelado de datos para resolver problemas reales. Este proyecto forma parte de mi camino formativo y refleja mi compromiso con metodologías como **CRISP-DM** y el uso de herramientas clave del entorno Python.

📫 **Contacto**: Yaredlevi@outlook.com  
🔗 [LinkedIn](https://www.linkedin.com/in/yaredlevi)
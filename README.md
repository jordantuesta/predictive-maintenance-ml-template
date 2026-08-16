# 🔧 Plantilla ML para Mantenimiento Predictivo (No-Code)

Plantilla interactiva en Jupyter/Colab que permite **entrenar y evaluar modelos de Machine Learning** para predecir fallas de maquinaria, **sin escribir código**. Usa widgets (`ipywidgets`) para cargar datos, elegir variables, seleccionar un modelo y ver métricas y gráficos de resultado, todo desde celdas ya ejecutables.

Pensada como plantilla reutilizable: puedes usar el dataset de ejemplo incluido o **subir tu propio CSV** y entrenar modelos sobre tus propios datos, sin tocar el código.

## ¿Qué hace el proyecto?

El notebook guía paso a paso por un flujo completo de Machine Learning:

1. **Preparación del entorno** — instala e importa automáticamente las librerías necesarias.
2. **Carga de datos** — usa el dataset de ejemplo (AI4I 2020) o sube tu propio CSV con un botón.
3. **Exploración rápida** — dimensiones, tipos de datos, nulos, estadísticas descriptivas y distribuciones.
4. **Selección de target y features** — mediante menús desplegables y selección múltiple.
5. **Detección automática del tipo de problema** — clasificación o regresión, según el target elegido.
6. **Selección de modelo** — elige entre varios algoritmos según el tipo de problema.
7. **Entrenamiento con un clic** — divide los datos, entrena, y muestra métricas, matriz de confusión (o real vs. predicho), e importancia de variables.
8. **Notas y buenas prácticas** — recomendaciones sobre comparación de modelos, *data leakage* y datasets desbalanceados.

## Cómo abrirlo en Google Colab (paso a paso)

**No copies ni pegues el contenido del notebook como código.** Sube el archivo `.ipynb` directamente:

1. Descarga de este repositorio los archivos `Plantilla_Mantenimiento_Predictivo_ML.ipynb` y `data/ai4i2020.csv` (botón "Code" → "Download ZIP", o descarga cada archivo individualmente).
2. Ve a [colab.research.google.com](https://colab.research.google.com).
3. Selecciona **Archivo → Subir cuaderno (Upload notebook)** y elige `Plantilla_Mantenimiento_Predictivo_ML.ipynb`.
4. Una vez abierto el notebook, en el panel izquierdo abre la pestaña de **archivos** (ícono de carpeta) y sube `ai4i2020.csv`.
5. Crea una carpeta llamada `data` dentro del entorno de Colab (clic derecho → "Nueva carpeta") y mueve `ai4i2020.csv` dentro de ella, de forma que quede en la ruta `data/ai4i2020.csv` (la misma estructura que usa el notebook por defecto).
   - Alternativa más simple: en la celda de carga de datos, usa el botón **"Subir CSV"** del propio notebook para cargar el archivo directamente, sin necesidad de crear carpetas.
6. Ejecuta las celdas en orden (**Entorno de ejecución → Ejecutar todas**, o celda por celda con Shift+Enter).

> Nota: los archivos subidos a Colab de esta forma son temporales y se pierden al cerrar la sesión, a menos que los guardes en tu Google Drive.

También puedes abrirlo localmente con Jupyter Notebook/JupyterLab clonando este repositorio; en ese caso la ruta `data/ai4i2020.csv` ya funciona sin pasos adicionales.

## Modelos incluidos

**Clasificación** (cuando el target tiene pocas categorías, ej. falla/no falla):
- Regresión Logística
- Árbol de Decisión
- Random Forest
- Gradient Boosting
- SVM (Máquina de Vectores de Soporte)
- K-Vecinos Cercanos (KNN)
- Naive Bayes

**Regresión** (cuando el target es una variable numérica continua):
- Regresión Lineal
- Árbol de Decisión
- Random Forest
- Gradient Boosting
- SVR (SVM para regresión)
- K-Vecinos Cercanos (KNN)

El notebook detecta automáticamente el tipo de problema según la variable objetivo seleccionada y muestra solo los modelos correspondientes.

## Dataset: fuente y licencia

Este proyecto usa el dataset **AI4I 2020 Predictive Maintenance Dataset**, publicado en el [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/601/ai4i+2020+predictive+maintenance+dataset).

- **Licencia del dataset:** CC BY 4.0 (Creative Commons Attribution 4.0 International).
- **Cita sugerida:** Matzka, S. (2020). AI4I 2020 Predictive Maintenance Dataset [Dataset]. UCI Machine Learning Repository.

El dataset simula datos de sensores de una máquina industrial (temperatura del aire y del proceso, velocidad rotacional, torque, desgaste de herramienta) junto con un indicador de falla y el tipo de falla ocurrida.

## ⚠️ Nota sobre *data leakage*

La columna **`Failure Type`** indica directamente qué tipo de falla ocurrió (o si no hubo falla), por lo que **no debe usarse como feature/predictor** — filtra la respuesta del target y produce modelos con métricas artificialmente perfectas pero inútiles en un escenario real. El notebook la excluye de las features sugeridas por defecto; si seleccionas features manualmente, evita incluirla.

Adicionalmente, el dataset está desbalanceado (las fallas representan ~3.4% de los casos), así que un *accuracy* alto puede ser engañoso: presta atención a *precision*, *recall* y *f1-score*, especialmente para la clase minoritaria.

## Usar tu propio dataset

El notebook incluye un botón de carga de CSV: si subes tu propio archivo, este reemplaza al dataset de ejemplo y el resto del flujo (exploración, selección de features, entrenamiento) se adapta automáticamente a tus columnas.

## Licencia

El código de este repositorio está bajo licencia [MIT](LICENSE). El dataset (`data/ai4i2020.csv`) conserva su licencia original **CC BY 4.0** del UCI Machine Learning Repository — consulta la fuente citada arriba para más detalles de atribución.

# Proyecto: Telecom X - Etapa 2 - Machine Learning para Churn de Clientes

<img width="720" height="480" alt="ml_churn" src="https://github.com/user-attachments/assets/47f70705-edb9-45d8-937d-f33dd452d2a5" />

## Índice 📋

1. Descripción del proyecto.
2. Acceso al proyecto
3. Etapas del proyecto.
4. Descripción de los datos
5. Resultados y conclusiones
6. Tecnologías utilizadas.
7. Agradecimientos.
8. Desarrollador del proyecto.

## 1. Descripción del proyecto 📚

* En el presente proyecto se desarrollaron múltiples modelos supervisados de Machine Learning con el objetivo de identificar clientes propensos a cancelar el servicio en una empresa de telecomunicaciones, seleccionando el modelo con mejor desempeño a través de métricas de evaluación específicas.
* Se aplicaron transformaciones a los datos para ajustarlos a los requerimientos de cada algoritmo, considerando la sensibilidad a escalas y la multicolinealidad entre variables.
* Se realizaron múltiples experimentos dentro de cada familia de algoritmos mediante la optimización de hiperparámetros, seleccionando el mejor modelo por familia para luego compararlos entre sí. El criterio de selección final priorizó la métrica **Recall**, con el fin de minimizar los falsos negativos (clientes que abandonan y no son detectados), sin comprometer significativamente la **Precisión**, para asegurar campañas de retención efectivas y sostenibles en términos de costos.
* Finalmente, se diseñó un entorno de simulación productiva con datos sintéticos para validar la operación del modelo a partir de entradas en su formato original.


## Acceso al proyecto 📂

Para obtener el proyecto tienes dos opciones:

1. Clonar el repositorio utilizando la línea de comandos. Solo debes dirigirte al directorio donde deseas clonar el mismo e ingresar el comando:
   `git clone https://github.com/ignaciomajo/proyecto_TelecomX_ML`

2. O puedes descargarlo directamente desde el repositorio en GitHub en el siguiente enlace:
   <p><a href="https://github.com/ignaciomajo/proyecto_TelecomX_ML">https://github.com/ignaciomajo/proyecto_TelecomX_ML</p>

   Esto te llevará a la siguiente pantalla, donde deberás seguir los siguientes pasos:

<img width="1072" height="672" alt="image" src="https://github.com/user-attachments/assets/d12f967f-0993-41b5-8619-2602d2376cf3" />
   
Esto descargará un archivo comprimido `.zip`, que podras alojar en el directorio que desees.


## 3. Etapas del proyecto 📝

1. Descripción del proyecto
2. Importación de librerías y configuraciones
   - Importación de librerias
   - Paths
   - Configuraciones
   - Funciones
3. Preprocesamiento de datos
   - Encoding de variables categóricas
   - Balance del dataset
   - Normalizacion de datos
   - Correlacion entre variables
   - Análisis de multicolinealidad
   - Análisis dirigido
4. Modelado de datos
   - Baseline Model - Decision Tree Classifier
   - Random Forest Classifier
   - Logistic Regression
   - K-Nearest Neighbors
   - XGBoost Classifier
   - Support Vector Machine
5. Evaluación Best Models
   - Métricas Generales
   - Subajuste (Underfitting) y Sobreajuste (Overfitting)
   - Matrices de confusión
   - Importancias y Coeficientes
6. Champion Model
7. Pipeline de prueba en entorno productivo
   - Generación de datos artificiales
   - Pipeline de prueba

## 4. Descripción de los datos 📊

La base de datos utilizada proviene de la etapa anterior del presente proyecto, donde se realizó exploración y limpieza de los datos, los cuales pueden obtenerse en el siguiente enlace:

<a href="https://github.com/ignaciomajo/proyecto_TelecomX/tree/main/src">Base de datos</a>

Se tomaron los archivos📄: 

* <a href="https://raw.githubusercontent.com/ignaciomajo/proyecto_TelecomX/refs/heads/main/src/preprocessed_TelecomX_data.json">preprocessed_TelecomX_data.json</a>
* <a href="https://raw.githubusercontent.com/ignaciomajo/proyecto_TelecomX/refs/heads/main/src/clientes_altovalor_abandonan.json">clientes_altovalor_abandonan.json</a>

Ambos archivos se integraron en un único dataset de **7152 observaciones**. El archivo **clientes_altovalor_abandonan.json** contiene los clientes identificados como outliers en la etapa anterior, que, aunque fueron apartados para un análisis aislado, se incluyeron en este proyecto para representar con mayor fidelidad el patrón general de comportamiento del cliente.

### Variables

| Variable           | Tipo       | Descripción breve                         | Valores originales                             | Preprocesado          |
| ------------------ | ---------- | ----------------------------------------- | ---------------------------------------------- | --------------------- |
| `customerID`       | Categórica | Identificador único del cliente           | String                                         | -                     |
| `Gender`           | Categórica | Género del cliente                        | `'Male'`, `'Female'`                           | One-hot-encoding      |
| `SeniorCitizen`    | Categórica | Indica si el cliente es mayor de 65 años  | `0`, `1`                                       | One-hot-encoding      |
| `Partner`          | Categórica | Si el cliente tiene pareja                | `'Yes'`, `'No'`                                | One-hot-encoding      |
| `Dependents`       | Categórica | Si el cliente tiene personas a cargo      | `'Yes'`, `'No'`                                | One-hot-encoding      |
| `PhoneService`     | Categórica | Si tiene servicio telefónico              | `'Yes'`, `'No'`                                | One-hot-encoding      |
| `MultipleLines`    | Categórica | Si tiene múltiples líneas telefónicas     | `'Yes'`, `'No'`,                               | One-hot-encoding      |
| `InternetService`  | Categórica | Tipo de conexión a internet               | `'DSL'`, `'Fiber optic'`, `'No'`               | One-hot-encoding      |
| `OnlineSecurity`   | Categórica | Seguridad en línea                        | `'Yes'`, `'No'`,                               | One-hot-encoding      |
| `OnlineBackup`     | Categórica | Respaldo en línea                         | `'Yes'`, `'No'`,                               | One-hot-encoding      |
| `DeviceProtection` | Categórica | Protección de dispositivo                 | `'Yes'`, `'No'`,                               | One-hot-encoding      |
| `TechSupport`      | Categórica | Soporte técnico                           | `'Yes'`, `'No'`,                               | One-hot-encoding      |
| `StreamingTV`      | Categórica | TV en streaming                           | `'Yes'`, `'No'`,                               | One-hot-encoding      |
| `StreamingMovies`  | Categórica | Películas en streaming                    | `'Yes'`, `'No'`,                               | One-hot-encoding      |
| `Contract`         | Categórica | Tipo de contrato                          | `'Month-to-month'`, `'One year'`, `'Two year'` | One-hot-encoding      |
| `PaperlessBilling` | Categórica | Si el cliente usa facturación electrónica | `'Yes'`, `'No'`                                | One-hot-encoding      |
| `PaymentMethod`    | Categórica | Método de pago                            | 4 categorías                                   | One-hot-encoding      |
| `Tenure`           | Numérica   | Antigüedad en meses                       | int, `0` a `72`                                | Igual/Escalado        |
| `ChargesMonthly`   | Numérica   | Costo mensual del servicio                | float                                          | Igual/Escalado        |
| `ChargesTotal`     | Numérica   | Costo total acumulado del cliente         | float                                          | Igual/Escalado        |
| `ChargesDaily`     | Numérica   | Estimación diaria del costo del cliente   | float (`Charges.Monthly/30`)                   | Descartada            |
| `Churn`            | Categórica | Si el cliente abandonó la empresa         | `'Yes'`, `'No'`                                | Label Encoding        |

### Balance de clases

Debido a un desbalance en la variable de respuesta (`Churn`), se llevó a cabo una reducción del Dataset utilizando el algoritmo `NearMiss Version 3`.
Se optó por reducir la clase mayoritaria para que el aprendizaje de los modelos estuviese basado en datos reales. Ya que, aún con justificación matemática, la creación de datos artificiales implica alimentar el modelo con clientes que no existen en la empresa. 

Esta reducción resultó en un conjunto de datos con **3362 observaciones** para el entrenamiento, y conservando la distribución original de los datos para la evaluación de modelos, con un total de **1073 observaciones**, con aproximadamente **72.3%** etiquetados como `Churn = 0` (clase mayoritaria) y **27.7%** etiquetados como `Churn = 1` (clase minoritaria.

Sin embargo, para la simulación del pipeline en entorno productivo, se generaron datos artificiales utilizando la técnica `SMOTENC`, y luego se tomó una muestra mantiendo la distribución inicial de las clases, ya que el objetivo de esto era demostrar el uso y capacidades del modelo, lo cual no se ve afectado por la utilización de datos creados de manera artificial.


### Codificación y reescalado de datos

Debido a los distintos requerimentos de cada familia de algoritmos de Machine Learning, el dataset balanceado fue transformado de diversas maneras para ajustarlos a las necesidades de cada familia.

* Para modelos basados en árboles: `Random Forest Classifier` y `XGBoost Classifier`
  - Codificación `One-hot`, descartando una variable cuando esta era de naturaleza binaria (dos categorías) a través del parámetro `drop='if_binary'`.
  - Variables numéricas: `Tenure`, `ChargesMonthly` y `ChargesTotal` no fueron escaladas ya que estos modelos no se ven afectados por la escala de los datos debido a su naturaleza basada en particiones y árboles.

* Para modelos lineales: `Logistic Regression` y `Support Vector Machine (kernel = 'linear')`
  - Codificación `One-hot` para variables categóricas con el parámetro `drop='first'` descartando la primera categoría de cada variable para evitar introducir multicolinealidad al modelo.
  - Variables numéricas: escaladas utilizando `Robust Scaler` debido a la presencia de valores atípicos, el cual utiliza la mediana y el rango intercuartílico (IQR) para escalar los datos (lo cual lo hace resistente a outliers), debido a la sensibilidad de dichos modelos a la escala de los datos.
  - Dataset: `X_linear`

* Para modelos basados en distancia: `K-Nearest Neighbors Classifier`
  - Codificación `One-hot` con el parámetro `drop='if_binary'`, ya que este tipo de modelos se beneficia de mayor cantidad de variables al calcular la distancia entre observaciones.
  - Variables numéricas escaladas con `Robust Scaler`, ya que el modelo es sensible a la escala de los datos.
  - Dataset: `X_scaled`
 
* La variable respuesta (Churn) fue codificada utilizando `Label Encoder`, transformando:
  - `'Yes'` -> `1`
  - `'No'` -> `0`

<br><br>
## 5. Resultados y conclusiones ✍️

### Modelos

Se evaluaron los modelos de cada familia para seleccionar un modelo campeón (**Champion Model**), el cual será implementado en un entorno simulado de producción.
Estos, fueron guardados y cargados como `Best {familia algoritmo}`:

| Modelo                       | Dataset                      | Accuracy | Precision | Recall | F1-score | AUC    | Umbral |
|------------------------------|------------------------------|----------|-----------|--------|----------|--------|--------|
| Best Random Forest           | X                            | 0.7698   | 0.5654    | 0.7273 | 0.6362   | 0.8326 | 0.5    |
| Best Logistic Regression     | X_linear[selected_features]  | 0.7633   | 0.5657    | 0.6229 | 0.5929   | 0.8137 | 0.5    |
| Best K-Nearest Neighbors     | X_linear                     | 0.7251   | 0.5027    | 0.6364 | 0.5617   | 0.7513 | 0.5    |
| Best XGBoost Classifier      | X                            | 0.7568   | 0.5464    | 0.7138 | 0.6190   | 0.8188 | 0.5    |
| Best Support Vector Machine  | X_linear                     | 0.7540   | 0.5563    | 0.5488 | 0.5525   | 0.8073 | 0.5    |

A los cuales se buscó llevar la métrica **Recall** a un valor mínimo de 0.85 al modificar el umbral de decisión del modelo:

| Modelo                       | Dataset                      | Accuracy | Precision | Recall | F1-score | AUC    | Umbral |
|------------------------------|------------------------------|----------|-----------|--------|----------|--------|--------|
| Best Random Forest           | X                            | 0.7148   | 0.4914    | 0.8620 | 0.6259   | 0.8326 | 0.39   |
| Best Logistic Regression     | X_linear[selected_features]  | 0.6747   | 0.4539    | 0.8620 | 0.5947   | 0.8137 | 0.39   |
| Best XGBoost Classifier      | X                            | 0.6925   | 0.4695    | 0.8552 | 0.6062   | 0.8188 | 0.38   |
| Best Support Vector Machine  | X_linear                     | 0.6785   | 0.4571    | 0.8620 | 0.5974   | 0.8073 | 0.38   |

***Nota:** ya que `Best K-Nearest Neighbors` no consiguió alcanzar el valor esperado en el rango de umbrales determinados, fue descartado en esta etapa de la evaluación*

Al evaluar las métricas obtenidas, se seleccionó el modelo `Best Random Forest` como **Champion Model** para implementación en entorno productivo, debido a su capacidad de generalización, ya que para alcanzar el nivel esperado de la métrica prioritaria (**Recall**), es el que menos incurre en errores de falsos positivos (clientes identificados como abandono, que no lo eran).

A pesar de mostrar cierto sobreajuste a los datos de entrenamiento, como puede verse en las tablas a continuación, `Best Random Forest` se mantiene como el mejor generalizador.


| Model	                       | Recall Train	 | Recall Test	     | Variación   |
|-------------------------------|----------------|------------------|-------------|
| Best Random Forest	           | 0.8769	       | 0.7273	        | -14.96%     |
| Best Logistic Regression	     | 0.6383	       | 0.6229	        | -1.54%      | 
| Best XGBoost Classifier	     | 0.7555	       | 0.7138	        | -4.17%      | 
| Best Support Vector Machine   | 0.5996	       | 0.5488	        | -5.08%      | 

| Model	                       | F1-score Train	 | F1-score Test	     | Variación   |
|-------------------------------|-------------------|---------------------|-------------|
| Best Random Forest	           | 0.8673	          | 0.6362              | -23.11%     |
| Best Logistic Regression	     | 0.6301	          | 0.5929	           | -3.72%      |
| Best XGBoost Classifier	     | 0.7591	          | 0.6190	           | -14.01%     |
| Best Support Vector Machine	  | 0.6126	          | 0.5525	           | -6.01%      |

Las **10 variables más importantes** determinadas por el modelo `Best Random Forest` son:

<img width="2963" height="1763" alt="Importancia_variables_RandomForest_importancias" src="https://github.com/user-attachments/assets/464d14c7-e239-44c6-a36e-04a272315f2b" />

Sin embargo, dado que este modelo no permite evaluar la dirección y magnitud del impacto en la Evasión de dichas variables. Por lo que, en el reporte ejecutivo presente en el directorio `reports` 📂, se complementó el análisis con los coeficientes determinados por `Best Logistic Regression`

<img width="2963" height="1763" alt="Coeficiente_variables_LogReg_best_coef" src="https://github.com/user-attachments/assets/d6ed9be9-6099-4dad-9ef1-385274af71f7" />
<br>

A partir de las cuales se llevó a cabo el siguiente análisis de impacto:

<img width="3570" height="1768" alt="tabla_coef_logreg" src="https://github.com/user-attachments/assets/422990ad-2f5f-4971-95bf-a8a0ec0a2e77" />

### Pipeline de prueba

Finalmente, se desarrolló la simulación de un pipeline para la implementación del modelo en entorno productivo, utilizando datos sintéticos generados con la técnica `SMOTENC`.
El mismo, recibe un archivo JSON (formato original de la base de datos) con datos crudos (sin ninguna transformación) para producir predicciones.
Cuenta con dos modos de utilización:

* `mode='production'`: que devuelve un archivo JSON con `CustomerID`, `Probabilidad Churn` y `Churn` *(Etiqueta: si Probabilidad Churn >= 0.39, Churn = 1, si Probabilidad Churn < 0.39, Churn = 0)*
* `mode='monitor'`: devuelve un archivo JSON con las métricas `Accuracy`, `Precision`, `Recall` y `F1-score`, y un campo con fecha y hora de ejecución del monitoreo.

Dicho pipeline realiza las transformaciones necesarias sobre los datos crudos utilizando los artefactos creados a lo largo del proyecto.

Los resultados pueden verse en:
* <a href="https://github.com/ignaciomajo/proyecto_TelecomX_ML/tree/main/champion/log/production">Resultados Pipeline Producción</a>
* <a href="https://github.com/ignaciomajo/proyecto_TelecomX_ML/tree/main/champion/log/monitor">Resultados Pipeline Monitoreo</a>


Este enfoque no solo permitió construir un modelo predictivo sólido, sino también demostrar su aplicabilidad real en entornos simulados, sentando las bases para su escalado y mantenimiento en producción.

## 6. Tecnologías utilizadas 🛠️

![Static Badge](https://img.shields.io/badge/Python-3.11.7-blue) <br>
![Static Badge](https://img.shields.io/badge/Numpy-1.26.4-green) ![Static Badge](https://img.shields.io/badge/pandas-2.2.2-green) ![Static Badge](https://img.shields.io/badge/matplotlib-3.10.0-green)
![Static Badge](https://img.shields.io/badge/seaborn-0.13.2-green) ![Static Badge](https://img.shields.io/badge/scikit--learn-1.5.2-green)
![Static Badge](https://img.shields.io/badge/imbalanced--learn-1.5.2-green) ![Static Badge](https://img.shields.io/badge/xgboost-2.1.3-green)

* `Jupyter Notebook`
* `Git and GitHub`

## 7. Agradecimientos 🤝

Quiero agradecer a Oracle y Alura LATAM por proporcionar las bases y el material necesarios para la realización de este proyecto, y por su alianza que hace posible este programa de capacitación para el desarrollo del futuro en tecnología.

![Alura LATAM](https://github.com/user-attachments/assets/92a155ab-bcbb-41c6-8bbc-a0e8f552eb0f) ![Oracle](https://github.com/user-attachments/assets/f399257d-d637-44be-809e-4bac2232fe25)

![ONE](https://github.com/user-attachments/assets/368ff23a-e3f2-4f08-a987-0f736996779c)

## 8. Desarrollador del proyecto 👷

![imagen-readme](https://github.com/user-attachments/assets/133bc743-0424-4120-a7a6-7245d2f28f8c)

**| Ignacio Majo | Data Scientist Junior |**

📫 Contacto: ignacio.majoo@gmail.com | 💻[LinkedIn](https://www.linkedin.com/in/ignacio-majo/)

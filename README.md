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
Esta reducción resultó en un conjunto de datos con **3952 observaciones**.

Sin embargo, para la simulación del pipeline en entorno productivo, se generaron datos artificiales utilizando la técnica `SMOTENC`, ya que el objetivo de esto era demostrar el uso y capacidades del modelo, lo cual no se ve afectado por la utilización de datos creados de manera artificial.


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

|Model	             |Accuracy	|Precision	|Recall	|F1-score|
|---------------------|----------|-----------|--------|--------|
|RandomForest 1	    |0.7131	   |0.7056	   |0.7292	|0.7172  |
|LogisticRegression 4 |0.6715	   |0.6565	   |0.7167	|0.6853  |
|KNN 1	             |0.6653	   |0.6416	   |0.7458	|0.6898  |
|XGB Classifier 3	    |0.7048	   |0.7059	   |0.7000	|0.7029  |
|SVM 3       	       |0.6778	   |0.6481	   |0.7750	|0.7059  |

Estos, fueron guardados y cargados como `Best {familia algoritmo}`, y que luego fueron evaluados en los datos de prueba *(datos no vistos por los modelos durante el entrenamiento)*:

|Model	                    |Accuracy	|Precision |Recall	|F1-score |
|----------------------------|---------|----------|---------|---------|
|Best Random Forest	        |0.6566	|0.6761	  |0.6010	|0.6364   |
|Best Logistic Regression	  |0.6692	|0.6618	  |0.6919	|0.6765   |
|Best K-Nearest Neighbors	  |0.6490	|0.6335	  |0.7071	|0.6683   |
|Best XGBoost Classifier	  |0.6389	|0.6536	  |0.5909	|0.6207   |
|Best Support Vector Machine |0.6439	|0.6234    |0.7273	|0.6713   |

Al evaluar las métricas obtenidas, se seleccionó el modelo `Best Logistic Regression` como **Champion Model** para implementación en entorno productivo, debido a su capacidad de generalización e interpretabilidad de coeficientes y, especialmente, por su alto Recall con baja variación, priorizando la detección de clientes que abandonan (objetivo de negocio), sin penalizar fuertemente la Precisión.

Como puede verse en las tablas a continuación:

|Model	                     |Recall Validation| Recall Testing |Variación|
|----------------------------|-----------------|----------------|---------|
|Best Random Forest	        |0.7292           |0.6010          |-12.82%  |
|Best Logistic Regression    |0.7167	        |0.6919          |-2.48%   |
|Best K-Nearest Neighbors    |0.7458           |0.7071	       |-3.87%   |
|Best XGBoost Classifier     |0.7000           |0.5909          |-10.91%  |
|Best Support Vector Machine |0.7750		     |0.7273	       |-4.47%   |

|Model                       |F1-score Validation| F1-score Testing|Variación|
|----------------------------|-------------------|-----------------|---------|
|Best Random Forest          |0.7172             | 0.6364          |-8.08%   |
|Best Logistic Regression    |0.6853             | 0.6765          |-0.88%   |
|Best K-Nearest Neighbors    |0.6898             | 0.6683          |-2.15%   |
|Best XGBoost Classifier     |0.7029             | 0.6207          |-8.22%   |
|Best Support Vector Machine |0.7059     	       | 0.6713          |-3.46%   |


El modelo `Best Logistic Regression` es el que sufre menos variaciones en sus métricas, demostrando robustez y buena capacidad de generalización frente a datos nuevos.
A partir de este modelo se identificaron las variables más influyentes en la evasión (tanto protectoras como factores de riesgo) son:

<img width="2963" height="1763" alt="Coeficiente_variables_LogReg_best_coef" src="https://github.com/user-attachments/assets/d6ed9be9-6099-4dad-9ef1-385274af71f7" />
<br>
A partir de las cuales se llevó a cabo el siguiente análisis de impacto:

<img width="3570" height="1768" alt="tabla_coef_logreg" src="https://github.com/user-attachments/assets/422990ad-2f5f-4971-95bf-a8a0ec0a2e77" />

### Pipeline de prueba

Finalmente, se desarrolló la simulación de un pipeline para la implementación del modelo en entorno productivo, utilizando datos sintéticos generados con la técnica `SMOTENC`.
El mismo, recibe un archivo JSON (formato original de la base de datos) con datos crudos (sin ninguna transformación) para producir predicciones.
Cuenta con dos modos de utilización:
* `mode='production'`: que devuelve un archivo JSON con `CustomerID`, `Probabilidad Churn` y `Churn` *(Etiqueta: si Probabilidad Churn > 0.5, Churn = 1, si Probabilidad Churn <= 0.5, Churn = 0)*
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

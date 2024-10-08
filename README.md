# Universidad ICESI  
# **Parcial 2 de Fundamentos de Analitica**

## Integrantes:
- Álvaro Rodríguez  
- Alfredo Aponte  

Octubre de 2024


En el contexto del desafío de Kaggle, estamos abordando la maximización de la métrica ROC_AUC como criterio de evaluación clave. Para ello, hemos implementado y evaluado una variedad de algoritmos de clasificación sobre un conjunto de datos común, utilizando técnicas robustas de preprocesamiento, validación cruzada y optimización de hiperparámetros. El flujo de trabajo incluye la generación de archivos de predicción ("submission") para Kaggle, lo que permite evaluar el desempeño final en un conjunto de datos que el modelo nunca ha visto.



En el [Analisis Exploratorio de datos](/01_EDA/01_Compresion%20y%20analisis%20de%20los%20datos.ipynb), identificamos que el conjunto de datos presenta varios problemas importantes que deben abordarse antes de avanzar hacia la creación de modelos predictivos. Entre los principales desafíos encontrados, destacamos la presencia de valores nulos reales, categorías mal etiquetadas (como variables booleanas clasificadas incorrectamente con un valor de "2"), variables con un alto porcentaje de valores faltantes y la existencia de datos atípicos (outliers).

Estos problemas de calidad de datos fueron corregidos de manera cuidadosa, implemententando estrategias adecuadas en las etapas de preprocesamiento. Para ello, usamos de pipelines y transformadores (transformers) que automaticen la limpieza y transformación de los datos, asegurando que cualquier valor nulo o erróneo sea tratado adecuadamente y que los outliers se manejen de manera que no distorsionen los resultados del modelo. Esto garantizará que el proceso de modelado sea más robusto y eficiente, minimizando el riesgo de sesgos o errores en las predicciones.


**Algoritmos Evaluados:**

Los modelos que hemos entrenado y evaluado incluyen:

- [Support Vector Classifier](/02_SVC/02_SVC.ipynb), al aplicarlo manualmente, surgieron dificultades al intentar ajustar sus hiperparámetros debido al tamaño considerable del conjunto de datos de entrenamiento. Para superar este inconveniente, se decidió trabajar con el 10% del dataset y utilizar las variables recomendadas por una médica experta. Esta estrategia permitió mejorar la velocidad del proceso de optimización de hiperparámetros, logrando identificar los mejores parámetros de forma más eficiente.

    Sin embargo, esta reducción del conjunto de datos impactó negativamente en los resultados del modelo, obteniendo un valor de ROC AUC de 0.61, lo cual está por debajo de lo esperado. Dado este rendimiento subóptimo, se tomó la decisión de no considerar este modelo en los envíos finales de Kaggle, ya que sus resultados no cumplen con los estándares requeridos.

- [Support Vector Classifier Linear de Pycaret](/03_SVC_linear_pycaret/), al utilizar Pycaret, el modelo se ajustó y optimizó automáticamente empleando la totalidad del conjunto de datos de entrenamiento. Después de varias horas de procesamiento, el resultado obtenido fue un valor de ROC AUC de 0.50, un desempeño claramente insuficiente. Por este motivo, se decidió no considerar este modelo en los envíos de Kaggle debido a sus bajos resultados.

    Adicionalmente, se intentó ajustar un modelo SVC con kernel radial también utilizando PyCaret. Sin embargo, el proceso de ajuste nunca llegó a completarse, lo que impidió obtener resultados concluyentes con este algoritmo.

    Como conclusión, se pudo confirmar que el autotuning de PyCaret no es una opción adecuada para este tipo de modelos en datasets grandes y complejos. En su lugar, se recomienda realizar un ajuste manual de la arquitectura para obtener mejores resultados en términos de rendimiento y eficiencia.

- [MLP](/05_MLP/05_MLP.ipynb), , al aplicarlo manualmente, se presentaron dificultades para ajustar sus hiperparámetros debido al tamaño considerable del conjunto de datos de entrenamiento. Para mitigar este problema, se optó por trabajar con el 10% del dataset y utilizar las variables sugeridas por una médica experta. Esta estrategia permitió una mayor velocidad en la búsqueda de los mejores hiperparámetros.

    Sin embargo, la reducción del conjunto de datos tuvo un impacto negativo en el rendimiento del modelo, obteniendo un valor de ROC AUC de 0.61, un resultado por debajo de las expectativas. Por lo tanto, se tomó la decisión de no considerar este modelo en los envíos finales de Kaggle, debido a su bajo rendimiento.

- [MLP desde Pycaret](/06_MLP_pycaret/06_MLP_pycaret.ipynb), El modelo MLP también fue ajustado y optimizado automáticamente utilizando PyCaret con la totalidad del conjunto de datos de entrenamiento. Después de varias horas de procesamiento, el resultado fue un valor de ROC AUC de 0.50, lo cual se consideró insuficiente. Debido a este rendimiento, se decidió no incluir este modelo en los envíos a Kaggle.

    Como conclusión adicional, se puede afirmar que el autotuning de PyCaret no es una estrategia adecuada para este tipo de modelos en datasets grandes y complejos. Por lo tanto, se recomienda optar por una construcción manual de la arquitectura del modelo para obtener un mejor rendimiento y resultados más satisfactorios.

- [Ramdom Forest](/07_RF/07_RF_Pycaret.ipynb), dado que los resultados obtenidos con los modelos SVC y MLP fueron insatisfactorios y demandaron largos tiempos de procesamiento, se decidió explorar otros modelos para mejorar el rendimiento en términos de ROC AUC. Utilizando PyCaret, se ajustó y optimizó automáticamente un nuevo modelo con la totalidad del conjunto de datos de entrenamiento. En tan solo unos minutos de procesamiento, se logró un valor de ROC AUC de 0.82, un resultado significativamente mejor que los anteriores.

    Este modelo mostró un desempeño mucho más prometedor y, por lo tanto, se decidió incluirlo en los envíos a Kaggle debido a sus buenos resultados.

    Como conclusión adicional, se pudo confirmar que el autotuning de PyCaret es una opción eficiente y efectiva para este tipo de modelos, especialmente cuando se requiere optimización en datasets grandes, logrando buenos resultados en un tiempo relativamente corto.

- [Extra tree clasifier con Pycaret](/08_et/08_ET_Pycaret.ipynb), ddo que los resultados obtenidos con los modelos SVC y MLP fueron deficientes y demandaron un tiempo considerable de procesamiento, se decidió explorar otros modelos para mejorar el desempeño en términos de ROC AUC. Utilizando PyCaret, se ajustó y optimizó automáticamente un nuevo modelo con la totalidad del conjunto de datos de entrenamiento. En solo unos minutos de procesamiento, se alcanzó un valor de ROC AUC de 0.81, un resultado mucho más favorable que los obtenidos previamente.

    Este modelo mostró un rendimiento satisfactorio, por lo que fue seleccionado para ser considerado en los envíos de Kaggle debido a sus buenos resultados.

    Como conclusión adicional, se puede confirmar que el autotuning de PyCaret es una opción viable y eficiente para este tipo de modelos, especialmente cuando se busca optimizar rápidamente en datasets grandes y mejorar los resultados de forma significativa.

- [XGBoost](/09_XG/09_XG_Pycaret.ipynb), dado que los resultados de SVC y MLP fueron pobres y demorados, exploramos con otros modeles diferentes para poder obtener mejores ROC_AUC.  Se ajusta y tunea el modelo en referencia, automáticamente con Pycaret con todo el dataset de entrenamiento y después tan solo unos minutos de procesamiento, el resultado es un roc_auc es de 0.81.  

    Este modelo sí será tenido en cuenta en los submissions de kaggle por sus buenos resultados.  Como conclusión adicional, se puede confirmar que el autotuneo de Pycaret sí  es una buena opción para este tipo de modelos.

- [Red Neuronal](/Red%20Neuronal.ipynb), se entrenó una red neuronal con el objetivo de optimizar sus hiperparámetros utilizando un enfoque de optimización bayesiana. No obstante, debido al alto consumo de tiempo, no fue factible aplicar este proceso a todo el conjunto de datos. Para superar esta limitación, se trabajó con un subconjunto del dataset original, lo que permitió ejecutar el algoritmo de manera más eficiente.

    Como resultado, se obtuvo un valor de ROC AUC de 0.73, lo cual representa un rendimiento razonable dadas las restricciones impuestas por el tiempo y los recursos disponibles.

Modelo|	ROC_AUC
------|-------------------------------------
|SVC (manual)|	0.61|
|SVC_linear_Pycaret|	0.50|
|SVC_radial_Pycaret|	No corre|
|MLP (manual)|	0.61|
|RF_Pycaret (random forest)|	0.82|
|ET_Pycaret (Extra tree clasifier)|	0.81|
|XG_Pycaret (XG Boost) |	0.81|
|Red Neuronal |	0.73|

## **Conclusiones**

- Fue necesario fragmentar el conjunto de datos de entrenamiento para poder ejecutar los modelos SVC y MLP utilizando Sklearn, debido a las limitaciones en términos de tiempo de procesamiento y memoria que estos modelos presentan al trabajar con datasets grandes.

- Los modelos de clasificación basados en árboles de decisión resultaron ser significativamente más efectivos tanto en términos de tiempo de procesamiento como en la métrica de ROC AUC, superando el desempeño de los modelos SVC y MLP. Estos modelos demostraron ser una opción más eficiente y efectiva para este caso particular.

- Modelos mas robustos, no nos generaron un mejor ROC, modelos mas basicos generaron mejores resultados.

- Un punto a tener en cuenta, que nos vamos a encontrar en el futuro es la cantidad de datos, en este caso teniamos casi 28.000 muestras o registros y todos los modelos fueron lentos al momento de correr, analizando el caso pensabamos, de "que hubiera ocurrido si el set de datos tuviera 1.000.000 de registros?", el enfoque inicial hubiera estado en optimizar la seleccion de registros. Utilizar mecanismos como mini-batch learning, nos permitirían haces esta seleccion y desde seguir a los pasos siguientes del pipeline.


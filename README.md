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

- [Support Vector Clasifier](/SVC.ipynb), al aplicarlo manualmente, surgieron dificultades al intentar ajustar sus hiperparámetros debido al tamaño considerable del conjunto de datos de entrenamiento. Para superar este inconveniente, se decidió trabajar con el 10% del dataset y utilizar las variables recomendadas por una médica experta. Esta estrategia permitió mejorar la velocidad del proceso de optimización de hiperparámetros, logrando identificar los mejores parámetros de forma más eficiente.

Sin embargo, esta reducción del conjunto de datos impactó negativamente en los resultados del modelo, obteniendo un valor de ROC AUC de 0.61, lo cual está por debajo de lo esperado. Dado este rendimiento subóptimo, se tomó la decisión de no considerar este modelo en los envíos finales de Kaggle, ya que sus resultados no cumplen con los estándares requeridos.

- [Support Vector Clasiffier Linear de Pycaret](/03_SVC_linear_pycaret/), al utilizar Pycaret, el modelo se ajustó y optimizó automáticamente empleando la totalidad del conjunto de datos de entrenamiento. Después de varias horas de procesamiento, el resultado obtenido fue un valor de ROC AUC de 0.50, un desempeño claramente insuficiente. Por este motivo, se decidió no considerar este modelo en los envíos de Kaggle debido a sus bajos resultados.

Adicionalmente, se intentó ajustar un modelo SVC con kernel radial también utilizando PyCaret. Sin embargo, el proceso de ajuste nunca llegó a completarse, lo que impidió obtener resultados concluyentes con este algoritmo.

Como conclusión, se pudo confirmar que el autotuning de PyCaret no es una opción adecuada para este tipo de modelos en datasets grandes y complejos. En su lugar, se recomienda realizar un ajuste manual de la arquitectura para obtener mejores resultados en términos de rendimiento y eficiencia.

- [MLP](/05_tutoria-1-af-ii-2024-ii-svc.ipynb)
- [MLP desde Pycaret](/06_MLP_pycaret/06_MLP_pycaret.ipynb)
- [Ramdom Forest](/07_RF/07_RF_Pycaret.ipynb)
- [ET](/08_et/08_ET_Pycaret.ipynb)
- [XGBoost](/09_XG/09_XG_Pycaret.ipynb)
- [LG](/10_LG/10_LG_Pycaret.ipynb)
- [Red Neuronal](/Red%20Neuronal.ipynb)


## ** Conclusiones**



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

- [Support Vector Clasifier](/SVC.ipynb)
- [Support Vector Clasiffier Linear de Pycaret](/03_SVC_linear_pycaret/)
- [MLP](/05_tutoria-1-af-ii-2024-ii-svc.ipynb)
- [MLP desde Pycaret](/06_MLP_pycaret/06_MLP_pycaret.ipynb)
- [Ramdom Forest](/07_RF/07_RF_Pycaret.ipynb)
- [ET](/08_et/08_ET_Pycaret.ipynb)
- [XGBoost](/09_XG/09_XG_Pycaret.ipynb)
- [LG](/10_LG/10_LG_Pycaret.ipynb)
- [Red Neuronal](/Red%20Neuronal.ipynb)


## ** Conclusiones**



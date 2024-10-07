# Universidad ICESI  
# **Parcial 2 de Fundamentos de Analitica**

## Integrantes:
- Álvaro Rodríguez  
- Alfredo Aponte  

Octubre de 2024


En el contexto del desafío de Kaggle, estamos abordando la maximización de la métrica ROC_AUC como criterio de evaluación clave. Para ello, hemos implementado y evaluado una variedad de algoritmos de clasificación sobre un conjunto de datos común, utilizando técnicas robustas de preprocesamiento, validación cruzada y optimización de hiperparámetros. El flujo de trabajo incluye la generación de archivos de predicción ("submission") para Kaggle, lo que permite evaluar el desempeño final en un conjunto de datos que el modelo nunca ha visto.


Los datos recibidos han pasado por un proceso de revisión para identificar características que permitan conocer la relevancia, distribución y composición que se puede validar en el [Analisis Exploratorio de datos](/01_EDA/01_Compresion%20y%20analisis%20de%20los%20datos.ipynb)


**Algoritmos Evaluados:**

Los modelos que hemos entrenado y evaluado incluyen:

- [Support Vector Clasifier](/SVC.ipynb)
- [Support Vector Clasiffier Linear de Pycaret](/03_SVC_linear_pycaret/)
- [MLP](/05_tutoria-1-af-ii-2024-ii-svc.ipynb)
- [MLP desde Pycaret](/06_MLP_pycaret/06_MLP_pycaret.ipynb)
- [Ramdom Forest](/07_RF/07_RF_Pycaret.ipynb)
- [ET](/08_et/08_ET_Pycaret.ipynb)
- [XGBoost](/09_XG/09_XG_Pycaret.ipynb)
- [Red Neuronal](/Red%20Neuronal.ipynb)


## ** Conclusiones**

01_EDA:  encontramos un dataset con varios problemas, principalmente temas de datos nulos reales y de categorías falsas (variables boleanas, clasificadas con “2), variables muy nulas y datos atípicos.  Este tipo de problemas deberán ser ajustados al momento de crear los modelos predictivos a través de pipelines y transformers.

02_SVC:  al aplicar este modelo manualmente, nos encontramos con la dificultad en tunear sus hiperparámetros, dada la magnitud del dataset de entrenamiento.  Para solucionar el inconveniente anterior, se trabajó con el 10% del dataset de entramiento y con variables recomendadas por una médica experta, logrando gran velocidad al encontrar los mejores hiperparámetros, pero impactando negativamente el resultado del ROC AUC, llegando a un valor de 0.61.  Este modelo no será tenido en cuenta en los submissions de kaggle por sus bajos resultados

03_SVC_linear_pycaret:  se ajusta y tunea el modelo automáticamente con Pycaret con todo el dataset de entrenamiento y después de unas horas de procesamiento, el resultado es un roc_auc es de 0.50.  Este modelo no será tenido en cuenta en los submissions de kaggle por sus bajos resultados.  Adicionalmente, se prueba en Pycaret un modelo tuneado SVC con kernel radial, pero el algoritmo NUNCA termina su ejecución.  Como conclusión adicional, se puede confirmar que el autotuneo de pycaret no es una buena opción para este tipo de modelos y es mejor construir su arquitectura manualmente.

05_MLP:  al aplicar este modelo manualmente, nos encontramos con la dificultad en tunear sus hiperparámetros, dada la magnitud del dataset de entrenamiento.  Para solucionar el inconveniente anterior, se trabajó con el 10% del dataset de entramiento y con variables recomendadas por una médica experta, logrando gran velocidad al encontrar los mejores hiperparámetros, pero impactando negativamente el resultado del ROC AUC, llegando a un valor de 0.61.  Este modelo no será tenido en cuenta en los submissions de kaggle por sus bajos resultados.

06_MLP_pycaret:  se ajusta y tunea el modelo automáticamente con Pycaret con todo el dataset de entrenamiento y después de unas horas de procesamiento, el resultado es un roc_auc es de 0.50.  Este modelo no será tenido en cuenta en los submissions de kaggle por sus bajos resultados.  Como conclusión adicional, se puede confirmar que el autotuneo de Pycaret no es una buena opción para este tipo de modelos y es mejor construir su arquitectura manualmente.

07_RF (Random Forest): dado que los resultados de SVC y MLP fueron pobres y demorados, exploramos con otros modeles diferentes para poder obtener mejores ROC_AUC.  Se ajusta y tunea el modelo en referencia, automáticamente con Pycaret con todo el dataset de entrenamiento y después tan solo unos minutos de procesamiento, el resultado es un roc_auc es de 0.82.  Este modelo sí será tenido en cuenta en los submissions de kaggle por sus buenos resultados.  Como conclusión adicional, se puede confirmar que el autotuneo de Pycaret sí  es una buena opción para este tipo de modelos.

08_ET (Extra tree clasifier): dado que los resultados de SVC y MLP fueron pobres y demorados, exploramos con otros modeles diferentes para poder obtener mejores ROC_AUC.  Se ajusta y tunea el modelo en referencia, automáticamente con Pycaret con todo el dataset de entrenamiento y después tan solo unos minutos de procesamiento, el resultado es un roc_auc es de 0.81.  Este modelo sí será tenido en cuenta en los submissions de kaggle por sus buenos resultados.  Como conclusión adicional, se puede confirmar que el autotuneo de Pycaret sí  es una buena opción para este tipo de modelos.

09_XG (XG Boost clasifier): dado que los resultados de SVC y MLP fueron pobres y demorados, exploramos con otros modeles diferentes para poder obtener mejores ROC_AUC.  Se ajusta y tunea el modelo en referencia, automáticamente con Pycaret con todo el dataset de entrenamiento y después tan solo unos minutos de procesamiento, el resultado es un roc_auc es de 0.81.  Este modelo sí será tenido en cuenta en los submissions de kaggle por sus buenos resultados.  Como conclusión adicional, se puede confirmar que el autotuneo de Pycaret sí  es una buena opción para este tipo de modelos.

Modelo	ROC_AUC
02_SVC (manual)	0.61
03_SVC_linear_Pycaret	0.50
04_SVC_radial_Pycaret	No corre
05_MLP (manual)	0.61
07_RF_Pycaret (random forest)	0.82
08_ET_Pycaret (Extra tree clasifier)	0.81
09_XG_Pycaret (XG Boost)	0.81
Red Neuronal	

Conclusiones finales.

•	Es necesario fragmentar el dataset de entrenamiento para poder correr modelos SVC y MLP con Sklearn.
•	Los modelos de clasificación basados en árboles de decisión fueron más efectivos en tiempo y ROC_AUC que SVC y MLP.




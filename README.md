# Chihuahua_or_Muffin
¿Es un Chihuahua o es un Muffin?
### Python AI image identification
#### Marco Antonio Camalich Pérez
## Descripción del Proyecto
El posterior repositorio contiene el desarrollo de un sistema de inteligencia artificial desarrollado en Python mediante la lógica de una red neuronal convolucional para identificar y clasificar diferentes tipos de fotografías de chihuahuas y muffins. El presente programa aplicará el aprendizaje automático preprocesado de una variedad de imágenes de entrenamiento validadas con un subset específico para hacer la posterior identificación de las imágenes de prueba.
## Selección del data set
#### Cortinhas, S. (2022). Muffin vs chihuahua. Kaggle.com. https://www.kaggle.com/datasets/samuelcortinhas/muffin-vs-chihuahua-image-classification/data
El dataset utilizado en este proyecto fue obtenido de kaggle.com. Posee 5.917 fotografías en formato .jpg divididas en tres subcarpetas: "prediction", "test" y "training". Estas fotografías pertenecen a una de dos diferentes subclases:
{'chihuahua','muffin'}
‌
Hay alrededor de 4733 imágenes en training, 638 en test y 546 en prediction (80/20 de proporción, solamente considerando training y test; excelentes valores porcentuales para garantizar un entrenamiento suficiente para aprender patrones). Este dataset aprenderá las fotografías previamente procesadas mediante una red neuronal convolucional para reconocerlas y clasificarlas en su debido subtipo. La totalidad de las imágenes, incluyendo algunas de las preprocesadas mediante aumentación de los datos, se encuentran en el presente repositorio.
## Preprocesado de los datos
Se realizó un algoritmo de aumentación de los datos sobre el grupo de testing de fotografías para mejorar la capacidad de generalización del modelo a crear. Esto se realiza al exponerlo a diferentes variaciones de los datos durante el entrenamiento aumentando la diversidad de los datos. Algunas de las técnicas implementadas incluyen el reescalamiento de los píxeles, la rotación aleatorio de las imágenes, desplazamientos horizontales y verticales aleatorios, zoom, cambio en el ángulo de la fotografía, entre otros. Se realiza la impresión y el guardado de las imágenes generadas, lo que es fundamental para el entrenamiento eficiente de modelos de aprendizaje computacionales. Este procesamiento se encuentra sólido para futuros pasos, ya que se redujo la probabiblidad de memorización del modelo.
## Implementación de Modelo
### Elección de modelo: VGG16
#### Wu, Xinyi, et al. "A comprehensive survey on VGG-based networks." arXiv preprint arXiv:2003.11338 (2020). https://arxiv.org/abs/2003.11338
#### Dong, X., Lin, S., Cheng, G., Zhao, Y., Yang, L., & Zhang, X. (2021). Revisiting residual networks for image classification: A comprehensive study. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. https://arxiv.org/abs/2103.12793
Habiendo realizado el preprocesado pertinente de los datos, se determinó que el modelo VGG16 es una red neuronal convolucional profunda que ha demostrado un rendimiento sobresaliente en tareas de clasificación de imágenes, por lo que se convirtió en una opción idónea para el modelado del proyecto. La elección del modelo se basa en su capacidad para aprender características complejas de grupos distintos de imágenes, y ha demostrado ser altamente eficiente en una amplia variedad de tareas de visión por computadora, lo que la convierte en una elección sólida para este identificador.
A diferencia del modelo ResNet-50 escogido inicialmente, VGG16 no utiliza bloques residuales. En su lugar, su efectividad se basa en la repetición de bloques convolucionales y agrupaciones maxpool. Estas capas convolucionales actúan como filtros que se deslizan sobre la imagen, analizando pequeñas secciones de la misma. Mientras más desplazan, las capas detectan patrones y características específicas del grupo de fotos, permitiendo al modelo comprender la estructura y el contenido de cada imagen individual. Las agrupaciones maxpool se encargan de reducir la dimensión espacial de la información, manteniendo las características más importantes de las imágenes. Esto permite al modelo procesar datos de manera eficiente y evitar la sobrecarga de la computadora.

En el VGG16 del presente repositorio, se utiliza un generador de datos para cargar las imágenes de entrenamiento y prueba desde los directorios correspondientes, con un tamaño de imagen de 224x224 píxeles y un tamaño de lote de 8 imágenes. La red neuronal se carga con los pesos preentrenados anteriormente de ImageNet, que es conjunto de datos de imágenes ampliamente utilizado en la investigación de visión por computadora. Ergo, esto significa que el modelo aprovecha el conocimiento previo adquirido al ser entrenado mediante un conjunto de imágenes generales masivo. Luego, se agregan capas adicionales al modelo para adaptarlo específicamente a la tarea de identificar y clasificar las fotos a su respectiva clasificación de imagen. Es importante rescatar que el usar 5 épocas hacía que el modelo perdiera precisión ya que sobreajustaban los valores de entrenamiento
## Generación del modelo
![image](https://github.com/CamalichM/chihuaha_or_muffin/assets/99758150/d8bf63b6-5c95-458f-b199-33be7f6adffa)
![image](https://github.com/CamalichM/chihuaha_or_muffin/assets/99758150/78995563-82bd-48d9-ba2e-bb642b9b6f0e)
#### Gráficas de precisión del modelo
![image](https://github.com/CamalichM/chihuaha_or_muffin/assets/99758150/5f963f53-1b42-40f0-8c1d-f918e3cb4207)
![image](https://github.com/CamalichM/chihuaha_or_muffin/assets/99758150/0f5ff365-4447-4790-97ce-9c1fd794edc9)
#### Gráficas de pérdida del modelo
La primera iteración del modelo tuvo un total de 5 épocas que llevaron la exactitud del modelo a 0.96 en una escala de 0 a 1, mientras que el loss tuvo un comportamiento de decremento exponencial contrario al aumento de la exactitud del modelo con un valor de 0.1232. Esto significa que el modelo fue mejorando gradualmente en su capacidad para hacer predicciones precisas, siendo capaz de clasificar correctamente aproximadamente el 97.65% de las imágenes de prueba. Al generar el contraste con las imágenes de prueba, se observó que el accuracy del modelo es de 0.978 con un loss de 0.0941, por lo que es un modelo casi perfecto para predecir fotografías en estas dos categorías.
El graficado de los resultados es sustentado por el escrito: 
#### He, K., Zhang, X., Ren, S., & Sun, J. (2015). Deep residual learning for image recognition. In Proceedings of the IEEE conference on computer vision and pattern recognition (pp. 770-778). Enlace: https://arxiv.org/abs/1512.03385
El paper determina el uso de gráficas de puntos para visualizar el error de entrenamiento y validación durante el entrenamiento de la red ResNet como un acercamiento adecuado y visualmente atractivo para una posterior toma de decisiones.

![image](https://github.com/CamalichM/chihuaha_or_muffin/assets/99758150/1efefa9c-8063-4fda-9ee8-84ca847bda11)
#### Matriz de Confusión
![image](https://github.com/CamalichM/chihuaha_or_muffin/assets/99758150/3da1cfa0-1762-4406-977d-ae45e424fd79)
#### Variables de desempeño
La matriz de confusión es una tabla que muestra la cantidad de predicciones correctas e incorrectas desglosadas por cada clase. Por su parte, las variables son métricas cruciales para evaluar el rendimiento de un modelo de clasificación, especialmente en contextos donde no solo es importante la cantidad de aciertos, sino también la calidad de los casos positivos. Estos datos permiten entender no solo la precisión general del modelo, sino también el tipo de errores que está cometiendo. La validez de estas métricas se encuentra en el siguiente escrito, el cual presenta ejemplos detallados y explicaciones claras para ayudar a los lectores a comprender e interpretar la matriz de confusión y las variables de desempeño de manera efectiva: 
#### "Confusion Matrix Analysis: A Practical Guide for Machine Learning Classification Problems" por Singh, A., & Thakur, M. (2022). International Journal of Advanced Computer Science and Applications, 13(1), 1-10. https://joecsa.coecsa.org/index.php/joecsa/about
## Correcciones realizadas con respecto a la primera iteración
- Reducción de 10 a 5 epochs para limitar el sobreajuste.
- Adición de matriz de confusión y variables de desempeño para observar la eficiencia del modelo.
- Cambio de modelo de ResNet50 a VGG16 basado en el paper previamente referenciado.
- Adición de callbacks para realizar ajustes paulatinos al modelo.
- Adición de validation data para efectuar un entrenamiento más específico.
##### Estos cambios se encuentran documentados, de igual manera en el código del proyecto.

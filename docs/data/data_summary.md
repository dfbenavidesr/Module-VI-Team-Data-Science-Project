# Data Report

La información utilizada en el proceso de afinamiento del modelo está basada en un conjunto de mensajes SMS con los cuales se reentrena la última capa del modelo preentrenado

## General summary of the data

El conjunto de datos está compuesto por 5572 mensajes SMS y sus correspondientes etiquetas, tal como se muestra en el script donde se realiza el EDA

## Data quality summary

Se revisa la data y no se tienen datos faltantes ni nulos; es decir, para cada texto se tiene su correspondiente etiqueta y visceversa. 

## Target variable

El modelo busca predecir con base  en la aplicación de fine-tuning de un modelo preentrenado para clasificación de sentimientos a cual de las  dos etiquetas **(Ham o Spam)** corresponde el texto que se somete a prueba. 

## Individual variables
**Ham**: son definidos de esta manera los mensajes que realmente tienen información de interés para la persona que los recibe. 

**Spam**:  Son aquellos mensajes no deseados; mensajes cuya envío es realizado sin autorización de la persona que los recibe. 

## Variable ranking

Desde el modelo no existe una clasificación de variables debido a su caracter binario; la importancia de las dos es la misma en la medida que estas son excluyentes.Es decir, si obtengo una por residuo tengo la otra. 

## Relationship between explanatory variables and target variable

Existe una relación directa entre el texto del mensaje como variable explicatoria y su etiqueta como variable explicativa. Tras del modelo hay una serie de capas de redes neuronales  que lo que hacen es aprender de la estructura de los tensores de cada uno de los textos para arrojar el resultado en el modelo de clasificación de spam. 


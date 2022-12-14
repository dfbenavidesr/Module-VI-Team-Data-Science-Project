# Exit Report of Project <X> for Customer <Y>

Instructions: Template for exit criteria for data science projects. This is concise document that includes an overview of the entire project, including details of each stage and learning. If a section isn't applicable (e.g. project didn't include a ML model), simply mark that section as "Not applicable". Suggested length between 5-20 pages. Code should mostly be within code repository (not in this document).

Customer: <Enter Customer Name\>

Team Members: <Enter team member' names. Please also enter relevant parties names, such as team lead, Account team, Business stakeholders, etc.\>

##	Overview

<Executive summary of entire solution, brief non-technical overview\>

##	Business Domain
<Industry, business domain of customer\>

Sector tecnológico

##	Business Problem
<Business problem and exact use case(s), why it matters\>

La detección  de spam es un importante servicio que puede beneficiar a muchas compañias, ya que los correos masivos terminan consumiendo recursos computacionales y esto se traduce en recursos. Por otro lado, el que los mismos lleguen a consumidores finales genera perdida de tiempo y molestias por los mismos. 

##	Data Processing
<Schema of original datasets, how data was processed, final input data schema for model\>

La data con la cual se realiza el entrenamiento del modelo se descarga de Kaggle y se aloja de forma local en este repositorio

##	Modeling, Validation
<Modeling techniques used, validation results, details of how validation conducted\>



El objeto del presente proyecto es poner en producción las técnicas de Deep Learning exploradas en el presente módulo.  Es por esto  que se plantea la utilización de un modelo de _**fill mask**_ de la librería **_transformers_** a partir del cual aplicando **_Fine Tuning_** y que de ello pueda derivar en ujn modelo de clasificador de spam. 


Es así como se hace el ejercicio de fine-tuning del modelo preentrenado de transformers  [_'distilbert-base-uncased'_](https://huggingface.co/distilbert-base-uncased?text=Paris+is+the+%5BMASK%5D+of+France.). Este modelo inicialmente fue entrenado para labores de _fill mask_ y se adaptará  como modelo clasificación  de **SMS** no  deseado. 

### Preprocesamiento
	
importamos pandas, por medio del cual hacemos el respectivo cargue del dataset, delimitamos por el espacio la  etiqueta del mensaje. Luego por medio de la función _list_ convertimos el mensaje y las etiquetas en un par de listas. luego convertimos las etiquetas en una variable dummie, debido a que tenemos una salida binaria  _(el mensaje es spam o no lo es)_
	
Luego importamos la función *train_test_split*  del módulo *model_selection* de la librería *scikit-learn*  y por medio de este dividimos  en set de entrenamiento y prueba. Definimos el tamaño de set de prueba en 20% de la muestra. También definimos el parámetro *random_state* para efectos de controlar la generación  de los dos conjuntos de tal manera que  no sean aleatorios. 

	
Ahora debemos invocar los modelos de que vamos a utilizar de la librería transformers  en los siguientes pasos: 

* Llamamos el modelo preentrenado
* Llamamos el tokenizador 

Necesitamos aplicar el tokenizador sobre nuestro conjunto de datos. 

Así que acontinuación llamamos de la librería transformers el tokenizador _"DistilBertTokenizerFast"_ luego lo definimos como nuestro **tokenizer** indicando que el mismo proviene del modelo preentrenado [_'distilbert-base-uncased'_](https://huggingface.co/distilbert-base-uncased?text=Paris+is+the+%5BMASK%5D+of+France.)
	
	
Luego  aplicamos el tokenizador que acabamos de definir sobre nuestro conjunto  de mensajes de entrenamiento y prueba. Como los SMS no tienen la misma longitud (cantidad de tokens) debemos definir los parámetros truncation y padding como True para que se obtener oraciones del mismo tamaño; uno se encarga de rellenar de ceros (padding) y el otro de truncar las oraciones más largas. Esto para obtener un conjunto y luego tensores rectangulares. 
	
Ahora se procede a importar Tensorflow para efecto de convertir en tensores los encodings generados en el paso anterior. Acá se junta cada uno a su correspondiente etiqueta.
	
### Entrenamiento
	
A continuación se importan los módulos de TFDistilBertForSequenceClassification que es usado para la tarea de clasificación  de sentimientos. También se importan los módulos  y *TFTrainingArguments* y *TFTrainer*que son los encargados de definir los argumentos  y posteriormente parametrizar el **trainer** del modelo y  hacer las nuevas predicciones. 

Hemos determinado el conjunto de argumentos que serán utilizados en el reentrenamiento del modelo,estos quedan alojados en  el  objeto *training_args*   y  ahora definiremos el modelo refiriendo el modelo preentrenado que vamos a utilizar, que en este caso es  _"distilbert-base-uncased"_. se creará el **trainer** al cual se le pasarán los argumentos antes definidos   y los dos tensores de entrenamiento y prueba; para luego  entrenar el modelo que hemos definido. Una vez instanciado el modelo que será reentrenado, parametrizados los argumentos para ello, se toma la data y se realiza el reentrenamiento del modelo.
	
Ahora solo queda por aplicar modelo que reentrenamos con el dataset de **entrenamiento**, hacer la predicción, y la evaluación de las predicciones. Este procedimiento se encuentra definido en el [manual de fine-tuning](https://huggingface.co/transformers/v3.5.1/training.html) que tiene Hugging Face disponible. 

##	Solution Architecture
<Architecture of the solution, describe clearly whether this was actually implemented or a proposed architecture. Include diagram and relevant details for reproducing similar architecture. Include details of why this architecture was chosen versus other architectures that were considered, if relevant\>
	
La arquitectura del modelo está referenciada el mismo proviene del modelo preentrenado [_'distilbert-base-uncased'_](https://huggingface.co/distilbert-base-uncased?text=Paris+is+the+%5BMASK%5D+of+France.)
	
	
	docs/modeling/Accuray.jpg
	docs/modeling/Accuray.jpg
	
	
![]((https://github.com/dfbenavidesr/Module-VI-Team-Data-Science-Project/blob/fb70f3fc16b5cb36f518b6e9778556b917faa956/docs/modeling/Accuray.jpg))

##	Benefits
	
###	Company Benefit (internal only. Double check if you want to share this with your customer)
<What did our company gain from this engagement? ROI, revenue,  etc\>

###	Customer Benefit
What is the benefit (ROI, savings, productivity gains etc)  for the customer? If just POC, what is estimated ROI? If exact metrics are not available, why does it have impact for the customer?\>

##	Learnings

### 	Project Execution
<Learnings around the customer engagement process\>

### Data science / Engineering
<Learnings related to data science/engineering, tips/tricks, etc\>


### Domain
<Learnings around the business domain, \>

### Product
<Learnings around the products and services utilized in the solution \>

###	What's unique about this project, specific challenges
<Specific issues or setup, unique things, specific challenges that had to be addressed during the engagement and how that was accomplished\>

##	Links
<Links to published case studies, etc.; Link to git repository where all code sits\>

##	Next Steps
 
<Next steps. These should include milestones for follow-ups and who 'owns' this action. E.g. Post- Proof of Concept check-in on status on 12/1/2016 by X, monthly check-in meeting by Y, etc.\>

## Appendix
<Other material that seems relevant – try to keep non-appendix to <20 pages but more details can be included in appendix if needed\>

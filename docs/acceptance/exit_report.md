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
	
Se aplica modelo que reentrenamos con el dataset de **entrenamiento**, hacer la predicción, se evalúan  las predicciones y se encuentra los siguientes resultados  en el dataset de prueba
	
![](https://github.com/dfbenavidesr/Module-VI-Team-Data-Science-Project/blob/fb70f3fc16b5cb36f518b6e9778556b917faa956/docs/modeling/Accuray.jpg)	


##	Solution Architecture
<Architecture of the solution, describe clearly whether this was actually implemented or a proposed architecture. Include diagram and relevant details for reproducing similar architecture. Include details of why this architecture was chosen versus other architectures that were considered, if relevant\>
	
La arquitectura del modelo está referenciada el mismo proviene del modelo preentrenado [_'distilbert-base-uncased'_](https://huggingface.co/distilbert-base-uncased?text=Paris+is+the+%5BMASK%5D+of+France.)
	

##	Customer Benefit
	
What is the benefit (ROI, savings, productivity gains etc)  for the customer? If just POC, what is estimated ROI? If exact metrics are not available, why does it have impact for the customer?\>
	
El beneficio corresponde en la solución a un problema de poder desechar información de manera ahutomática, lo cual supone un ahorro de tiempo en cada uno de los usuarios al no tener que revisar información sin importancia. 

##	Learnings



### Data science / Engineering
<Learnings related to data science/engineering, tips/tricks, etc\>

Este ejercicio  en lo personal ha sido un reto inmenso. Se trata de la implementación de las técnicas enseñadas a lo largo del tercer módulo del [**Diplomado Avanzado de  Machine Learning and Data Science**](https://ingenieria.bogota.unal.edu.co/uec/?p=10947)  de la Facultad de Ingeniería de la Universidad Nacional de Colombia. Las cuales en el momento no he podido interiorizar en su totalidad por la complejidad de las mismas. Sin embargo, estoy convencido que las dominaré y  quedará este repositorio como  muestra  del trabajo realizado y para luego poder evaluar mi avance. 

### Domain
<Learnings around the business domain, \>
	
Se destaca como técnicas adquiridas, la introducción a herramientas como Poetry para el empaquetamiento de los desarrollos, MlFlow como herramienta impostantísima de la gestión de la proyectos de ciencia de datos 


###	What's unique about this project, specific challenges
<Specific issues or setup, unique things, specific challenges that had to be addressed during the engagement and how that was accomplished\>

Los retos asumidos en este proyecto fueron enormes: En lo personal he tenido demasiado interés pero no bastos conocimientos en python y sus diferentes librerías así que constantemente tuve problemas de base. En segundo lugar, no conocía el protocolo Git y no había trabajado en él así que también fue un trabajo arduo. Lo tercero es que no había  tenido cercanía a las herramientas de gestión de proyectos de ciencia de datos y poco adentramiento en el tema del despliegue de modelos. 
	
Aún cuando poseo todas las falencias mencionadas también sé que la manera como se realizaron  las clases por parte de los Docentes son insumo suficiente para poder con tiempo trabajarlas  un tema a la vez y  aprender la técnica como se debe. 
	
##	Links
<Links to published case studies, etc.; Link to git repository where all code sits\>
	
El link donde reposa el modelo que se describe en este documento es: 
	


##	Next Steps
 
<Next steps. These should include milestones for follow-ups and who 'owns' this action. E.g. Post- Proof of Concept check-in on status on 12/1/2016 by X, monthly check-in meeting by Y, etc.\>

## Appendix
<Other material that seems relevant – try to keep non-appendix to <20 pages but more details can be included in appendix if needed\>

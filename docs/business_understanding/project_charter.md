# Project Charter

## Business background

* El desarrollo realizado se encarga de hacer una clasificación de spam, el cual  termina siendo un importante producto que puede beneficiar a muchas compañias, ya que los correos masivos terminan consumiendo recursos computacionales  de los servidores de los consumidores finales. Asi que **El Cliente Final** Es cualquier compañia que se quiera "protegerse" de los correos masivos en cualquier segmento de la industria, esto debido a que el servicio de correo electrónico es ampliamente utilizado.  

## Scope
* Por medio de la aplicación de la técnica de fine-tuning a un modelo preentrenado de  ASR (Automatic Speech Recognition)  se lleva a construir un potente clasificador de spam; es decir, se retira el cabezal y se coloca como salida una clasificación binaria (Spam o no); este cabezal debe ser entrenado con una variada muestra de entrenamiento para que aprenda a realizar la clasificación de los mensajes en Spam o no. 

* La forma de entrega al cliente está por ser desarrollada y hace parte de próxima entregas

## Personnel

En el aún incipiente  mercado laboral colombiano el integrante de este proyecto (**Daniel F. Benavides R.**) será llamado *"Científico de Datos"*: 

A raíz del conocimiento acá compartido se sabe que un proyecto de ciencia de datos tiene: 

* Lider del Proyecto
* Gerente de proyecto
* Arquitecto de Soluciones
* Ingeniero de datos 
* Científico de datos

Todos estos roles deben ser asumidos por el  Integrante del proyecto: **Daniel F. Benavides R.**

## Metrics
* ¿Cuáles son los objetivos cualitativos?
El objetivo es reducir la cantidad de correos no deseados recibidos 
* ¿ Cuál es la métrica cuantificable? 
El objetivo es reducir la proporción  de correos no deseados recibidos
* Cuantificar qué mejora en los valores de las métricas son útiles para el escenario del cliente. 
reducir en un 80% la proporción de correos no deseados recibidos
* ¿Cuál es el valor de referencia (actual) de la métrica? 
El 70% de los correos recibidos son no deseados. 
* ¿Cómo mediremos la métrica?
Se cuentan la cantidad de correos recibidos y de ellos cuales son los deseados y cuales no. A partir de la implementación del modelo se evalúan los dos meses subsiguientes y se comparan con los dos últimos meses evaluados;  En esta comparación se habrá de poder disminuir en un 30% la proporción de correos no deseados. 

## Plan

Una vez se entrene el modelo con una muestra suficientemente  grande acerca de los mensajes que son o no deseados y se despliegue el mismo, se hará corte a  los dos meses y se verificará el rendimiento del mismo. 

## Architecture
### Datos
  * Accederemos a la fuente de datos de los clientes por medio de las respectivas Querys de sus archivos locales, esto para obtener los datos de la etapa de entrenamiento. 
 Esta información será llevada al drive del cual será consultada a la hora de hacer el respectivo preprocesamiento y procesamiento de la data. Este se hará desde **Google Colaboratory.**
 


## Communication
* El contacto con el cliente se hara de manera semanal hasta el despliegue del modelo; una vez este se haga, se hará hasta el momento de evaluar resultados, a menos que se evidencie alguna circunstancia que amerite reunión urgente con el cliente. 

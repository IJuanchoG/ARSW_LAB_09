### Escuela Colombiana de Ingeniería
### Arquitecturas de Software - ARSW

## Escalamiento en Azure con Maquinas Virtuales, Sacale Sets y Service Plans

### Dependencias
* Cree una cuenta gratuita dentro de Azure. Para hacerlo puede guiarse de esta [documentación](https://azure.microsoft.com/en-us/free/search/?&ef_id=Cj0KCQiA2ITuBRDkARIsAMK9Q7MuvuTqIfK15LWfaM7bLL_QsBbC5XhJJezUbcfx-qAnfPjH568chTMaAkAsEALw_wcB:G:s&OCID=AID2000068_SEM_alOkB9ZE&MarinID=alOkB9ZE_368060503322_%2Bazure_b_c__79187603991_kwd-23159435208&lnkd=Google_Azure_Brand&dclid=CjgKEAiA2ITuBRDchty8lqPlzS4SJAC3x4k1mAxU7XNhWdOSESfffUnMNjLWcAIuikQnj3C4U8xRG_D_BwE). Al hacerlo usted contará con $200 USD para gastar durante 1 mes.

### Parte 0 - Entendiendo el escenario de calidad

Adjunto a este laboratorio usted podrá encontrar una aplicación totalmente desarrollada que tiene como objetivo calcular el enésimo valor de la secuencia de Fibonnaci.

**Escalabilidad**
Cuando un conjunto de usuarios consulta un enésimo número (superior a 1000000) de la secuencia de Fibonacci de forma concurrente y el sistema se encuentra bajo condiciones normales de operación, todas las peticiones deben ser respondidas y el consumo de CPU del sistema no puede superar el 70%.

### Escalabilidad Serverless (Functions)

1. Cree una Function App tal cual como se muestra en las  imagenes.

![](images/part3/part3-function-config.png)

![](images/part3/part3-function-configii.png)

2. Instale la extensión de **Azure Functions** para Visual Studio Code.

![](images/part3/part3-install-extension.png)

3. Despliegue la Function de Fibonacci a Azure usando Visual Studio Code. La primera vez que lo haga se le va a pedir autenticarse, siga las instrucciones.

![](images/part3/part3-deploy-function-1.png)

![](images/part3/part3-deploy-function-2.png)

4. Dirijase al portal de Azure y pruebe la function.

![](images/part3/part3-test-function.png)

5. Modifique la coleción de POSTMAN con NEWMAN de tal forma que pueda enviar 10 peticiones concurrentes. Verifique los resultados y presente un informe.

6. Cree una nueva Function que resuleva el problema de Fibonacci pero esta vez utilice un enfoque recursivo con memoization. Pruebe la función varias veces, después no haga nada por al menos 5 minutos. Pruebe la función de nuevo con los valores anteriores. ¿Cuál es el comportamiento?.

**Preguntas**

* ¿Qué es un Azure Function?
Azure Functions es una solución para integrar pequeños desarrollos con eventos de otros sistemas que permita responder de manera simple. 
Permite desarrollar con mayor eficacia platafomas sin servidor basadas en evento.
* ¿Qué es serverless?
Es un modelo de ejecución en el que el proveedor de la nube se responsabiliza por ejecutar fragmentos de código mediante asignación dinámica de los recursos.

* ¿Qué es el runtime y que implica seleccionarlo al momento de crear el Function App?
Proceso host del Azure Webjob que escucha eventos, recopila y envía información interaccionando con las Function.

* ¿Por qué es necesario crear un Storage Account de la mano de un Function App?
Esto se debe a que Functions se basa en Azure Storage para ciertas operaciones como lo son la administración de disparadores y Registros de ejecución de funciones. 
* ¿Cuáles son los tipos de planes para un Function App?, ¿En qué se diferencias?, mencione ventajas y desventajas de cada uno de ellos
Principalmente se basan en *consumo de recursos* y en *Ejecuciones* para definir los precios. 
![image](https://user-images.githubusercontent.com/49318314/98157990-3b1c9500-1ea8-11eb-9eb6-0519adcb1101.png)

Los planes pueden ser los siguientes:
- Ejecuciones
El costo está baasado en el número total de peticiones ejecutadas por mes de todas las funciones.
- Consumo de recursos
EL costo está basado en la medida de cuanto consumo de recursos se realizó en GB-s.
- Premium Plan
Provee mecanimos de escalamiento y features basado en número de eventos.
![image](https://user-images.githubusercontent.com/49318314/98158048-55ef0980-1ea8-11eb-99f8-b43486dc35f5.png)
-Functions Proxies
Mismos costos que el Premium.
* ¿Por qué la memoization falla o no funciona de forma correcta?
* ¿Cómo funciona el sistema de facturación de las Function App?
* Informe

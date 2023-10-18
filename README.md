# PruebaSofttek
Prueba técnica de QA DEV
 1.1 Ejercicio 1: Prueba exploratoria y reporte de bugs
					
La primera tarea es encontrar un bug, nos da igual en que web de internet lo encuentres, lo importante es poder encontrarlo y reportarlo. No te preocupes porque internet está lleno de ellos.			
Haz el reporte al nivel de detalle que consideres necesario para que el equipo de desarrollo pueda encontrarlo, debuggearlo y solucionarlo. Proporciona evidencias del fallo y resultado esperado. Clasifícalo en cuanto a prioridad, impacto y probabilidad de ocurrencia.

Respuesta Ejercicio 1
Reporte de Bug:
1. Titulo y ID: 'Orden de Menor a Mayor en sitio mercadolibre.com.ar no funciona o muestra duplicados' Ticket Nro XXXX (creado en JIRA o similar)
2. Entorno/Ambiente donde fue encontrado: Produccion (tambien podria ser QA o PreProd, depende de donde se este probando. NOTA: al ser PROD, el bug se llama 'incidente' en vez de bug, ya que toma una seriedad/relevancia/impacto distinta/o)
3. Pasos para reproducir el bug:
   a. ingresar en www.mercadolibre.com.ar
   b. hacer clic en boton 'hasta 35% off'
   c. marcar los siguientes radiobotones: - Llegan hoy, - Envio Gratis, - Programa Ahora 12
   d. Filtrar por precio '0 hasta 60.000'
   e. Ordenar por 'Menor precio'
OBSERVAR que los dos ultimos productos de la lista NO ESTAN ordenados por precio ($29482 y $41761)
4. Resultado esperado: que los productos de la lista esten ordenados de MENOR A MAYOR, en el rango de $0 a $60.000
5. Resultado actual: productos ordenados de menor a mayor SALVO los dos ultimos productos de la lista ($29482 y $41761)
6. Prueba visual:

   


					
1.2 Ejercicio 2: Automatización de una web 
Debes realizar una automatización consistente en:	
Buscar en Google la palabra “automatización”
 						
Buscar el link de la Wikipedia resultante
 						
Comprobar en qué año se hizo el primer proceso automático
 						
Realizar un screenshot de la página de la Wikipedia
 						
La resolución del ejercicio debe estar dentro de un repositorio de control de versiones para que
 							
podamos valorar arquitectura y codificación.
 						
					 					
1.3 Ejercicio 3: Tratamiento de datos en APIs En este enlace encontrarás la documentación de la API de una tienda de mascotas:
					
https://petstore.swagger.io/
					
Crea tu usuario mediante petición HTTP y posteriormente recupera sus datos llamando al servicio correspondiente.
 						
Recoge mediante petición HTTP, el JSON que retorna el endpoint /pet/findByStatus y lista mediante una función los nombres de las mascotas que se hayan vendido.
 													
-  El formato de salida deberá estar formado por la tupla {id, name}.
 									
-  Puedes utilizar la estructura de datos que prefieras.
 													 						
Crea una clase cuyo constructor requiera de la estructura de datos anterior y realiza un método que pueda recorrerla para poder identificar cuantas mascotas se llaman igual.
 							
								 									
-  Ejemplo de salida: {“William”: 11, “ Floyd”: 2} Como output, te pediremos el código (puedes
 									
separarlo en archivos como quieras) y los resultados de salida de los puntos anteriores.
 								
								 									
-  Recuerda que puedes utilizar el lenguaje que prefieras y cualquier mejora adicional será bien
 									
considerada
 									
La resolución del ejercicio debe estar dentro de un repositorio de control de versiones para que podamos valorar arquitectura y codificación. 

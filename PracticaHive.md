
# Práctica Hive

#### Elaboró: Alejandra López
Diciembre 2018

##### Esta práctica tiene el objetivo de hacer uso de Hive, la cual es una infraestructura que forma parte de Hadoop, utilizado para gestionar grandes datasets, mediante querys sobre los datos. 

Accessando a Hive

![AccesoHive.PNG](attachment:AccesoHive.PNG)





Creamos la tabla Votos en la Base de Datos testbd.

![CrearVotos.PNG](attachment:CrearVotos.PNG)

Cargamos los datos del archivo votacion.csv a la tabla votos. 

![CargaDatos.PNG](attachment:CargaDatos.PNG)

Realizamos una consulta a la tabla votos para verificar el contenido. 

![ContVotos.PNG](attachment:ContVotos.PNG)





Creamos una copia del archivo Encuestas.csv en la carpeta datosCompartidosHive.

![CopiaEncuesta.PNG](attachment:CopiaEncuesta.PNG)

Generamos la tabla Encuestas como External. 

![EncuestaExternal.PNG](attachment:EncuestaExternal.PNG)

#### ¿Cuántos votos se obtuvieron en los distritos 1048, 5572 y 8999? 

Como se puede observar en la pantalla inferior se obtuvieron los siguientes votos: 

1048 - 4,041

5572 - 2,002

8999 - 4,006

![pregunta1.PNG](attachment:pregunta1.PNG)

#### Haga una tabla votosPorGenero que contenga cuántos votos se obtuvieron por hombres y por mujeres.

Como se observa en la pantalla inferior, se obtuvieron los siguientes votos por género: 

Hombres -  50,044

Mujeres - 49,956

![VotosGenero.PNG](attachment:VotosGenero.PNG)

Exportamos el resultado de la consulta que contiene los votos del candidato 5 a nuestro directorio local. 

![dirlocal.PNG](attachment:dirlocal.PNG)

#### Confirme que el resultado generó un archivo en el sistema de archivos local. ¿Qué nombre tiene el archivo? ¿Cuáles son las últimas tres líneas?

En la pantalla inferior se verifica que el archivo votosCAND5 se generó en el sistema de archivos local.

![archdirlocal.PNG](attachment:archdirlocal.PNG)

Creamos una tabla particionada por el campo Candidato. 

![PartCand.PNG](attachment:PartCand.PNG)

Efectuamos la carga de los datos particionados del archivo votacion.csv a la tabla votosPart que se creo en el punto anterior. 

![part1.PNG](attachment:part1.PNG)

Realizamos una selección de registros de la tabla votosPart. 

![votosPart.PNG](attachment:votosPart.PNG)

Verificamos si los registros seleccionados en efecto corresponden al Candidato 4. 

Como se observa en la imagen inferior los registros no corresponden al Candidato 4. 

![verificacion.PNG](attachment:verificacion.PNG)



Utilizaremos particiones dinámicas para que se vayan creando distintos valores considerando los diferentes valores del campo Cand. 

![PartCand_2.PNG](attachment:PartCand_2.PNG)

Validamos la creación de las diferentes carpetas generadas por la partición realizada en el punto anterior. 

![PartVotosPart.PNG](attachment:PartVotosPart.PNG)

#### ¿Qué ocurre si consultamos nuevamente votosPart filtrando o no los campos con la cláusula WHERE?

Visualizamos el contenido del archivo 000000_0

![archivo000000.PNG](attachment:archivo000000.PNG)

![cat000000.PNG](attachment:cat000000.PNG)

Efectuamos la consulta en la tabla votos filtrando por el Candidato4

![filtrovotos.PNG](attachment:filtrovotos.PNG)

![ejecucionvotos.PNG](attachment:ejecucionvotos.PNG)

Filtramos votosPart incluyendo solo al Candidato4, observando que en efecto sólo se están considerando los votos correspondientes a dicho candidato. 

![filtrovotosPart1.PNG](attachment:filtrovotosPart1.PNG)

![filtrovotosPart2.PNG](attachment:filtrovotosPart2.PNG)

Ahora no aplicamos filtro por el Candidato4 a la tabla votosPart y vemos que nos envía el total de votaciones de los diferentes candidatos. 

![filtrovotosPart3.PNG](attachment:filtrovotosPart3.PNG)

![filtrovotosPart4.PNG](attachment:filtrovotosPart4.PNG)

Creamos una nueva tabla (candcasa), seleccionando algunos campos de las tablas votos y encuestas.

![union2tablas.PNG](attachment:union2tablas.PNG)

#### Encuentre el promedio de percepción de conocimiento de los candidatos según las casas encuestadoras 1, 3 y 6

![promediocandcasa.PNG](attachment:promediocandcasa.PNG)

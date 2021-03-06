# Práctica 5: Replicación de bases de datos MYSQL

En esta práctica necesitamos crear una base de datos en cada máquina. Ambas bases de datos se llamarán **Libreria** y contendrán la tabla **Libro** con las columnas de _título_, _autor_, _precio_ y _género_.

![Describe Libro](https://github.com/pcerezo/SWAP1819/blob/master/Practica5/describe_Libro.png)

En la máquina 1 insertamos valores a dicha tabla y, tras ejecutar la orden *"FLUSH TABLES WITH READ LOCK"* para colocar un cerrojo y proteger la información, generamos un fichero donde guardamos la información de la base de datos con formato **.sql** tal y como se muestra en la imagen con la orden **mysqldump**.

![mysqldump](https://github.com/pcerezo/SWAP1819/blob/master/Practica5/mysqldump.png)

Tras generar mencionado archivo, liberamos el cerrojo que pusimos sobre él y vamos a la segunda máquina (la máquina esclava). En ella usamos la orden **scp** para obtener el archivo .sql desde la máquina 1 (la máquina maestra). Posteriormente creamos la base de datos **Libreria** en la esta máquina y después importamos a mysql el archivo .sql de antes.

![unlock_tables_m1](https://github.com/pcerezo/SWAP1819/blob/master/Practica5/unlock_tables_m1.png)
![scp_Libreria_maquina2](https://github.com/pcerezo/SWAP1819/blob/master/Practica5/scp_Libreria_maquina2.png)

## Replicacion de BD automática maestro-esclavo
Después de hacer las modificaciones necesarias en el fichero de configuración de mysql, nos vamos a la máquina maestra donde creamos un usuario esclavo que será quien reciba todas las tablas de la base de datos replicada automáticamente. Ejecutamos las ejecuciones correspondientes seguidas de la colocación de un cerrojo para proceder posteriormente con la configuración en la máquina esclava en la que indicamos quién es el usuario maestro, los ficheros LOG correspondientes y el puerto que se utilice. Justo después ejecutamos **START SLAVE**. Desbloquemos las tablas y consultamos el estado del esclavo con **SHOW SLAVE STATUS\G** tal y como muestro en la siguiente imagen:

![show_slave_status\g](https://github.com/pcerezo/SWAP1819/blob/master/Practica5/show_slave_status%5Cg.png)

Podemos apreciar que no se muestra ningún tipo de error en los valores de las variables y que concretamente la variable **Seconds_Behind_Master** está a 0, lo que indica que la replicación entre ambas máquinas está funcionando.

Probamos ahora a introducir valores de prueba en la base de datos de la máquina maestra para comprobar que también aparecen en la máquina esclava:

![replicacion](https://github.com/pcerezo/SWAP1819/blob/master/Practica5/replicacion.png)

Por último, señalar que he creado un script de formato **.sql** en el que están asignadas todas las variables de la configuración del esclavo necesarias para la replicación automática, por lo que, si existiera algún problema con dicho proceso, bastaría con comprobar el estado del maestro en mysql y en función de ello modificar las variables correspondientes en el fichero. Justo después habría que parar el esclavo en mysql de la máquina secundaria, ejecutar *source **script.sql*** y volver a lanzar el esclavo. Éste es el script que he usado:

![script_sql](https://github.com/pcerezo/SWAP1819/blob/master/Practica5/script_sql.png)


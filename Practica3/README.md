# PRÁCTICA 3: Balanceado de carga
## Uso de nginx
Antes que nada muestro las IP's de cada máquina y los contenidos de cada archivo que vamos a tratar para demostrar el correcto funcionamiento de las herramientas:

La IP de la máquina principal es:

![ip_maquina1](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/ip_1.png)

Y el contenido de su archivo html que vamos a manejar es:
![html_1](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/archivo_html_1.png)

La IP de la máquina secundaria es:
![ip_maquina2](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/ip_2.png)

Y su correspondiente archivo html:
![html_2](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/archivo_html_2.png)

Por último, el balanceador de carga:
![balanc](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/ip_balanceador.png)

Una vez instalado el nginx procedo a editar su archivo de configuración indicando qué servidores son los que ha de balancear las peticiones que les llegan, dejándolo de esta manera:
![conf_nginx](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/conf_nginx.png)

Tras activar el servicio, procedo a comprobar el correcto balanceo que por defecto usará un algoritmo Round-Robin:
![balanceo_nginx](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/balanceo_nginx.png)

También podemos alterar el balanceo indicando mayor peso (mayor proporción de recepción de solicitudes) en una de las máquinas, por ejemplo en la máquina 1:
![balanceo_ponderado](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/balanceo_ponderado_nginx.png)


## Uso de haproxy
Tras instalar haproxy, activarlo y detener nginx, procedo a editar su archivo de configuración:
![haproxy_conf](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/haproxy_conf.png)

Y muestro su correcto balanceo:
![balanceo_haproxy](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/balanceo_haproxy.png)

## Apache Benchmark
Por último someto a una carga importante de 1000 peticiones de 10 peticiones concurrentes a ambos servidores orquestados por el balanceador nginx:
![apache_benchmark](https://github.com/pcerezo/SWAP1819/blob/master/Practica3/apache_benchmark.png)

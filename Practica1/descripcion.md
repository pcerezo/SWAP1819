#PRÁCTICA 1
Acceder por ssh y curl entre dos servidores.
##Descripción

Primero indico qué **interfaz de red** contiene cada servidor Ubuntu (ambos clonados pero con direcciones de red diferentes):


![interfaz1](https://github.com/pcerezo/SWAP1819/blob/master/Practica1/interfaz_red_maquina1.png)

![interfaz2](https://github.com/pcerezo/SWAP1819/blob/master/Practica1/interfaz_red_maquina2.png)

El servidor principal (la máquina 1) contiene el archivo hey.html en /var/www/html/ al que he podido acceder con curl tanto en la propia máquina que lo contiene como en el otro servidor:

![html] (https://github.com/pcerezo/SWAP1819/blob/master/Practica1/contenido_html_maquina1.png)

![curl1] (https://github.com/pcerezo/SWAP1819/blob/master/Practica1/curl_maquina1.png)

![curl2] (https://github.com/pcerezo/SWAP1819/blob/master/Practica1/curl_maquina2.png)

Por último muestro el correcto funcionamiento de **ssh**:
![ssh1] (https://github.com/pcerezo/SWAP1819/blob/master/Practica1/ssh_de_maquina1_a_maquina2.png)

![ssh2] (https://github.com/pcerezo/SWAP1819/blob/master/Practica1/ssh_de_maquina2_a_maquina1.png)



#PRÁCTICA 2

##Clonado de carpetas

Para mostrar el clonado de carpetas, muestro primero el contenido de la máquina principal (ubuserver):

![contenido1](https://github.com/pcerezo/SWAP1819/blob/master/Practica2/contenido_html_ubuntu1.png)

Después muestro el contenido de la misma carpeta en la máquina secundaria (ubuserver2) y seguidamente ejecuto la herramienta rsync:

![rsync_ubuntu2](https://github.com/pcerezo/SWAP1819/blob/master/Practica2/rsync_ubuntu2.png)

##ssh sin contraseña
Tras ejecutar **ssh-keygen** en la máquina secundaria para generar la llave pública/privada, indicar una contraseña en blanco y posteriormente ejecutar **ssh-copy-id 192.168.1.20** para copiarla en el servidor principal, obtengo que, finalmente el uso de ssh desde la máquina secundaria hacia la primaria no pide contraseña como podemos ver en la siguiente captura:

![ssh_sin_contraseña] (https://github.com/pcerezo/SWAP1819/blob/master/Practica2/ssh_sin_contraseña.png)

##Automaticación de copia de archivos: crontab
Tras comprobar el correcto funcionamiento de rsync y que ssh ya no pide contraseña, automatizo el proceso en crontab para que cada cierto tiempo ejecute la orden en un segundo plano. Para que el clonado sea más completo, he añadido las opciones **--delete** y **--exclude** en la parte de órdenes de crontab. Dicho archivo quedaría de esta forma:

![crontab] (https://github.com/pcerezo/SWAP1819/blob/master/Practica2/crontab.png)


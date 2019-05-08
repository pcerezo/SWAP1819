# PRÁCTICA 4: SEGURIDAD

## Creación del certificado SSL
Comenzamos en la máquina 1 habilitando el módulo ssl de apache y recompilándolo de la siguiente forma:

![Imagen1](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/1_server1_ssl_certificados.png)

Obtenemos los certificados autofirmados, recompilamos apache y probamos desde la máquina 2 que funciona:

![Imagen2](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/2_reiniciarApache.png)

![Imagen3](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/3_comprobar_https.png)

Hacemos lo mismo con el segundo servidor pero obteniendo los archivos mediante rsync:

![Imagen4](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/4_activarssl_reiniciarApache.png)

![Imagen5](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/5_rsync_balanceado.png)

En el balanceador también guardamos los archivos del certificado digital y además modificamos el archivo de configuración del balanceador nginx indicando el puerto por el que escuchar ssl y las rutas en las que almacenamos los archivos del certificado.

![Imagen6](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/6_nginx_conf.png)
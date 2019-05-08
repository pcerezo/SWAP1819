# PRÁCTICA 4: Seguridad

## Creación del certificado SSL
Comenzamos en la máquina 1 habilitando el módulo ssl de apache y recompilándolo de la siguiente forma:

![Imagen1](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/1_server1_ssl_certificados.png)

Obtenemos los certificados autofirmados, recompilamos apache y probamos desde la máquina 2 que funciona:

![Imagen2](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/2_reiniciarApache.png)

![Imagen3](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/3_comprobar_https.png)

Hacemos lo mismo con el segundo servidor pero obteniendo los archivos mediante rsync:

![Imagen4](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/4_activarssl_reiniciarApache.png)

![Imagen5](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/5_rsync_balanceador.png)

En el balanceador también guardamos los archivos del certificado digital y además modificamos el archivo de configuración del balanceador nginx indicando el puerto por el que escuchar ssl y las rutas en las que almacenamos los archivos del certificado.

![Imagen6](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/6_nginx_conf.png)

## Configuración del cortafuegos: iptables
Por último creo un script de configuración del cortafuegos en el servidor 1 con la herramienta iptables habilitando únicamente las entradas de conexiones ssh(22), http(80) y https(443).

![Imagen7](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/7_iptables_conf.png)

Finalmente indico la ruta de este archivo en el rc.local para que se ejecute el script automáticamente cada vez que se arranque de la máquina principal.

![Imagen8](https://github.com/pcerezo/SWAP1819/blob/master/Practica4/8_rc.local.png)
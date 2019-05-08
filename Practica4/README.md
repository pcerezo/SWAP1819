# PRÁCTICA 4: SEGURIDAD

## Creación del certificado SSL
Comenzamos en la máquina 1 habilitando el módulo ssl de apache y recompilándolo de la siguiente forma:

![Imagen1]()

Obtenemos los certificados autofirmados, recompilamos apache y probamos desde la máquina 2 que funciona:

![Imagen2]()

![Imagen3]()

Hacemos lo mismo con el segundo servidor pero obteniendo los archivos mediante rsync:

![Imagen4]()

![Imagen5]()

En el balanceador también guardamos los archivos del certificado digital y además modificamos el archivo de configuración del balanceador nginx indicando el puerto por el que escuchar ssl y las rutas en las que almacenamos los archivos del certificado.

![Imagen6]()
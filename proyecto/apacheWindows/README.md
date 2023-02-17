Instalar apache .msi
    Eso lo vamos a descargar de la ruta
Montar servicio Windows 
Repositorio de git descagarmos una web
Configurar el Apache ficheros de configuración TEMPLATE

Abrir el puerto 
Probar todo 

ESO DE ARRIBA SERIA UN SCRIPT DE INSTALACION, 
    que no es lo que vamos a montar en ANSIBLE

QUEREMOS UN SCRIPT CON IDEMPOTENCIA 


---
# Escenario 1

no tengo apache
ni configuracion
no tengo servicio

# Escenario 2

si tengo apache
ni configuracion
no tengo servicio

# Escenario 3

si tengo apache
si configuracion
no tengo servicio

# Escenario 4

si tengo apache
si configuracion
si tengo servicio y no esta arrancado

# Escenario 5

si tengo apache
si configuracion
si tengo servicio y si esta arrancado

# Escenario 6

si tengo apache
si configuracion pero obsoleta
si tengo servicio y si esta arrancado


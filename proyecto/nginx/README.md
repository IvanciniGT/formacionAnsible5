Queremos un play que nos:

- Asegure que la VERSION X del PROGRAMA nginx está instalado (Servidor web)
- Que tiene la configuración que me interesa
- Que está sirviendo una web que tengo en un repositorio de GIT

server {
        listen 80;
        server_name localhost;
        root /var/www/html;
        index index.html index.htm index.nginx-debian.html;
}

---

Necesitas tener SOFTWARE instalado  =  MAL !

---

Tengo un equipo de desarrolllo que me dice:
Para desplegar mi app necesitas la BBDD: MS SQL SERVER < - VERSION !

----

Escenarios que puedo encontrarse:

# ESCENARIO 1

Que la maquina tenga nginx 1.14 
con una configuración obsoleta
El servicio ya estaba arrancado 

# ESCENARIO 2

Que la máquina no tenga nginx

# ESCENARIO 3

Que la máquina tenag nginx 1.21, pero con otra configuración
Y con el nginx arrancado

# ESCENARIO 4

Que la máquina tenag nginx 1.21, 
pero con otra configuración
Y con el nginx parado

# ESCENARIO 5

Que la máquina tenag nginx 1.21, 
con la misma configuración que necesito
Y con el nginx parado

# ESCENARIO 6

Que la máquina tenag nginx 1.21, 
con la misma configuración que necesito
Y con el nginx arrancado

ESO ES IDEMPOTENCIA !

----


Paso1:
Instala nginx 1.21

Paso2:
Copia el fichero de configuración de nginx a la caperta adecuada

Paso3:
Arranca nginx.


---

Casos / EVENTOS que podrían desencadenar la ejecución de mi playbook:
- Solicitud de nueva instalación
- Solicitud de upgrade
- El sistema de monitorización detecta que la máquina no está sirviendo la web
- Directamente para monitorizar 
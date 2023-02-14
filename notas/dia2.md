# Estructura de un play

Dentro de un play, las tareas pueden definirse en 3 bloques diferentes:
- PRE_TASKS
- TASKS
- POST_TASKS

**Básicamente esta estructura nos ayuda a agrupar tareas a nivel conceptual.**

Hay algo funcional en esa estructuración.. poco...



Quiero instalar NGINX en un servidor

NGINX es un proxy reverso con capacidades WEB. 
Es usado habitualmente como servidor WEB y es EL SERVIDOR WEB MAS USADO DEL MUNDO

PRE_TASKS:
- Requisitos previos de instalación
TASKS: 
- Instalación del software
POST_TASKS:
- SmokeTest

---


# Estados de ejecución de las tareas:

- Ok
- Changed
- Failed

Cómo sabe ANSIBLE si una tarea ha ido mal, bien, os si ha provocado o no cambios?

El módulo que ejecuta la tarea manda esa inforamción de vuelta a ANSIBLE!

Quién ejecuta una tarea en Ansible? UN MODULO !

# MODULO DE ANSIBLE

Un módulo es un programa EXTERNO a ANSIBLE CORE, que ejecuta un tipo de tarea concreto.

- Si quiero crear un usuario en una máquina Linux, necesitaré UN MODULO
- Si quiero crear un usuario en una máquina Windows, necesitaré OTRO MODULO
- Si quiero instalar un programa en una máquina Windows, necesitaré OTRO MODULO
- Si quiero iniciar un servicio en una máquina Linux, necesitaré OTRO MODULO


# Todo MODULO SERÁ CAPAZ DE INFORMAR VERAZMENTE DE SI UNA TAREA HA PROVOCADO CAMBIOS?

Debería ser que si... pero va a ser que NO. Dependerá del módulo concreto y de la tarea concreta.

```yaml

- name: Asegurarse que el archivo C:\Temp\foo.conf no está en la computadora
  win_file:
    path: C:\Temp\foo.conf
    state: absent

- name: Asegurarse que la carpeta C:\Temp\folder\subfolder está en la computadora.
  win_file:
    path: C:\Temp\folder\subfolder
    state: directory

- name: Asegurarse que la carpeta C:\Temp no está en la computadora.
  win_file:
    path: C:\Temp
    state: absent

```

win_file

Y en ese programa la lógica de programación:
Mira si la ruta existe.
Si existe y state:absent entonces: BORRAR LA RUTA ! -> Diré que ha habido cambios? SI
Si no existe y state:absent entonces? Todo bien.    -> Diré que ha habido cambios? NO

```yaml

- name: Asegurar que el usuario BOB está en la máquina con unas determinadas características
  win_user:
    name: bob
    password: B0bP4ssw0rd
    state: present
    groups:
      - Users

- name: Asegurar que el usuario BOB NO está en la máquina
  win_user:
    name: bob
    state: absent

```

win_user:
    usuarios: Ivan
    state: Absent
    
El modulo debería:
1- Mirar si hay un usuario Ivan
2- QUE SI: Borrarlo -> Informo de que ha habido cambios? SI
3- QUE NO: Todo ok  -> Informo de que ha habido cambios? NO

```yaml
- win_shell: C:\somescript.ps1 
```

Tiene el modulo idea de si el script ha provocado un cambio en el host? NUNCA JAMAS !


EN MUCHOS casos, usaremos módulos que NO INFORME CORRECTAMENTE acerca del estado REAL de la tarea:
- OK
- CHANGED
- FAILED
Ansible nos ofrecen 2 palabras para controlar el estado de una tarea:
failed_when
changed_when

-----

.....
- Tarea 9
  Esta tarea NO PROVOCA CAMBIO.. por lo que no ACTIVA el handler 2

- Tarea 10
  Esta tarea SI PROVOCA CAMBIO... por lo que ACTIVA HANDLER 1

- Tarea 11
  Esta tarea SI PROVOCA CAMBIO... por lo que ACTIVA HANDLER 1 

- Tarea 12

< AQUI ACABA EL BLOQUE TASKS 

Y por ello, inicia la ejecución de los handlers que hayan sido activados:

- HANDLER 1

----
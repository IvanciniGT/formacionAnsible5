En YAML, tenemos que tipos de nodos:
- Escalares
    - Numeros
    - Textos
    - Valores lógicos
    - Nulo
    - Fechas
- De colección
    - Listas ordenadas
    - Diccionarios

Los datos decidiremos estructurarlos de una deterinada forma.

En base a cómo hayamos decidido estructurar los datos, 
así la manera en la que deberemos procesarlos.

Habrá maneran más cómodas que otras.

La manera en la que procese los datos, 
influirá en la forma en la que los estructure?

Dicho de otra forma:

Voya. buscar una forma de estructurar los datos que posteriormente me 
sea cómoda de procesar? NO, ni de broma ! NUNCA

Por qué?

Los datos, los tendré que estruturar de la forma que sea más cómodo
RELLENARLOS !

Mi marrón , mi problema, será el procesarlos según esa estructura 
que haya definido.

1º Defino la estructura más conveniente
2º Me busco la vida para procesarlo... así sea complejo para mi.

---
# Ansible

## Project < Engine

### PLAYBOOKS

### INVENTARIOS

Catálogo de todos los entornos que voy a gestionar remotamente a través de Ansible

Lo entornos tendrán una serie de propiedades de configuración que habrá que suministrar:
- ip
- hostname
- credenciales
- sistema operativo? NO ESTE NO ! -> Inventario? Facts de la máquinas
- protocolo para conectarme? ssh, winrm

## AWX     < Tower
## Galaxy


----

Nueva máquinas

- 1 usuario administración
    contraseña
    ssh

- 1 usuario monitorizacion
    contraseña
    ssh

- Instalar agente de monitorizacion

- Instalar BBDD

- Abrir puertos


## Por qué quiero muchos playbooks y no uno solo?

Pero si hay necesidades comunes y no quiero reescribir las mismas tareas en 800 playbooks

##### En el ejemplo de arriba:
                                                        hosts
                                                        -------------------
- Playbook1: usuario administrador                      all
    - Role1: usuario admin

- Playbook2: monitorizar                                servidores
    - Role1: usuario monitorizacion
    - instalar agente de monitorizacion
    - Role2: abrir puertos 30203

- Playbook3: BBDD                                       servidores bbdd
    - Role1: usuario bbdd
    - instalar BBDD
    - Role2: abrir puertos 3306

- Role 1: usuario
- Role 2: abrir puertos


### ROLE de Ansible

Conjunto de tareas reutilizable

** La orquestación de los playbooks -> Esto no lo hace ansible-project/engine
                                    -> Ansible Tower/AWX
                                               ^
                                            Jenkins



ansible-playbook -i inventario playbook.yaml






----
Una red permite conectar procesos que corren en maquinas

 -------------------------------------------------------------
  |                                                 |
IvanPC                                          ServidorWeb
  |                                                 |
  navegador (chrome)                                servidor web (nginx)
  
  
Una cosa es la RED
Otra cosa es el dispositivo físico que use para conectarme a una red Fisica: NIC
Otro cosa es una interfaz de red, que es el nombre que le pongo bajo un SO
  a una conexión a una red
  
Servidor Web:
- interfaz de red: ethernet: 1 o varios NICs : RED FISICA DE MI EMPRESA
    IPv4? 172.X.X.X       192.168.X.X
    IPv6
- interfaz de red: loopback                  : RED VIRTUAL DENTRO DEL HOST
    IPv4? 127.0.0.1


----

Abrir un puerto de todas las interfaces de red para todas las direcciones entrantes
                    80              
                    
Un playbook que haga esto... no será tan simple
Un playbook que haga algo... no será tan simple

POR EL PUÑETERO CONCEPTO DE IDEMPOTENCIA: No importa el estado inicial(actual) siempre debe acabar igual

Escenario 1: 
Que la máquina sea Windows
Ya esté abierto

Escenario 2: 
Que la máquina sea Ubuntu
Ya esté abierto

Escenario 3: 
Que la máquina sea RHEL
Ya esté abierto


Cómo será la estructura de tareas

```yaml

    tasks:
        - name: Obtener el sistema operativo de la máquina
        
        - name: Asegurarme que el puerto queda abierto si tengo una máquina windows

        - name: Asegurarme que el puerto queda abierto si tengo una máquina ubuntu

        - name: Asegurarme que el puerto queda abierto si tengo una máquina redhat
        
        - name: Si tengo una máquina desconocida, cortar el playbook con un error
            



```
abrir-puertos
    ├── README.md           Expliación de cómo fiunciona este role que estamos creando
    ├── defaults            VALORES DE VARIABLES DE PARAMETRIZACION: puerto que quiero abrir
    │   └── main.yml
    ├── files               FICHEROS QUE NUESTRAS TAREAS PUEDAN NECESITAR: configuración, imagenes..
    ├── handlers
    │   └── main.yml        HANDLERS QUE PODRIAN ACTIVAR NUSTRAS TAREAS
    ├── meta                Metadatos del role: Autor, Para que sirve, URL 
    │   └── main.yml
    ├── tasks               TAREAS QUE QUIERO REUTILIZAR
    │   └── main.yml
    ├── templates           FICHEROS CON PLANTILLAS JINJA QUE NUESTRAS TAREAS PUEDAN NECESITAR
    ├── tests               PLAYBOOK PARA PROBAR EL ROLE a ver si funciona
    │   ├── inventory
    │   └── test.yml
    └── vars                VALORES DE VARIABLE INTERNAS (QUE NADIE QUIERO QUE CAMBIE)
        └── main.yml
        
Esta es la estructura básica... La podría haber creado yo.
El comando ansible-galaxy init lo ha hecho por mi.

Puede ser que mi ROLE por su naturaleza, no necesite algunas de estas carpetas... las borro







Familia de sistema operativo:

Windows
    distribuciones: Windows Server
    distribution:   Windows pro

Redhat:
    distribution: Redhat
    distribution: CentOS
    distribution: Fedora
    distribution: AmazonLinux

Debian:
    distribution: Debian
    distribution: Ubuntu
    distribution: Xubuntu
    

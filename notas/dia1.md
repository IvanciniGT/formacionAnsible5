# Ansible

Es un conjunto de herramientas de software, bajo el paraguas de Redhat Inc.

Todas esas herramientas son OPENSOURCE. 

No todas esas herramientas son GRATUITAS. (FREEWARE)

FREE SOFTWARE = FREWARE + OPENSOURCE

Eso es una politica de REDHAT:

- RHEL: Redhat Enterprise Linux (Opensource + DE PAGO)  <~ Fedora
- Openshift <~ OKD
- JBoss <~ Wildfly
- Ansible Engine <~ Ansible Project ****
- Ansible Tower  <~ AWX

## Herramientas dentro del ecosistema ANSIBLE

### Ansible project (Ansible Engine)

Herramienta que nos ofrece:
- Sintaxis DECLARATIVA para crear SRIPTS de automatización:     Playbooks
- Sintaxis (varias) para crear/definir:                         Inventarios
- Algunas utilidades de linea de comandos, con las que podremos hacer operaciones
  sobre los playbooks y los inventarios

Esta herramienta (y sus utilidades delinea de comandos), se pueden ejecutar en WINDOWS?  NO, no es posible!
Esta herramienta se ejecuta en LINUX ! Es una herramienta 100% Linux.

Esta herramiemnta la podemos usar para:
- Administrar entornos remotos (Windows, Linux, ....).    ***
- Configurar entornos remotos (Windows, Linux, otros...)  ***
- Me permite automatizar tareas... de cualquier tipo.

#### Alternativas a ANSIBLE

- Terraform: Muy especializada en automatizar adquisión de infraestructura en CLOUDs.
             Aunque permite automatizar otras tareas.
- Puppet, Chef, Salt
- Script de la shell, Script de la powershell, Archivo .bat, Python

### AWX (Ansible TOWER) - VIERNES (Introducción)

Herramienta que me ofrece:
- Consola WEB centralizada desde la que poder ejecutar playbooks en entornos remotos
- API REST para solicitar la ejecución de playbooks en entornos remotos
- ...

### Ansible Galaxy - JUEVES/VIERNES

???

---

# Sintaxis declarativa

Todas las herramientas que están triunfando a día de hoy, lo hacen por usar una SINTAXIS DECLARATIVA!
- Kubernetes

  > Kubernetes, en mi entorno de producción debe haber entre 5 y 10 replicas de esta aplciación instaladas y en funcionamiento

- Terraform

  > Terraform, necesito un volumen de 10Gbs en Azure y un servidor con 8 cores y 64Gbs de RAM.

- Ansible

  > Ansible, en esta máquina necesito estos paquetes instalados
  > Ansible, en esta máquina necesito estos usuarios creados
  > Ansible, en esta máquina necesito esta configuración.

## Ejemplo conceptual uso lenguaje imperativo

> Felipe! pon una silla debajo de la ventana !            Imperativa

Todos los lenguajes de scripting tradicionales: BASH, Powershell, .BAT, PYTHON usan lenguaje IMPERATIVO.
Y aunque el lenguaje imperativo no resulta MUY NATURAL... es MUY ENGORROSO ! No lo queremos !

mkdir:  "make" directory                                Imperativo

El problema grande de este tipo de sintaxis, es que no ME CENTRO EN LO QUE NECESITO.... 
Sino en dar las instrucciones para conseguir LO QUE NECESITO.


## Ejemplo conceptual uso lenguaje declarativo

> Felipe! Debajo de la ventana tiene que haber una silla.  DECLARATIVO !

En esta frase, me centro en LO QUE NECESITO

Felipe, es un personaje BIEN MANDAO... un poquito corto, pero MUY BIEN MANDAO = COMPUTADORA !

## Problema con el uso de sintaxis imperativa.

> Felipe! Si no hay sillas,
>    VETE AL IKEA                                        Más órdenes
>    Y COMPRA UNA SILLA                                  Más órdenes

> SI hay algo que no sea una silla debajo de la ventana:  IF - ELSE
>    QUITA ESO DE EN MEDIO !                             Otra orden

> Si no hay una silla debajo de la ventana:
>    Felipe! pon una silla debajo de la ventana !        Imperativa
> SINO
>    Todo está bien 

## Ventajas de usar lenguaje declarativo

> Felipe! Debajo de la ventana tiene que haber una silla.  DECLARATIVO !

Si no hay silla.... me da igual... que Felipe se busque la vida para conseguirla
Si ya hay una silla... me da igual... 
Si hay un mueble debajo de la ventana... me da igual

FELIPE ES EL RESPONSABLE DE hacer lo que tenga que hacer, para conseguir LO QUE YO NECESITO !

---

Ansible (todas estas herramientas) hoy en día se encuadran dentro de lo que llamamos herramientas DEVOPS

# DEV--->OPS

Cultura, un moviento en pro de la AUTOMATIZACION !

No es un perfil. No es una persona.
Dentro de muchas empresas, a las personas que se encargan de hacer esas AUTOAMTIZACIONES se las denomina DEVOPS.
Pero lo que significa ese perfil "devops" en cada empresa es diferente.

El gran despido en el mundo IT dicen que se debe a las IAs (Inteligencias Artificiales)... mentira. 
Se debe a las AUTOMATIZACION !

## Lo que significa AUTOMATIZAR:

AUTOMATIZAR SIGNIFICA que ahora, en lugar de hacer las tareas que hacíamos, 
construimos programas que hacen esas tareas por nosotros.

HOY EN DIA, TODOS los perfiles en el mundo IT los hemos convertido en PROGRAMADORES.

- Desarrollador
- Tester
- Sysadmin
    - Terraform
    - Ansible
    - Kubernetes
    - ...

Ansible me permite AUTOMATIZA UN TIPO MUY CONCRETO DE TAREAS: Tareas de administración de sistemas
Es la herramienta que se ha impuesto.

Pero ANSIBLE solo es un eslabon más en un cadena mucho más larga.

Ansible me permite configurar/admisnitrar un entorno remoto.
Pero... y ese entorno, de donde lo saco? Aquí también hay un cambio de tendencia!
Los entornos en las empresas, los compro ? y los tengo on premmises? NO , en clouds.

## Cloud

Es el conjunto de servicios que una empresa ofrece a través de internet a otras empresas /personas
(servicios relacionados con el mundo TIC)

Dentro de los clouds, encontramos:
- IaaS  Servicios de infra
- PaaS  Servicios de plataforma (Cluster de Kubernetes, BBDD)
- SaaS  Servicios de software (Office 365, Cloud9)

# Y automatizo la obtención del entorno a través de un cloud? SI... con terraform
# Y automatizo la obtención del entorno a través de VMWare?   SI... con vagrant

CADA UNA DE ESAS HERRAMIENTAS automatiza un ESLABON... unas tareas muy concretas.

El mundo devops va de montar una AUTOMATIZACION GLOBAL, end2end de principio a fin.

Por ejemplo:

Los desarrolladores de la casa, tienen una versión nueva de la app de HOME BANKING.

Quiero: 
1- Adquirir un entornode pruebas para la nueva versión en un cloud:             TERRAFORM
2- Planchar (configurar) ese entorno con unas características (plantilla)       ANSIBLE
3- Instalar la última versión del código de la app de HOME BANKING en
   el nuevo entorno                                                             MAVEN + ANSIBLE
4- Someter a pruebas automátics a esa aplicación                                SELENIUM, JMETER, ...
5- Instalar eso, si es que funciona en un entorno de producción             
    Lo cual puede implicar que genere un nuevo entorno de producción:           TERRAFORM
    Entorno que tendré que planchar                                             ANSIBLE
    Donde desplegaré la app                                                     ANSIBLE
    Y le haré unas pruebas de humo                                              ????

Y todas tareas ATOMICAS, concretas, las necesitaré ORQUESTAR: Servidor de automatización:
                                                                                JENKINS
                                                                                AZURE DEVOPS (TFS)
                                                                                BAMBOO (Atlassian)
                                                                                TEAMCITY
                                                                                GITLAB CI/CD
                                                                                GITHUB Actions
                                                                                TRAVIS CI
                                                                                
Estas herramientas deben ser operadas y ANTES NO HABIA ESE PERFIL EN LA EMPRESA ~> Perfil DEVOPS

Pero el que crea un script de AUTOMATIZACION de unas tareas de configuración de un servidor... Sysadmin

Y ahora simplemnente los SYSADMINS trabajan con unevo tipo (familia) de herramientas. Esto no es un DEVOPS
Eso es un adminsitrador de sistemas que conoce 4 herramientas nuevas.

---

# Ansible PLAYBOOKS

Un playbook es un script de automatización, lo que antes montaba con PYTHON, BASH, PS1

Para crear esos playbooks usamos sintaxis DECLARATIVA <<< ESTA ES LA MAGIA DE ANSIBLE !

Ansible ... y en general CUALQUIER HERRAMIENTA que usa sintaxis declarativa, hace especial enfasis en el concepto de 
IDEMPOTENCIA !

## Idempotencia

No importa el estado actual de un sistema, después de aplicarle el trabajo pertinente, SIEMPRE DEBE QUEDAR EN EL MISMO ESTADO.

### Ejemplo:

> Monto un script que me asegure que unos paquetes en unas versiones ESTAN PRESENTES en una máquina, y
  una determinada configuración (usuarios, permisos, puertos) ESTA APLICADA A MI MAQUINA

> > Cúantas veces querré ejecutar ese script? 

Quién ejecuta este programa/script? Se ejecutará por un Orquestador... cuando... quién sabe.
- Si un sistema de monitorización detecta que un servidor no contesta.
- Cuando escale un sistema
- Cuando actualice un sistema

Hoy en día ese script quiero que ejecuta ... no se... quizas una vez al día, cada hora, cada semana, ante cierto evento.

Estos scripts se escriben en un lenguaje que se llama YAML

# YAML

Lenguaje de marcado de información, equivalente a JSON, XML.

YAML es el que se está imponiendo.
De entrada, se ha comido a JSON < LITERALMENTE
Hoy en día cualquier documento JSON es un documento YAML. Dentro de la especificación de YAML (1.2) se ha incluido la de JSON.

Herramientas que trabajan con YAML:
- Ansible
- Kubernetes, Openshift...
- AzureDevops, Gitlab CI/CD
- La configuración de RED de una máquina ubuntu
 
---

# Qué es Linux? 

Un KERNEL de Sistema Operativo != Sistema Operativo

Un sistema operativo = FALSO !

Un sistema operativo, incluye muchos componentes de software:
- Un kernel
- Un gestor de arranque
- Shells
- Comandos
- Librerias
- Drivers
- Utilidades
- ...

Al fin y al cabo, LINUX es el Kernel de SO más usado en el mundo... por mucha diferencia ~> Android

En las empresas solemos usar Sistemas operativos GNU/Linux. Esos sistemas operativos se ofrencen en las llamadas DISTRIBUCIONES DE GNU/LINUX:
- Redhat Enterpise Linux
- Debian > Ubuntu
- Suse
- ...

--- 

# Tiene Kernel windows

Si tiene kernel.
De hecho microsoft ha tenido 2 kernels a lo largo de su historia:
- DOS -> MS-DOS, Windows 3, Windows 95, Windows 98, Windows Millenium
- NT -> New Technology -> Windows NT, Windows Xp, Windows Servers, Windows 7, 8, 10, 11

De hecho hoy en día, Microsoft permite ejecutar en paralelo con el kernel de Microsft: NT un Kernel Linux: wls2

La apuesta de Microsoft por Linux es GIGANTE !

---

# Quién desarrollo git?

Linus Torvalds > Linux 

Para poder desarrollar Linux, necesitaba de un Sistema de control de versión ~> git

La apuesta de Microsoft por git es aberrante! 

Microsoft abandonó su propio sistema de control de versión TFS en favor de git

Y le ha metido una pasta (dinero $$$$$) gigante a Github (lo compró hace años)

---

# MODULO DE ANSIBLE

Un módulo es un programa EXTERNO a ANSIBLE CORE, que ejecuta un tipo de tarea concreto.

- Si quiero crear un usuario en una máquina Linux, necesitaré UN MODULO
- Si quiero crear un usuario en una máquina Windows, necesitaré OTRO MODULO
- Si quiero instalar un programa en una máquina Windows, necesitaré OTRO MODULO
- Si quiero iniciar un servicio en una máquina Linux, necesitaré OTRO MODULO
- Si quiero iniciar un servicio en una máquina Windows, necesitaré OTRO MODULO

Ansible no hace nada, más que solicitar a MODULOS que hagan trabajo.

Nosotros podemos crear NUESTROS PROPIOS MODULOS.
Pero Ansible ya lleva unos cuantos cargados de antemano.

Cuántos módulos se incluyen con ANSIBLE? MILES !

Nuestro objetivo en el curso NO ES CONOCER TODOS ESOS MODULOS. Necesitariamos 100 horas de curso.
Y de esos, en la práctica usaríamos 20... 50.

Nuestro objetivo PRIMERO en el CURSO es: (Lo referente a playbooks)
- Aprender a manejar la sintaxis de Ansible (TODA LA SINTAXIS: SU ESQUEMA YAML)
- Jugar con algunos modulos, lo suficiente como para entender la MECANICA de uso de los módulos
  y acostumbrarnos a mirar la documentación de los módulos.

---

# Arquitectura de Ansible project

NODO MAESTRO                                -------> NODOS REMOTOS, ENTORNOS ADMINISTRADOS
donde se ejecuta un playbook de ansible                 Pueden ser Linux, Windows,...
Este nodo necesita tener instalado ANSIBLE              Aqui también necesitamos Python
Este nodo NO PUEDE SER WINDOWS. Solo LINUX
Aqui necesitamos python

---

Ejecutar un playbook:

$ ansible-playbook FICHERO-PLAYBOOK.yaml

Al ejecutar un playbook, me muestra al finalizar un resumen del estado de las tareas:

PLAY RECAP **************************************************************
localhost                : ok=4    changed=0    unreachable=0    failed=0   

# Estados de las tareas:

Una tarea en Ansible puede acabar en estado:
- Ok:       Que se ha ejecutado correctamente y NO ha provocado ningún cambio en el entorno REMOTO!
  Se representan en color VERDE
- Changed:  Que se ha ejecutado correctamente y ha provocado un cambio en el entorno REMOTO !
  Se representan en color AMARILLO
- Failed:   Que no se ha ejecutado correctamente. FALLO !
  Se representan en color ROJO
- Skipped:  La tarea no se ha ejecutado (se ha saltado)
  Se representan en color AZUL

En la mayor parte de los playbooks que diseñemos (hay excepciones) la segunda vez que ejecutásemos el playbook, 
deberíamos conseguir ver todas las tareas en estado: Ok

Hay que tener mucho CUIDADO y prestar MUCHA ATENCION al estado de als tareas CUANDO DISEÑAMOS UN PLAYBOOK

Un playbook BIEN DISEÑADO, la segunda vez, debería dejar todo en VERDE (OK) ~> IDEMPOTENCIA

Ansible me garantiza la IDEMPOTENCIA? NO. La debo garantizar YO al crear el playbook.
Los módulos de ansible me garantizan la IDEMPOTENCIA: La mayoría, no todos. 

---

# Qué es UNIX, hoy en día?

DOS especificaciones de COMO MONTAR UN SISTEMA OPERATIVO, basadas en aquel antiguo sistema operativo:

SUS + POSIX

Lo grandes fabricantes de HARDWARE suelen montar su propio Sistema operativo para controlar SU HARDWARE.

HP:  HP-UX UNIX®
IBM: AIX   UNIX®
ORACLE: SOLARIS UNIX®
APPLE: MacOS UNIX®

MS Windows. Cumple con el estandar UNIX®? Parte de él. POSIX los windows SERVER

Linux? cumple con el estandar UNIX®? Supuestamente. Nunca lo sabremos.
Se montó basado en ese estandar, pero nunca lo certificarón, ni nunca se hará. 

Eso cuesta dinero, y se pretende un SO GRATUITO

# Qué era UNIX?

UNIX era un sistema operativo creado por los laboratorio BELL de AT&T.
Su última versión fue en 2004

El sistema operativo más influyente del mundo.

---

Entre los módulos que podemos usar para ampliar la seguridad en el kernel de LINUX encontramos:
SELinux  <~ Redhat
AppArmor <~ Debian y Ubuntu
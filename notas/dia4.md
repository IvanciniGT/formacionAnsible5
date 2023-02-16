# Ansible y Windows

1. Creado un servidor windows 2022 en Amazon.

   NOTAS: No tiene habilitado winrm por defecto... La imagen es una KK
   En la empresa debería usar una imagen con winrm pre-habilitado

2. Entrar en la máquina por Remote Desktop (escritorio remoto) y ejecutar un script que nos da Ansible:

   https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1
   
   Esto habilita winrm

3. Hemos abierto las reglas de firewall de la RED (no las de la máquina: esto lo hace el script) para 
   permitir el acceso por winrm
   
 Con esto TODO LISTO !

La comunicacion se hace mediante TLS:

El protocolo TLS no permite frustrar 2 tipos de ataques:

- Suplantación de identidad     < Se usa un certificado (Documento de Identidad emitido por el gobierno)
                                                         ______________________             ___________
                                                            CERTIFICADO                     Entidad certificadora

- Man in the middle             < Encriptando la información que cliente y servidor se mandan
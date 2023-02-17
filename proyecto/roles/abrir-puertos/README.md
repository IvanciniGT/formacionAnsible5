abrir-puertos
=========

Este role abre puertos en distintos sistemas oeprativos.

Requisitos
------------

Un sistema operativo entre:

- Windows
- Ubuntu (con `ufw` activado)
- Familia Redhat (Redhat Enterprise Linux, Fedora, CentOS...) (con `firewalld` activado)

Variables
--------------

| Variable      | Tipo      | Concepto                      | Valor por defecto |
| ------------- | --------- | ----------------------------- | ----------------- |
| `puerto`      | numero    | Puerto a abrir en el firewall | No asignado       |
| `protocolo`   | texto     | Protocolo de comuniación      | tcp               |
| `nombre`      | texto     | Nombre de la regla            | No asignado       |

Ejemplo de uso
----------------

```yaml

    - name: Abrir el puerto 80
      include_role:
        name: abrir-puertos
      vars:
        puerto: 80
        protocolo: tcp
        nombre: "http"

```

Cualquier duda
----

Escribir a: <ivan.osuna.ayuste@gmailcom>
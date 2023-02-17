Git es un sistema de control de versión
===

Ahí dejamos el código de nuestra app.

Lo que genereramos en GIT son COMMITs

# COMMIT

Un commit es un backup completo de estado del proyecto en un momento dado.
Una copia De TODOS LOS ARCHIVOS en un momento dado.

Asociado a un commit se guardan metadatos:
- Autor
- Cuando se hizo
- Qué novedades incluye este commit con respecto al anterior

En GIT los commits se guardan en RAMAS

# Qué es una RAMA (branch)

Linea de evolución paralela en el tiempo de mi proyecto.

Un proyecto en UN INSTANTE DE TIEMPO tiene diferentes ramas de evolución temporal.

    Desarrollo ................F1(a)...F1(ab)..........
                                 ^      ^
        Lucas  ................F1(a)    ^
        Felipe ........................F1(b)

En ocasiones, cuando quiero llevar una foto (commit) de una rama a otra, es necesario una fusión de cambios.

Git, a diferencia de otros SCM (source code managers), es un sistema distribuido.
En git NO HAY UN REPO CENTRALIZADO (como existe en CVS o en SVN)

Cada persona del proyecto tiene su propio REPOSITORIO, donde guarda sus ramas y sus commits

                        Repo del proyecto 1
                            Rama desarrollo: C1, C2, C3
                    Servidor que aloje repos remotos de git
                                |
     ---------------------------------------------------------
     |                                                       |
    IvanPC                                                  MenchuPC
    - Repo proyecto 1                                       - Repo del proyecto 1
        - Rama desarrollo                                      - Rama desarrollo
            ^,   ^    C3                                           C1, C2.  ^
        - Rama ivan                                            - Rama menchu
            C1, C2     v  C4                                            v   v    C3

## Operaciones básicas de git

    git commit -> Generar una foto del proyecto (backup)
    git push   -> Enviar commita (rama) a un remoto
    git fetch  -> Recuperar cambios de un remoto

    Al recuperar cambios de un remoto, querremos fusionar esos cambios (que haya hecho otra persona) con los mios
    git merge  -> Fusionar cambios
    git rebase -> Otra forma de hacer una fusión de cambios

    git pull   -> git fetch + git merge < Por defecto
                            + git rebase

Se suele usar un conjunto de ramas preestablecido en cada empresa: Flujo de trabajo de GIT

- master / main:    Lo que hay en esta rama se entiende que está listo para producción
                    NUNCA JAMAS se hace un commit en esta rama. Solo se copian commits de otras ramas

- desarrollo/development/develop/dev: Aquí es donde se hacen los commits con los cambios que vamos haciendo al proyecto
                                      Cuando tengo aquí una versión completa y funcional, la comparto (commit) a master

- Rama por cada colaborador: Donde cada colaborador hace sus commits y los comparte a la rama desarrollo
- Rama por cada funcionalidad: Donde TODOS los colaboradores que estén involucrados en una funcionalidad hacen
                               sus commits y los comparten a la rama desarrollo



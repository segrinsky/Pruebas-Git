# Git + Consola

## Requisitos

- Cliente consola: https://git-scm.com/
- Repositorio en servidor Git: https://github.com/

---

## Iniciar consola

1. Instalar el cliente Git
2. Abrir la terminal
    1. Para usuarios Windows abrir la terminal llamada `Git Bash`.
    2. Para usuarios Linux/Mac abrir la terminal por defecto.

---

## Comandos de la terminal

- `ls`: Listado de archivos y directorios del directorio actual.
- `cd {nombre-de-directorio}`: Posicionarse en el directorio: `nombre-de-directorio`
- `cd ..`: Posicionarse en el directorio padre. Nota: el espacio en medio es importante.
- `clear`: Limpiar la terminal.
- `mkdir {nombre-de-directorio}`: Crea un directorio con el nombre: `nombre-de-directorio`

---

## Comandos Git

- `git clone {url-repositorio}`: clona en el git local el repositorio. Debe clonarse en un directorio vacío.
- `git status`: Verifica el estado del branch sobre el cual se está posicionado.
- `git fetch`: Actualiza el listado de repositorios remotos.
- `git add {archivo/directorio}`: Agrega los archivos o directorios modificados al stage area. Puede utilizar `git add .` para agregar todos los archivos y sub-directorios de un directorio en
  particular.
- `git commit -m "comentario del request"`: Crea un commit con los archivos que existen en el stage area
- `git checkout {branch}`: Realiza el cambio a otro branch
- `git chechout -b {branch}`: Realiza el cambio a otro branch y en este caso lo crea.
- `git pull origin {branch-remoto}`:  Actualiza el branch local con el `branch-remoto`
- `git push origin {branch-remoto}`: Envía los cambios realizados en el repositorio local hacía el `branch-remoto`
- ` git config --global {propiedad} {valor}`: Utilizado para añadir configuraciones globales:
    - `user.name`
    - `user.email`
    - `alias.{shortcut}`
- `git config --list --show-origin`: Lista la configuración actual

- `git config --global user.name "Leonardo Camacho"`
- `git config --global user.email leocamachocr@gmail.com`

// usa el editor code por defecto y espera hasta que el editor se cierre
`git config --global core.editor "code --wait"` // Esto es opcional
//Abre configuraciones globales
`git config --global -e`

// Para eliminar el crlf en windows usar:
`git config --global core.autocrlf true`: o `input` para mac





## Remover configuraciones locales
git config --global --unset user.name
git config --global --unset user.email
git config --global --unset credential.helper


### ¿Cómo funciona Git?

repositorio principal -> main -> archivos(.java, .md, ), directorios, etc
- Objetivo principal de Git: Mantener un registro de los cambios realizados en los archivos.
- Mantener el trabajo concurrente de los desarrolladores.

Organización de git
- Repositorio principal -> main
  - archivo: src/main/java/com/hola/Hola.java -> 3 desarrolladores: A, B, C

```java
public class Hola {//A
    public static void main(String[] args) {//A
        System.out.println("Hola Mundo");//B
        System.out.println("Hola Mundo de nuevo");//C
    }//A
}//A
```
- Necesitamos versiones alternativas del proyecto
- Repositorios ->main,  A: ft/registrar-usuario, B: ft/registrar-cursos, C: ft/matricular-estudiantes, A: bug/fix-registrar-estudiantes

- Un repositorio puede tener muchos branches
Repositorio remoto único
- main(4),  A: ft/registrar-usuario, B: ft/registrar-cursos

Múltiples repositorios locales
- A: main(4), ft/registrar-usuario(basado en la version 3 de main), bug/fix-registrar-estudiantes(basado en la version 4 de main)
- B: main(3), ft/registrar-cursos(basado en la version 3 de main)
- C: main(2), ft/matricular-estudiantes(basado en la version 2 de main)

## Escenario 1: A quiere mergear su branch(ft/registrar-usuario) con main
- Crear un PR(Pull Request) en el repositorio principal: main <- ft/registrar-usuario
- 1: Necesita sincronizar su branch con el main: `git pull origin main` para su branch local desde main(remoto)
- 2: Mergear el main local en el branch local: `git merge main`

## Escenario 2: B quiere mergear su branch(ft/registrar-cursos) con main
- Crear un PR(Pull Request) en el repositorio principal: main <- ft/registrar-cursos
- 1: Necesita sincronizar su branch con el main: `git pull origin main` para su branch local desde main(remoto)
  - Tenemos: ft/registrar-cursos(basado en la version 4 de main)

## Escenario 3: 
- Branch remotos: main(1119b75,1), patronDecorator
- Branch locales: main(1119b75,1), patronDecorator, lc/git-example(1119b75)

alguien modifica el main

- Branch remotos: main(f52ec04,2), patronDecorator
- Branch locales: main(1119b75,1), patronDecorator, lc/git-example(066b656,1'')


Esto simplemente es una prueba de merge

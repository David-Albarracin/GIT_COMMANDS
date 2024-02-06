![git](https://raw.githubusercontent.com/David-Albarracin/README_MATERIALS/main/git.png)

# Comandos Git

Documentación para recordar comandos útiles al momento de crear nuevos repositorios y configurar el entorno de git en nuevos equipos para trabajar en un entorno, Primero configuramos las variables globales iniciando credenciales

* **git config --global user.name "David-Albarracin:" **  Se usa para agregar el nombre de usuario 
* **git config --global user.email "90213684+David-Albarracin@users.noreply.github.com:"**  Se usa para agregar el correo electrónico
* **git config --global --replace-all core.editor "code --wait":"** Se usa para remplasar todos los editores de git y dejar por defecto el vscode la forma corta del comando es git config --global core.editor "code --wait"
* **git config --global init.defaultBranch main:** Se usa para usar la rama principal como main y evitar la rama master ya que esta descontinuada 

Ahora Te muestro unos ejemplos de como crear un archivo con estas configuración para el sistema operativo windows(.BAT) y linux(.SH) para iniciar Credenciales 

#### .BAT

```
@echo off
SETLOCAL EnableDelayedExpansion
set condition=true
git config --global user.name "David-Albarracin" 
git config --global user.email "90213684+David-Albarracin@users.noreply.github.com"
git config --global --replace-all core.editor "code --wait"
git config --global init.defaultBranch main
ENDLOCAL

```

#### .SH

```

```

Procedemos a crear alias para algunos comandos que son extensos y poder llamarlos mas rápidamente cuando sean requeridos para ello usaremos **git config --global alias.(Nombre del alias) "(comando)"** a continuación un ejemplo practico 

```
git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold
blue)%h%C(reset) - %C(bold green) (%ar)%C(reset)%C(white)%s%C(reset)%C(dim
white)-%an%C(reset)%C(bold yellow)%d%C(reset)' --all"
```

* **git config --global:** Este Comando Se utiliza para configurar opciones de git. La opcion (--global) indica que el cambio se aplicara a nivel global, es decir, para todos los repositorios
* **alias.lg: ** Establece un alias llamado "lg" en la configuracion del git
* **log --graph --abbrev-commit --decorate --format=format:'%C(bold
  blue)%h%C(reset) - %C(bold green) (%ar)%C(reset)%C(white)%s%C(reset)%C(dim
  white)-%an%C(reset)%C(bold yellow)%d%C(reset)' --all:"** El comando el cial se ejecuta cuando se hace referencia al comando git lg aqui esta el desglose de formato utilizado en el comando
  * **--graph:** Muestra una presentacion grafica del historial de commits con lineas que indican bifurcaciones y funsiones
  * **--abbrev-commit: ** Muestra el hash del commit abreviado 
  * **--decorate:** Muestra las referencias (ramas o tag) junto a los commits
  * **--format=format:** Define un formato personalizado para la salida del log. La cadena entre comillas simples ('.....') especifica como formatear cada entrada del log
  * **%C(bold blue)%h%C(reset):** Muestra el hash abreviado del commit en azul y negrita
  * **%C(bold green) (%ar)%C(reset):** Muestra la fecha relativa del commit en verde y negrita
  * **%C(white)%s%C(reset):** Muestra el mensaje del commit en blanco
  * **%C(dim white)-%an%C(reset):** Muestra el nombre del auto en blanco con una intensidad redusida 
  * **%C(bold yellow)%d%C(reset):** Muestra las referencias (ramas o tags) en amarillo y negrita



Después de crear las variables globales podemos empezar a trabajar en git para ello creamos una carpeta accedemos a ella e inicializamos git

```
cd Documentos
mkdir GitHub
cd ./GitHub
mkdir comandos_git (Nombre del Proyecto)
cd ./comandos_git (Nombre del Proyecto)
```

Una vez creada las carpetas podremos crear archivos dentro de ella usando **TOUCH NOMBRE.EXTENCION** siguiendo el ejemplo suponiendo que estamos en la ruta ./Documentos/GitHub/comandos-git

```
touch index.html
```

Después de realizar la estructura del proyecto damos inicio al control de versiones con el comando **git init**



## Taller Alias Git

Ahora para practicar algunos comandos vamos a realizar un Taller para ello vamos usar algunas opciones del log en este apartado encontraras la información: 

* **--all:** Se usa para hacer referencia a todas las ramas 
* **--decorate:** Muestra las referencias (ramas o tag) junto a los commits
* **--oneline:** Muestra todo el decorate en una sola linea 
* **--graph:** Muestra una presentacion grafica del historial de commits con lineas que indican bifurcaciones y funsiones
* **--n (numero):** Lista los ultimos n commits 
* **--format=format:** Define un formato personalizado para la salida del log. La cadena entre comillas simples ('.....') especifica como formatear cada entrada del log
* **%C(bold blue)%h%C(reset):** Muestra el hash abreviado del commit en azul y negrita

### Ejemplos:

1. Obtener un resumen gráfico de los últimos 5 commits en todas las ramas

   * **Solucion:** comando implementado (git log --all --decorate --oneline --graph -n 5)

     ```
     git config --global alias.ls5 "log --all --decorate --oneline --graph -n 5"
     ```

2. Esta trabajando en un proyecto Git colaborativo y necesitas obtener una visión gráfica y
   detallada del historial de commits. Tu tarea es utilizar el comando git log con opciones
   específicas para personalizar el formato y presentación de la salida. La salida debe tener
   las siguientes especificaciones:

   * Muestra una representación gráfica del historial de commits

   * Muestra el hash corto del commit en color rojo

   * Muestra las referencias (ramas o tags) en las que está involucrado el commit en color
     amarillo

   * Muestra el mensaje del commit.

   * Muestra la fecha relativa del commit en color verde.

   * Muestra el hash del commit como un identificador abreviado.

   * Muestra las fechas de los commits de forma relativa

   * **Solucion :** comando implementado (git log --graph --abbrev-commit --decorate --format=format:'%C(bold red)%h%C(reset) - %C(bold green) (%ar)%C(reset) - %C(white)%s%C(reset) - %C(dim white)-%an%C(reset) - %C(bold yellow)%d%C(reset)' --all)

     ```
     git config --global alias.lsG5 "log --graph --abbrev-commit --decorate --format=format:'%C(bold red)%h%C(reset) - %C(bold green) (%ar)%C(reset) - %C(white)%s%C(reset) - %C(dim white)-%an%C(reset) - %C(bold yellow)%d%C(reset)' --all"
     ```

3. Estas trabajas frecuentemente con el comando git log -1 HEAD para obtener detalles sobre
   el último commit en la rama actual. Sin embargo, encuentras que escribir este comando
   completo es un poco tedioso. Quieres simplificarlo creando un alias personalizado.

   Tu tarea es utilizar el comando git config para crear un alias llamado last que represente el
   comando git log -1 HEAD.

   + **Solucion:** Comando implementado:  git log -1 HEAD.

     ```
     git config --global alias.last "log -1 HEAD"
     ```

4. Imagina que deseas simplificar el proceso de editar la configuración global de Git. Tu tarea
   es utilizar el comando git config para crear un alias que te permita abrir fácilmente la
   configuración global en tu editor de texto preferido. Ejecuta el comando para crear un alias
   llamado ec que cumpla con la especificación dada.

   + **Solucion:** Comando Implementado: git config --global -e

     ```
     git config --global alias.ec "config --global -e"
     ```

5. Imagina que estás trabajando en un proyecto Git colaborativo con múltiples colaboradores
   y ramas. Tu tarea es utilizar el comando git log con opciones específicas para personalizar
   la salida del historial de commits y resaltar información clave. El resultado de la ejecución
   del comando se debe ve como el ejemplo siguiente:

   + **Solucion:** Comando Implementado git log --graph --abbrev-commit --decorate --format=format:'%C(bold yellow)%h%C(reset)%C(bold red)\ %d\ %C(reset) %C(white)%s%C(reset)%C(blue)\ [%an]%C(reset)' --all

     ```
     git config --global alias.lsFinal "log --graph --abbrev-commit --decorate --format=format:'%C(bold yellow)%h%C(reset)%C(bold red)\ %d\ %C(reset) %C(white)%s%C(reset)%C(blue)\ [%an]%C(reset)' --all"
     ```

     

### Prueba de Verificación :

Prueba ahora  todas las soluciones e implementa estos alias para tener un desarrollo mas ágil en tus proyectos copia y pega esto en tu git bash y presiona enter (Recuerda ubicarte en una carpeta que tenga el git inicializado)

```

git config --global alias.ls5 "log --all --decorate --oneline --graph -n 5"

git config --global alias.lsG5 "log --graph --abbrev-commit --decorate --format=format:'%C(bold red)%h%C(reset) - %C(bold green) (%ar)%C(reset) - %C(white)%s%C(reset) - %C(dim white)-%an%C(reset) - %C(bold yellow)%d%C(reset)' --all"

git config --global alias.last "log -1 HEAD"

git config --global alias.ec "config --global -e"

git config --global alias.lsFinal "log --graph --abbrev-commit --decorate --format=format:'%C(bold yellow)%h%C(reset)%C(bold red)\ %d\ %C(reset) %C(white)%s%C(reset)%C(blue)\ [%an]%C(reset)' --all"

git ls5
git lsG5
git last
git ec
git lsFinal
```
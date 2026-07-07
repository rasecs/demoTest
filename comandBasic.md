# Guía Práctica de Git y GitHub - Desde Básico hasta Nivel Profesional

Esta guía está diseñada para reforzar conceptos y enfocarse en **lo más usado en el día a día** de un desarrollador.

---

## 1. Configuración Inicial

```bash
# Configurar tu identidad (se guarda globalmente)
git config --global user.name "Tu Nombre Completo"
git config --global user.email "tu@email.com"

# Verificar configuración
git config --global --list

# Editor predeterminado para commits (recomendado: VS Code)
git config --global core.editor "code --wait"

# Activar colores en la terminal
git config --global color.ui auto

# Crear un nuevo repositorio local
mkdir mi-proyecto
cd mi-proyecto
git init

# Clonar un repositorio remoto (GitHub, GitLab, etc.)
git clone https://github.com/usuario/proyecto.git
# O con SSH (más cómodo una vez configurado)
git clone git@github.com:usuario/proyecto.git

# Ver estado actual
git status

##############
 Ejemplo 1: Crear un proyecto desde cero y hacer el primer envíoImagina que vas a iniciar una nueva página web en tu computadora. Los comandos se ejecutan en este orden dentro de tu terminal:
 
 git initResultado: Creas el repositorio. Git empieza a vigilar la carpeta de tu proyecto.
 
 git statusResultado: Git te avisa que creaste un archivo llamado index.html pero que aún no está guardado en el historial.
 
 git add index.htmlResultado: Preparas el archivo para la foto. Si tienes muchos archivos nuevos, usas git add ..
 
 git commit -m "Mi primer commit: estructura inicial de la web"Resultado: Guardas la foto en el historial con ese mensaje descriptivo.

#######3
Ejemplo 2: Trabajar en equipo (Subir y bajar cambios)   

git clone https://github.comResultado: Descargas una copia exacta de todo el proyecto a tu computadora para empezar a trabajar.

git clone https://github.comResultado: Descargas una copia exacta de todo el proyecto a tu computadora para empezar a trabajar.

(Haces tus cambios en el código y guardas con git add y git commit)

git pullResultado: Regla de oro antes de subir algo. 

Descargas los cambios que tus compañeros hayan subido mientras tú trabajabas, evitando pisar el trabajo de otros.

git pushResultado: Subes tus nuevos cambios a GitHub para que el resto del equipo pueda verlos y usarlos.

######
Ejemplo 3: Crear una función nueva sin romper lo que ya funcionaQuieres probar un diseño de botón nuevo pero no quieres arruinar la página web que ya está funcionando en producción (rama main).

git branch nuevo-botonResultado: Creas una línea de tiempo paralela llamada "nuevo-boton".

git checkout nuevo-botonResultado: Te mudas a esa línea de tiempo. Todo lo que hagas aquí no afectará a la rama principal.

(Modificas el diseño del botón, haces git add . y luego git commit -m "Diseño de botón moderno")

listar las ramas 
 git branch
  con * estara marcada la rama que estamos actualmente

git checkout main  ##rama principal

##  1. Cambiarlo de forma GLOBAL (Para todos tus proyectos futuros)Si quieres que cada vez que uses git init la rama por defecto se llame main en lugar de master, ejecuta este comando una sola vez en tu terminal:

git config --global init.defaultBranch main)

Cambiarlo en un proyecto LOCAL (Que no has subido a internet)Si estás trabajando en tu computadora y tu rama actual se llama master, cámbiala usando la bandera -m (move/renombrar):Asegúrate de estar posicionado en la rama master:

git checkout master
Usa el código con precaución.Renombra la rama a main:

git branch -m master main

Cambiarlo en un proyecto REMOTO (Que ya está en GitHub/GitLab)Si el repositorio ya existe en internet con la rama master, debes renombrarla tanto en tu computadora como en el servidor siguiendo estos pasos cronológicamente:Renombra tu rama local (igual que en el paso anterior):

git branch -m master main

Usa el código con precaución.Sube la nueva rama main al servidor y establece el rastreo:

git push -u origin main

Usa el código con precaución.Cambia la rama por defecto en la interfaz web:Entra a tu repositorio en GitHub/GitLab desde el navegador.Ve a Settings (Configuración) -> Branches (Ramas).Cambia la rama por defecto ("Default branch") de master a main y guarda los cambios.Borra la vieja rama master del servidor escribiendo en tu terminal:

git push origin --delete master

Resultado: Regresas a la versión segura y estable de tu proyecto. El nuevo botón "desaparece" momentáneamente porque está a salvo en su propia rama.
########
4: Revisar qué has hechoLlevas horas programando y no recuerdas qué archivos modificaste o qué hiciste ayer.

git status

Resultado: Te muestra una lista en rojo con los archivos que modificaste hoy y no has guardado.

git log --onelineResultado: Te muestra una lista compacta y limpia (un commit por línea) de los últimos cambios guardados en los días anteriores.

###########
Cómo se usa git merge (Paso a Paso)Imagina que creaste una rama llamada nuevo-boton, terminaste el diseño y ahora quieres integrarlo a tu rama principal main.Regresa a la rama que va a recibir los cambios (el destino):

git checkout main

Usa el código con precaución.Asegúrate de tener lo último del servidor (por si tus compañeros subieron algo):

git pull

Usa el código con precaución.Fusiona la rama secundaria dentro de tu rama actual:

git merge nuevo-boton

Usa el código con precaución.¡Listo! Los cambios de nuevo-boton ahora forman parte de main.

########3
# Añadir archivos al staging
git add archivo.txt          # un archivo específico
git add .                    # todo (cuidado)
git add -u                   # solo archivos modificados/eliminados

# Hacer commit
git commit -m "Mensaje claro y descriptivo"
# Buenas prácticas de commit:
# - Usa presente ("Añade login")
# - Sé específico
# - No muy largo (máx 50 caracteres en primera línea)

# Ver historial
git log --oneline --graph --all
git log -p                   # ver cambios detallados

##################3

git push: Sube tus commits locales confirmados al repositorio remoto para compartirlos con el equipo.

git pull: Descarga y fusiona automáticamente los últimos cambios del repositorio remoto en tu rama local actual.

pasos para conectarte a un reposutorio

git remote add origin URL_COPIADA_DE_GITHUB

# Guía paso a paso para conectar un repositorio local a GitHub

## 1. Crear el repositorio en GitHub
* Inicia sesión en [GitHub](https://github.com) y haz clic en el botón **New** (Nuevo).
* Escribe un **nombre** para tu repositorio.
* Selecciona si será **Public** (Público) o **Private** (Privado).
* **Importante:** Deja desmarcadas las opciones de *Add a README file*, *Add .gitignore* y *Choose a license*. El repositorio debe estar completamente vacío.
* Haz clic en **Create repository**.
* Copia la **URL HTTPS** del repositorio que aparece en pantalla (ejemplo: `https://github.com`).

## 2. Inicializar el repositorio en la Laptop
* Abre la terminal de tu sistema (Git Bash, CMD, Terminal de macOS/Linux o la consola de VS Code).
* Navega hasta la carpeta de tu proyecto local con el comando `cd`:
  ```bash
  cd "ruta/de/tu/carpeta"
  ```
* Inicializa Git en esa carpeta:
  ```bash
  git init
  ```
* Añade todos tus archivos locales al área de preparación (*staging*):
  ```bash
  git add .
  ```
* Guarda los cambios de forma local con tu primer commit:
  ```bash
  git commit -m "Primer commit"
  ```
* Renombra la rama principal a `main` (el estándar actual de GitHub):
  ```bash
  git branch -M main
  ```

## 3. Vincular y subir a GitHub
* Enlaza tu carpeta local con el repositorio remoto de GitHub (reemplaza `URL_DE_GITHUB` con el enlace que copiaste en el paso 1):
  ```bash
  git remote add origin URL_DE_GITHUB
  ```
* Sube tus archivos locales a GitHub por primera vez:
  ```bash
  git push -u origin main
  ```
* Si la terminal lo solicita, inicia sesión en tu cuenta de GitHub o introduce tu Token de Acceso Personal (PAT) para autorizar la subida.


## 4. Realizar cambios subsecuentes (Actualizar código)
Cada vez que modifiques, agregues o elimines archivos en tu laptop y quieras subirlos a GitHub, sigue estos tres pasos en tu terminal:

1. **Preparar los archivos modificados:**
   ```bash
   git add .
   ```
   *(Si solo quieres subir un archivo específico, usa `git add nombre_del_archivo.ext`)*

2. **Confirmar los cambios localmente:**
   ```bash
   git commit -m "Descripción breve de los cambios realizados"
   ```

3. **Subir los cambios a GitHub:**
   ```bash
   git push
   ```
   *(A partir de la segunda subida, ya no es necesario escribir `origin main`, basta con `git push`)*

---

## 5. Configurar el archivo `.gitignore`
El archivo `.gitignore` le dice a Git qué carpetas o archivos de tu laptop **nunca** debe subir a GitHub (como contraseñas, dependencias pesadas o archivos del sistema).

1. Crea un archivo de texto en la raíz de tu carpeta y nómbralo exactamente: `.gitignore`
2. Ábrelo con tu editor de código y escribe adentro los nombres de los archivos o carpetas que deseas excluir. Ejemplos comunes:
   ```text
   # Excluir la carpeta de dependencias de Node.js
   node_modules/

   # Excluir archivos de configuración del entorno (que contienen contraseñas o claves)
   .env
   config.json

   # Excluir archivos temporales del sistema operativo
   .DS_Store
   Thumbs.db
   ```
3. Guarda el archivo `.gitignore` y súbelo a GitHub usando el flujo de cambios subsecuentes del punto anterior (`git add .`, `git commit`, `git push`).

---

## 6. Crear el archivo `README.md`
El archivo `README.md` es la portada de tu proyecto en GitHub. Es lo primero que la gente ve al visitar tu repositorio y sirve para explicar de qué trata tu código.

1. Crea un archivo en la raíz de tu carpeta llamado exactamente: `README.md`
2. Puedes usar una estructura estándar como esta para documentar tu proyecto:
   ```markdown
   # Nombre de tu Proyecto o Repositorio

   Una descripción breve y directa de lo que hace este proyecto.

   ## 🚀 Características
   * Característica 1
   * Característica 2

   ## 🛠️ Requisitos e Instalación
   Instrucciones paso a paso para ejecutar el proyecto en otra laptop:
   ```bash
   # Clonar el proyecto
   git clone https://github.com
   ```

   ## ✒️ Autor
   * **Tu Nombre** - [Tu GitHub](https://github.com)
   ```
3. Guarda el archivo y súbelo a GitHub con los comandos de actualización normales.
Usa el código con prec


####
ara solucionar este conflicto y poder subir tu código, debes traer los archivos de GitHub a tu laptop, fusionarlos y luego volver a intentar la subida. Sigue estos pasos en tu terminal:

1. **Forzar la descarga y fusión de los archivos remotos:**
   Como tu repositorio local y el de GitHub no comparten un historial común todavía (porque se crearon por separado), debes usar el parámetro `--allow-unrelated-histories` ejecutando:
   ```bash
   git pull origin main --allow-unrelated-histories
   ```

2. **Resolver el mensaje de confirmación (si aparece):**
   * Al ejecutar el comando anterior, es muy probable que se abra un editor de texto en la terminal (como Vim o Nano) pidiéndote un mensaje para el "Merge".
   * **Si se abre Vim (pantalla con líneas amarillas o texto raro):** Presiona la tecla `Esc`, luego escribe `:wq` y presiona `Enter` para guardar y salir.
   * **Si estás en VS Code:** Simplemente cierra la pestaña del mensaje que se haya abierto.

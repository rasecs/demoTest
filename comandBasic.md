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
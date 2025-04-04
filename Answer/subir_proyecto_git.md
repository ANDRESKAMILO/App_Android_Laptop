### Prompt_1: VsCode-COPILOT EDITS Edit / Claude 3.5 Sonnet
Te ayudaré con los pasos para subir tu carpeta local a GitHub como un nuevo proyecto.

Pasos a seguir:

1. Crear una cuenta en GitHub (si aún no tienes una):

	- Ve a GitHub.com
	- Haz clic en "Sign up" y sigue el proceso de registro
2. Instalar Git en tu computadora (si aún no lo tienes):

	- Descarga Git desde git-scm.com
	- Ejecuta el instalador y sigue las instrucciones por defecto
	- Verifica la instalación abriendo una terminal y escribiendo: git --version
3. Configurar Git con tus credenciales:

	```bash
	   git config --global user.name "Tu Nombre"
	   git config --global user.email "tu.email@ejemplo.com"
	```

Te ayudaré con los pasos para subir tu carpeta local a GitHub como un nuevo proyecto.

Pasos a seguir:

4. Crear una cuenta en GitHub (si aún no tienes una):
   - Ve a [GitHub.com](https://github.com)
   - Haz clic en "Sign up" y sigue el proceso de registro

5. Instalar Git en tu computadora (si aún no lo tienes):
   - Descarga Git desde [git-scm.com](https://git-scm.com/downloads)
   - Ejecuta el instalador y sigue las instrucciones por defecto
   - Verifica la instalación abriendo una terminal y escribiendo: `git --version`

6. Configurar Git con tus credenciales:
   ```bash
   git config --global user.name "Tu Nombre"
   git config --global user.email "tu.email@ejemplo.com"
   ```

7. Crear un nuevo repositorio en GitHub:
   - Inicia sesión en GitHub
   - Haz clic en el botón "+" en la esquina superior derecha
   - Selecciona "New repository"
   - Nombra tu repositorio como "App_Android_Laptop"
   - Deja la opción "Public" seleccionada
   - No inicialices el repositorio con ningún archivo
   - Haz clic en "Create repository"

8. Inicializar el repositorio local y subir los archivos:
   - Abre una terminal
   - Navega hasta tu carpeta:
     ```bash
     cd "C:\Users\Andres B\Desktop\GIT\App_Android_Laptop"
     ```
   - Inicializa el repositorio:
     ```bash
     git init
     git add .
     git commit -m "Initial commit"
     ```
   - Conecta tu repositorio local con GitHub:
     ```bash
     git remote add origin https://github.com/TU_USUARIO/App_Android_Laptop.git
     git branch -M main
     git push -u origin main
     ```

9. Verificar:
   - Ve a tu cuenta de GitHub
   - Deberías ver tu repositorio "App_Android_Laptop" con todos los archivos

Notas importantes:
- Reemplaza "TU_USUARIO" con tu nombre de usuario de GitHub
- Si es la primera vez que usas Git con GitHub, te pedirá autenticarte
- Si tienes archivos grandes (>100MB), necesitarás usar Git LFS
- Asegúrate de no subir información sensible (contraseñas, tokens, etc.)

¿Necesitas ayuda con algún paso específico?


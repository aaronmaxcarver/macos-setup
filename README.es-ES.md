

# macos-setup

**Configuración de fábrica --> Uso diario**

### Contenido
- [Configuración de Cursor (VS Code) - Python, TypeScript/NextJS](https://github.com/aaronmaxcarver/macos-setup/blob/main/README.md#cursor-vs-code-settings)
- [homebrew](https://github.com/aaronmaxcarver/macos-setup/tree/main?tab=readme-ov-file#homebrew)
- [Configuración de Shell](https://github.com/aaronmaxcarver/macos-setup/tree/main?tab=readme-ov-file#shell-setup)
- [AWS CLIv2](https://github.com/aaronmaxcarver/macos-setup/tree/main?tab=readme-ov-file#aws-cliv2)
- [Claves SSH](https://github.com/aaronmaxcarver/macos-setup/tree/main?tab=readme-ov-file#ssh-keys)
- [Python](https://github.com/aaronmaxcarver/macos-setup/tree/main?tab=readme-ov-file#python-1)
- [Node/JavaScript/TypeScript](https://github.com/aaronmaxcarver/macos-setup/blob/main/README.md#nodejavascripttypescript)

### Otros Documentos
- [configuración inicial](https://github.com/aaronmaxcarver/macos-setup/blob/main/initial_setup.md)
- [mantenimiento mensual](https://github.com/aaronmaxcarver/macos-setup/blob/main/monthly_maintenance.md)

---

## Configuración de Cursor (VS Code)
- Almacénalo en `.vscode/settings.json`

### Python
- [Configuración de Ruff para VS Code](https://github.com/astral-sh/ruff-vscode/blob/main/README.md#configuring-vs-code)
```json
{
  "[python]": {
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll": "explicit",
      "source.organizeImports": "explicit"
    },
    "editor.defaultFormatter": "charliermarsh.ruff"
  },
  "notebook.formatOnSave.enabled": true,
  "notebook.codeActionsOnSave": {
    "notebook.source.organizeImports": "explicit"
  },
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "workbench.activityBar.orientation": "vertical",
  "editor.wordWrap": "on",
  "better-comments.tags": [
    {
      "tag": "dev",
      "color": "#542F00", // Marrón oscuro
      "strikethrough": false,
      "underline": false,
      "backgroundColor": "#FFEB3B", // Amarillo brillante
      "bold": true,
      "italic": false
    },
    {
      "tag": "todo",
      "color": "#1565C0", // Azul profundo
      "strikethrough": false,
      "underline": false,
      "backgroundColor": "#90CAF9", // Azul medio
      "bold": true,
      "italic": false
    },
    {
      "tag": "note",
      "color": "#42A5F5", // Azul brillante
      "strikethrough": false,
      "underline": false,
      "backgroundColor": "transparent",
      "bold": false,
      "italic": true
    },
    {
      "tag": "tmp",
      "color": "#8D6E63", // Marrón cálido
      "strikethrough": false,
      "underline": false,
      "backgroundColor": "#EFEBE9", // Taupe muy claro
      "bold": false,
      "italic": true
    },
    {
      "tag": "working",
      "color": "#1B5E20", // Verde oscuro
      "strikethrough": false,
      "underline": false,
      "backgroundColor": "#A5D6A7", // Verde claro
      "bold": true,
      "italic": false
    }
  ],
  "python.testing.pytestArgs": ["app"],
  "python.testing.unittestEnabled": false,
  "python.testing.pytestEnabled": true
}
```

### NextJS TypeScript
```json
{
  "editor.codeActionsOnSave": {
    "source.organizeImports": "explicit"
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "typescript.tsdk": "node_modules/typescript/lib",
  "[json]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode",
    "editor.formatOnSave": true
  },
  "workbench.activityBar.orientation": "vertical",
  "editor.wordWrap": "on"
}
```
### IAC
```json
{
  // igual que Python, pero añade etiquetas YAML personalizadas para AWS CloudFormation:
  "yaml.customTags": [
    "!Base64 scalar",
    "!Cidr scalar",
    "!And sequence",
    "!Equals sequence",
    "!If sequence",
    "!Not sequence",
    "!Or sequence",
    "!Condition scalar",
    "!FindInMap sequence",
    "!GetAtt scalar",
    "!GetAtt sequence",
    "!GetAZs scalar",
    "!ImportValue scalar",
    "!Join sequence",
    "!Select sequence",
    "!Split sequence",
    "!Sub scalar",
    "!Transform mapping",
    "!Ref scalar"
  ]
}
```

## `homebrew`
0. Listar instalaciones actuales:
- Fórmulas
  - Principales - `brew leaves`
  - Todas - `brew list`
- Casks (todas son principales) - `brew list --cask`
1. Instalar [homebrew](https://brew.sh/)
2. Actualizar homebrew
```sh
brew update
```
3. Instalar [fórmulas de brew](https://formulae.brew.sh/)
```sh
brew install \
  asitop \
  awscli \
  cfn-lint \
  cocoapods \
  dopplerhq/cli/doppler \
  ffmpeg \
  gh \
  gnupg \
  graphviz \
  htop \
  just \
  libmagic \
  mongodb-atlas-cli \
  node \
  openapi-generator \
  pnpm \
  rbenv \
  redis \
  ripgrep \
  ruby-build \
  rust \
  stripe/stripe-cli/stripe \
  swiftformat \
  temporal \
  uv \
  watchman \
  xcbeautify \
  xcode-build-server \
  yarn \
  zsh
```
```sh
brew tap mobile-dev-inc/tap
brew install maestro
```
4. Instalar [casks de brew](https://formulae.brew.sh/cask/)
```sh
brew install --cask \
  android-platform-tools \
  android-studio \
  claude \
  cursor \
  docker \
  discord \
  firefox \
  github \
  google-chrome \
  logitech-camera-settings \
  mongodb-compass \
  mosaic \
  neo4j \
  nordvpn \
  notunes \
  ollama \
  pgadmin4 \
  postman \
  qgis \
  swiftformat-for-xcode \
  slack \
  visual-studio-code \
  zoom \
  zulu@17
```
5. Repositorios (taps) de brew
- MongoDB
  - tap - [github.com/mongodb/homebrew-brew](https://github.com/mongodb/homebrew-brew)
  - [Documentación de Database Tools](https://www.mongodb.com/docs/database-tools/)
```sh
brew tap mongodb/brew
brew install mongodb-database-tools
```
6. Instalaciones sin brew
- Instalar Xcode desde la App Store de Apple
  - después de instalar, abre Xcode y añade el soporte de plataforma para iOS, ej. "iOS 18.2, 8.72 GB"
  - ejecuta `xcode-select -p` para verificar la ruta de instalación, debería responder algo como `/Library/Developer/CommandLineTools`
  - abre Xcode y en la barra de menú selecciona "Xcode" > "Ajustes" > pestaña "Ubicaciones". Ahora en el menú desplegable "Herramientas de línea de comandos", aunque ya tenga un valor, haz clic de nuevo (¡¿qué!?¿) y autentifícate para habilitarlo. 
- Android Studio - sigue las instrucciones aquí https://reactnative.dev/docs/set-up-your-environment y usa la información a continuación como ayuda
  - Java Development Kit (JDK) - instalar mediante el script de homebrew anterior
    - luego, al actualizar `.zshrc`, coloca `JAVA_HOME=/Library/Java/JavaVirtualMachines/zulu-17.jdk/Contents/Home` justo debajo de `# User configuration`
    - luego reinicia la terminal o ejecuta `source ~/.zshrc`, después ejecuta `echo $JAVA_HOME` y verifica que la salida coincida con el valor de `.zshrc`, ej. `/Library/Java/JavaVirtualMachines/zulu-17.jdk/Contents/Home`
  - Android Studio - instalar mediante el script de homebrew anterior
    - ayuda para verificar la ruta después de añadir lo de Android Studio `echo $PATH | tr ":" "\n"`
7. Configurar programas
- Abre cada programa, añádelo al dock, inicia sesión, configura los ajustes, etc.
- Configurar elementos de inicio de sesión
  - Ajustes > General > Elementos de inicio > añadir noTunes

## Configuración del Shell
- Instalar [oh my zsh](https://ohmyz.sh/#install)
```sh
open ~/.zshrc
```
- en `.zshrc`, establece:
```sh
ZSH_THEME="agnoster"
```
- Añade esto al final del archivo:
```sh
# Eliminar nombre de usuario y host
prompt_context() {}
```
- Ver configuración
```sh
open ~/.zprofile
open ~/.zshrc
open ~/.bash_profile
open ~/.bashrc
open ~/.profile
```

## AWS CLIv2

### Configurar
- Ver configuración y demás
```sh
open ~/.aws
```
- SSO (requiere la creación de una cuenta SSO por parte del administrador de AWS)
  - Abrir `config`
  - Obtén la configuración de Aaron, se verá como lo siguiente:
```
# Documentación de AWS CLI + SSO - https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html
# En AWS IAM Identity Center, los conjuntos de permisos se heredan por asignación directa o pertenencia a grupo
# Para "sso_role_name", especifica cualquier conjunto de permisos al que el usuario tenga acceso
## {cuenta}--{conjunto_de_permisos}

# Sesión
[sso-session chrt]
sso_start_url = https://chrt.awsapps.com/start/#
sso_region = us-east-1
sso_registration_scopes = sso:account:access

# Perfiles
## Desarrollo (Dev)
[profile workloads-dev--PowerUserAccess]
sso_session = chrt
sso_account_id = REDACTED
sso_role_name = PowerUserAccess
region = us-east-1
output = json
## Preproducción (Staging)
[profile workloads-staging--PowerUserAccess]
sso_session = chrt
sso_account_id = REDACTED
sso_role_name = PowerUserAccess
region = us-east-1
output = json
## Producción (Prod)
[profile workloads-prod--PowerUserAccess]
sso_session = chrt
sso_account_id = REDACTED
sso_role_name = PowerUserAccess
region = us-east-1
output = json
## Entorno aislado (Sandbox)
[profile workloads-sandbox--PowerUserAccess]
sso_session = chrt
sso_account_id = REDACTED
sso_role_name = PowerUserAccess
region = us-east-1
output = json
```
- Clave de acceso (no recomendado, funciona para cualquier cuenta de AWS, no requiere que el admin cree una cuenta SSO)
```sh
# configurar
aws configure
# ingresar clave de acceso
# ingresar clave secreta
# ingresar `us-east-1`
# ingresar `json`
```

### Inicio de sesión
- Iniciar sesión en SSO
```sh
# usa el nombre de `sso-session` de `cat ~/.aws/config`
aws sso login --sso-session prod
```
- Usar un perfil con nombre para una sesión de shell
```sh
# establece la variable de entorno con el nombre de `profile` de `cat ~/.aws/config`
export AWS_PROFILE=PowerUserAccess-012345678901
# luego usa comandos CLI
aws sts get-caller-identity
aws s3 ls # no imprimirá nada si la cuenta no tiene elementos S3
```

### Inspeccionar la configuración de AWS CLI
```sh
# ver configuración y credenciales
open ~/.aws/config
open ~/.aws/credentials
# Probar qué cuenta se está usando
aws sts get-caller-identity
```

## Claves SSH
- Sigue las instrucciones. Es un poco complicado la primera vez, pero en general no está tan mal. 
  - [Generar una nueva clave SSH y agregarla al ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Sube la clave pública a los servicios según sea necesario, ej.:
  - GitHub - https://github.com/settings/keys
  - HuggingFace - https://huggingface.co/settings/keys


## Python

### `uv` - gestión de paquetes y entornos virtuales
- [Documentación](https://docs.astral.sh/uv/)
  - Ahora uso `uv` y creo que es lo mejor... ni `conda`, ni `pipenv` ni `poetry`, aunque apreciaba esas en el pasado
- Instala la fórmula de `homebrew` `uv` si no está instalada (`brew install uv`)
- Recomendado: lee la documentación de `uv` para encontrar instrucciones según tu caso de uso
  - Para gestionar un `venv` para un repositorio específico, consulta la documentación de [Proyectos](https://docs.astral.sh/uv/concepts/projects/#creating-projects)
    - Básicamente: ve al directorio base del repositorio y ejecuta `uv init`
    - También ejecuta `uv sync` si ya existe un `pyproject.toml`
- `uv` utiliza un archivo `pyproject.toml`: aquí está la [documentación oficial](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/)
  - Me pareció que la documentación era demasiado extensa para un uso básico. No conozco una buena introducción breve
- Comandos comunes de `uv` (donde [`requests`](https://pypi.org/project/requests/) es el nombre de un paquete de PyPI):
  ```sh
  uv add requests
  uv remove requests
  ```
- ¿Qué venv está activo?
  ```sh
  echo $VIRTUAL_ENV
  ```

  
### Ruff - linting y formateo
- [Documentación](https://docs.astral.sh/ruff/)
- Extensión de VS Code [`README`](https://github.com/astral-sh/ruff-vscode/blob/main/README.md)
- Activa "Formatear al guardar" usando la Configuración de VS Code
- Comandos CLI comunes:
  ```sh
  # linting
  ruff check
  ruff check --fix
  # formateo
  ruff format
  # ordenar importaciones
  ruff check --select I --fix
  ```
- Desactivar/activar en el código usando comentarios mágicos
  ```py
  # fmt: on 
  # fmt: off
  # fmt: skip 
  ```

### Cuadernos Jupyter - importaciones relativas
- Habilitar que los Cuadernos Jupyter usen importaciones relativas ([leer más](https://discourse.jupyter.org/t/how-can-i-pass-environment-variabel-pythonpath-to-jupyter-notebook/7351/2))
- 
```sh
uv run jupyter kernelspec list
# salida: python3    /Users/aaron/github/chrt-inc/chrt-fastapi/.venv/share/jupyter/kernels/python3
```
- Añade display_name, PYTHONPATH y ENVIRONMENT, ej.:
```sh
{
  "argv": ["python", "-m", "ipykernel_launcher", "-f", "{connection_file}"],
  "display_name": "chrt-fastapi",
  "env": {
    "PYTHONPATH": "/Users/aaron/github/chrt-inc/chrt-fastapi",
  },
  "language": "python",
  "metadata": {
    "debugger": true
  }
}
```
- Después de un cambio, recarga la ventana. A veces VS Code no sincroniza el cambio por un momento.
  - desde VS Code ejecuta: cmd + shift + p, Developer: Reload Window


## Node/JavaScript/TypeScript
- [Node](https://nodejs.org/en) (vía el comando `brew` anterior)
- [pnpm](https://pnpm.io/) (vía el comando `brew` anterior)

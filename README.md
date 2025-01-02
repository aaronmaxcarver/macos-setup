# macos-setup

**Factory settings --> Daily driver**

## VS Code Settings
- Store in `.vscode/settings.json`

### Python
- [Ruff vs code config](https://github.com/astral-sh/ruff-vscode/blob/main/README.md#configuring-vs-code)
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
  }
}
```

### NextJS TypeScript
```json
{
  "typescript.tsdk": "node_modules/typescript/lib"
}
```

## `homebrew`
1. Install [homebrew](https://brew.sh/)
2. Update homebrew
```sh
brew update
```
3. Install [brew formulae](https://formulae.brew.sh/)
```sh
brew install \
  asitop \
  awscli \
  cfn-lint \
  cocoapods \
  expo-orbit \
  fastlane \
  ffmpeg \
  graphviz \
  htop \
  mongodb-atlas-cli \
  pnpm \
  quarto \
  redis \
  rust \
  uv \
  watchman \
  zsh
```
4. Install [brew casks](https://formulae.brew.sh/cask/)
```sh
brew install --cask \
  android-platform-tools \
  docker \
  discord \
  firefox \
  github \
  mongodb-compass \
  mosaic \
  neo4j \
  notunes \
  ollama \
  pgadmin4 \
  postman \
  slack \
  snowflake-snowsql \
  visual-studio-code \
  zoom \
  zulu@17
```
5. Non-brew installs
- Android Studio per https://reactnative.dev/docs/set-up-your-environment
7. Setup programs
- Open each program, add to dock, log in, configure settings, etc.
- Set Login Items
  - Settings > General > Login Items > add noTunes, Mosaic


## Shell setup
- Install [oh my zsh](https://ohmyz.sh/#install)
```
open ~/.zshrc
# set:
ZSH_THEME="agnoster"
# Add these aliases:
alias py='python'
alias ty='typer'
# Add this to the end of the file:
# Remove username and hostname 
prompt_context() {}
```
- See setup
```sh
open ~/.zprofile
open ~/.zshrc
open ~/.bash_profile
open ~/.bashrc
open ~/.profile
```

## AWS CLIv2

### Configure
- View config and such
```sh
open ~/.aws
```
- Option 1: SSO (recommended)
  - requires SSO account creation by AWS admin
```sh
aws configure sso
$ SSO session name: `staging`
$ SSO Start URL: like this - `https://chrt.awsapps.com/start/#`
$ SSO region: `us-east-1`
$ SSO registration scopes: leave as is
# Browser automatically prompts sign in
# After sign in, you may see "There are x AWS accounts available to you."
# Choose the appropriate account, probably "Staging"
# You may also be prompted to pick a role - choose the appropriate one
$ CLI default client Region: `us-east-1`
$ CLI default output format: `json`
$ CLI profile name: leave as is
```
- Option 2: Access Key (not recommended)
  - this works for any AWS account
```sh
# configure
aws configure
# input access key
# input secret key
# input `us-east-1`
# input `json`
```

### Login
- Log in to SSO
```sh
# use the `sso-session` name from `cat ~/.aws/config`
aws sso login --sso-session prod
```
- Use a named profile for a shell session
```sh
# set env var to the `profile` name from `cat ~/.aws/config`
export AWS_PROFILE=PowerUserAccess-012345678901
# then use CLI commands
aws sts get-caller-identity
aws s3 ls # will print nothing if the account has no S3 items
```

### Inspect AWS CLI configuration
```sh
# view config and credentials
open ~/.aws/config
open ~/.aws/credentials
# Test which account is being used
aws sts get-caller-identity
```

## SSH keys
- Follow the instructions. It's a bit tricky the first time, but overall not so bad. 
  - [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Upload public key to services as needed, e.g.:
  - GitHub - https://github.com/settings/keys
  - HuggingFace - https://huggingface.co/settings/keys


## Python

### `uv` - manage packages and virtual environments
- [Docs](https://docs.astral.sh/uv/)
  - I now use `uv` and think it's the very best...not `conda` or `pipenv` or `poetry`, though I appreciated those in the past
- Install the `homebrew` fomulae `uv` if it's not already installed (`brew install uv`)
- Recommended: read through the `uv` docs to find instructions for your use case
  - For managing a `venv` for a particular repo, see the [Projects](https://docs.astral.sh/uv/concepts/projects/#creating-projects) docs
    - Basically - go to the repo's base directory and run `uv init`
    - Also run `uv sync` if there's already a `pyproject.toml`
- `uv` uses a `pyproject.toml` file - here's the official [docs](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/)
  - I found the docs to be overly verbose for basic usage. I don't know of a good brief intro
- Common `uv` commands (where [`requests`](https://pypi.org/project/requests/) is a PyPI package name):
  ```sh
  uv add requests
  uv remove requests
  ```
- Which venv is active?
  ```sh
  echo $VIRTUAL_ENV
  ```

  
### Ruff - linting and formatting
- [Docs](https://docs.astral.sh/ruff/)
- VS Code Extension [`README`](https://github.com/astral-sh/ruff-vscode/blob/main/README.md)
- Turn on "Format on Save" using VS Code Settings
- Common CLI commands:
  ```sh
  # lint
  ruff check
  ruff check --fix
  # format
  ruff format
  # sort imports
  ruff check --select I --fix
  ```
- Turn off/on in code using magic comments
  ```py
  # fmt: on 
  # fmt: off
  # fmt: skip 
  ```

### Jupyter Notebooks - relative imports
- Enable Jupyter Notebooks to use relative imports ([read more](https://discourse.jupyter.org/t/how-can-i-pass-environment-variabel-pythonpath-to-jupyter-notebook/7351/2))
```sh
# find the path to the kernel spec file
jupyter kernelspec list
# open that file and add env vars for PYTHONPATH and ENVIRONMENT, e.g.:
"env": {
  "PYTHONPATH": "/Users/aaronmaxcarver/GitHub/aaron-repo-name/",
  "ENVIRONMENT": "DEV"
  },
# Rename the kernel for convenience, e.g.:
"display_name": "aaron-repo-name",
# After a change, reload the window. Sometimes VS Code just won't sync the change for a bit. 
cmd + shift + p, Developer: Reload Window
```


## Node (JavaScript)
- [Node](https://nodejs.org/en) (via `brew` command above)
- [pnpm](https://pnpm.io/) (via `brew` command above)


## Initial Setup
- Connect mouse and/or keybaord (need wired or Apple brand ones) > Sign in to wifi and Apple ID > Create MacOS user
- Tinker with the screen(s) settings, mouse settings, etc. as desired
  - Settings > Displays >
    - set up dual screen w/ max resolution
    - Night Shift > Sunset to Sunrise + Color Temperature to full warm
  - Settings > Mouse >
    - Tracking Speed > maximum fast, Natural Scrolling > off, Secondary Click > Click Right Side, Smart Zoom > On
  - Settings > Desktop & Dock > set "Click wallpaper to reveal desktop" to "Only in Stage Manager"
  - Settings > Keyboard > Dictation > enable
  - Settings > Lock Screen >
    - Start Screen Saver when inactive > "For 1 hour", Turn display off when inactive > "For 1 hour", Require password ... > "Immediately"
- Download Google Chrome > Sign in to Google Account > Visit the bookmark for this page > Sign in to GitHub


## Maintenance (~1st day of each month)

### Backups e.g. to Google Drive [Backups folder](https://drive.google.com/drive/u/0/folders/1ZPrKNiOxw9zRAG6sz0WC9L2u2Um3CaLq)
- Chrome bookmarks - go to chrome://bookmarks/ > snowman at top right > export bookmarks > save file > save to backup location(s)
- Google Contacts - go to [https://contacts.google.com](contacts.google.com) > export button > save file > save to backup location(s)
- Code - go to a GitHub repo > Code button > Download zip > save to backup location(s)

### Credentials
- Collect credentials into an encrypted drive and backup
  - Create a credential folder > add all new credentials
  - Open the existing encrypted credentials `dmg` > add those files to the new credentials folder
  - Open `Disk Utility` > File > New Image > Image from folder
  - Select the new credentials folder > choose Encryption type of "256-bit AES ..." > enter password
  - Open the new encrypted `dmg` to ensure the password was set correctly
  - Copy the new `.dmg` to backup location(s)
  - Delete all plaintext credentials files

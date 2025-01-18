# macos-setup

**Factory settings --> Daily driver**

### Contents
- [Cursor (VS Code) Settings - Python, Typescript/NextJS](https://github.com/aaronmaxcarver/macos-setup/blob/main/README.md#cursor-vs-code-settings)
- [homebrew](https://github.com/aaronmaxcarver/macos-setup/tree/main?tab=readme-ov-file#homebrew)
- [Shell setup](https://github.com/aaronmaxcarver/macos-setup/tree/main?tab=readme-ov-file#shell-setup)
- [AWS CLIv2](https://github.com/aaronmaxcarver/macos-setup/tree/main?tab=readme-ov-file#aws-cliv2)
- [ssh keys](https://github.com/aaronmaxcarver/macos-setup/tree/main?tab=readme-ov-file#ssh-keys)
- [Python](https://github.com/aaronmaxcarver/macos-setup/tree/main?tab=readme-ov-file#python-1)
- [Node/JavaScript/TypeScript](https://github.com/aaronmaxcarver/macos-setup/blob/main/README.md#nodejavascripttypescript)

### Other Docs
- [initial setup](https://github.com/aaronmaxcarver/macos-setup/blob/main/initial_setup.md)
- [monthly maintenance](https://github.com/aaronmaxcarver/macos-setup/blob/main/monthly_maintenance.md)

---

## Cursor (VS Code) Settings
- Store in `.vscode/settings.json`

### Python
- [Ruff vs code config](https://github.com/astral-sh/ruff-vscode/blob/main/README.md#configuring-vs-code)
```json
{
  "editor.codeActionsOnSave": {
    "source.organizeImports": "explicit",
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
  "workbench.activityBar.orientation": "vertical",
  "editor.wordWrap": "on"
}
```

### NextJS TypeScript
```json
{
  "editor.codeActionsOnSave": {
    "source.organizeImports": "explicit",
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
  "workbench.activityBar.orientation": "vertical"
}
```

## `homebrew`
0. List current installs:
- Formulae
  - Top-level - `brew leaves`
  - All - `brew list`
- Casks (all are top-level) - `brew list --cask`
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
  node \
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
  notunes \
  ollama \
  pgadmin4 \
  postman \
  slack \
  visual-studio-code \
  zoom
```
5. Non-brew installs
- Android Studio per https://reactnative.dev/docs/set-up-your-environment
6. Setup programs
- Open each program, add to dock, log in, configure settings, etc.
- Set Login Items
  - Settings > General > Login Items > add noTunes
- For BentoBox, go to Settings > Desktop & Dock > turn off these: "Drag windows to scren edges to tile", "Drag windows to menu bar to fill screen", "Hold option key while dragging windows to tile", "Tiled windows have margins"

## Shell setup
- Install [oh my zsh](https://ohmyz.sh/#install)
```
open ~/.zshrc
# set:
ZSH_THEME="agnoster"
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


## Node/JavaScript/TypeScript
- [Node](https://nodejs.org/en) (via `brew` command above)
- [pnpm](https://pnpm.io/) (via `brew` command above)





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
  "editor.wordWrap": "on"
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
  // same as python, but also add custom YAML tags for AWS CloudFormation:
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
  stripe/stripe-cli/stripe \
  uv \
  watchman \
  zsh
```
4. Install [brew casks](https://formulae.brew.sh/cask/)
```sh
brew install --cask \
  android-platform-tools \
  claude \
  cursor \
  docker \
  discord \
  firefox \
  github \
  google-chrome \
  insomnia \
  logitech-camera-settings \
  mongodb-compass \
  mosaic \
  neo4j \
  nordvpn \
  notunes \
  ollama \
  pgadmin4 \
  postman \
  slack \
  visual-studio-code \
  zoom
```
5. brew taps
- MongoDB
  - tap - [github.com/mongodb/homebrew-brew](https://github.com/mongodb/homebrew-brew)
  - [Database Tools docs](https://www.mongodb.com/docs/database-tools/)
```sh
brew tap mongodb/brew
brew install mongodb-database-tools
```
6. Non-brew installs
- Android Studio per https://reactnative.dev/docs/set-up-your-environment
7. Setup programs
- Open each program, add to dock, log in, configure settings, etc.
- Set Login Items
  - Settings > General > Login Items > add noTunes

## Shell setup
- Install [oh my zsh](https://ohmyz.sh/#install)
```sh
open ~/.zshrc
```
- in `.zshrc`, set:
```sh
ZSH_THEME="agnoster"
```
- Add this to the end of the file:
```sh
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
- SSO (requires SSO account creation by AWS admin)
  - Open `config`
  - Get the config from Aaron - it will look like the below:
```
# AWS CLI + SSO Docs - https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html
# In AWS IAM Identity Center, permission sets are inherited by direct assignment or group membership
# For "sso_role_name", specify any permission set that a user has access to
## {account}--{permission_set}

# Session
[sso-session chrt]
sso_start_url = https://chrt.awsapps.com/start/#
sso_region = us-east-1
sso_registration_scopes = sso:account:access

# Profiles
## Dev
[profile workloads-dev--PowerUserAccess]
sso_session = chrt
sso_account_id = REDACTED
sso_role_name = PowerUserAccess
region = us-east-1
output = json
## Staging
[profile workloads-staging--PowerUserAccess]
sso_session = chrt
sso_account_id = REDACTED
sso_role_name = PowerUserAccess
region = us-east-1
output = json
## Prod
[profile workloads-prod--PowerUserAccess]
sso_session = chrt
sso_account_id = REDACTED
sso_role_name = PowerUserAccess
region = us-east-1
output = json
## Sandbox
[profile workloads-sandbox--PowerUserAccess]
sso_session = chrt
sso_account_id = REDACTED
sso_role_name = PowerUserAccess
region = us-east-1
output = json
```
- Access Key (not recommended, works for any AWS account, does not require SSO account created by admin)
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
# Add display_name, PYTHONPATH, and ENVIRONMENT, e.g.:
  "display_name": "aaron-repo-name",
  "env": {
    "PYTHONPATH": "/Users/aaron/code/pai",
    "ENVIRONMENT": "LOCAL"
  },
# After a change, reload the window. Sometimes VS Code just won't sync the change for a bit. 
cmd + shift + p, Developer: Reload Window
```


## Node/JavaScript/TypeScript
- [Node](https://nodejs.org/en) (via `brew` command above)
- [pnpm](https://pnpm.io/) (via `brew` command above)





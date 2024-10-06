# macos-setup


## Maintenance
### Routine (~1st day of each month)
- Backup code to secondary storage
  - e.g. Google Drive [Backups folder](https://drive.google.com/drive/u/0/folders/1ZPrKNiOxw9zRAG6sz0WC9L2u2Um3CaLq)
- Backup Chrome bookmarks
  - go to [chrome://bookmarks/](chrome://bookmarks/) > snowman at top right > export bookmarks > save file > add to secondary storage
    - e.g. Google Drive [Backups folder](https://drive.google.com/drive/u/0/folders/1ZPrKNiOxw9zRAG6sz0WC9L2u2Um3CaLq)
- Collect credentials into an encrypted drive and backup
  - Create a credential folder > add all new credentials
  - Open the existing encrypted credentials `dmg` > add those files to the new credentials folder
  - Open `Disk Utility` > File > New Image > Image from folder
  - Select the new credentials folder > choose Encryption type of "256-bit AES ..." > enter password
  - Open the new encrypted `dmg` to ensure the password was set correctly
  - Copy the new `.dmg` to secondary storage
    - e.g. Google Drive [Backups folder](https://drive.google.com/drive/u/0/folders/1ZPrKNiOxw9zRAG6sz0WC9L2u2Um3CaLq)
  - Delete all plaintext credentials files


## Setup - programs, shell, IDE, SSH keys
**Factory settings --> Daily driver**


### First steps
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


### `homebrew`
1. Install [homebrew](https://brew.sh/)
2. Update homebrew
```sh
brew update
```
3. Install [brew formulae](https://formulae.brew.sh/)
```sh
brew install \
  awscli \
  cfn-lint \
  graphviz \
  mongodb-atlas-cli \
  node@22 \
  quarto \
  redis \
  uv \
  zsh
```
4. Install [brew casks](https://formulae.brew.sh/cask/)
```sh
brew install --cask \
  cloudflare-warp \
  docker \
  discord \
  mongodb-atlas \
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
  zotero
```
5. Setup programs
- Open each program, add to dock, log in, configure settings, etc.
- Set Login Items
  - Settings > General > Login Items > add noTunes, Mosaic


### Shell
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

### AWS CLIv2

#### Configure
- Option 1: SSO (recommended)
  - you'll need to have your AWS admin make you an SSO account
```sh
aws configure sso
# SSO session name: `prod`
# SSO Start URL: like this - `https://chrt.awsapps.com/start/#`
# SSO region: `us-east-1`
# SSO registration scopes: leave as is
# browser automatically prompts sign in
# CLI default client Region: `us-east-1`
# CLI default output format: `json`
# CLI profile name: leave as is
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

#### Login
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

#### Inspect AWS CLI configuration
```sh
# view config and credentials
open ~/.aws/config
open ~/.aws/credentials
# Test which account is being used
aws sts get-caller-identity
```

### VS Code Settings

- For `.vscode/settings.json` setup, [see here](https://github.com/astral-sh/ruff-vscode/blob/main/README.md#configuring-vs-code)
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
    "notebook.source.fixAll": "explicit",
    "notebook.source.organizeImports": "explicit"
  }
}
```


### SSH keys
- Follow the instructions. It's a bit tricky the first time, but overall not so bad. 
  - [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Upload public key to services as needed, e.g.:
  - GitHub - https://github.com/settings/keys
  - HuggingFace - https://huggingface.co/settings/keys


## Python

#### `uv` - manage packages and virtual environments
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

  
#### Ruff - linting and formatting
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

## Node (JavaScript)
- Node 22
```sh
brew install node@22
```
- TODO - homebrew for multiple npm versions
  - https://medium.com/@rldsn/manage-multiple-node-js-versions-with-homebrew-d8e6bf5b3b54
- alternative - `nvm`


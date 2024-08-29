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


## Setup
**Factory settings --> Daily driver**


### First steps
- Connect mouse and/or keybaord (need wired or Apple brand ones) > Sign in to wifi and Apple ID > Create MacOS user
- Tinker with the screen(s) settings, mouse settings, etc. as desired
- Settings > Desktop & Dock > set "Click wallpaper to reveal desktop" to "Only in Stage Manager"
- Download Google Chrome > Sign in to Google Account > Visit the bookmark for this page > Sign in to GitHub


### `homebrew`
1. Install [homebrew](https://brew.sh/)
2. Update homebrew
```sh
brew update
```
3. install [brew `formulae`](https://formulae.brew.sh/)
```sh
brew install \
  awscli \
  mongodb-atlas-cli \
  quarto \
  uv \
  zsh
```
4. install [brew `casks`](https://formulae.brew.sh/cask/)
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
  - Settings > General > Login Items > add noTunes


### Shell
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


### SSH keys
- Follow the instructions. It's a bit tricky the first time, but overall not so bad. 
  - [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Upload public key to services as needed, e.g.:
  - GitHub - https://github.com/settings/keys
  - HuggingFace - https://huggingface.co/settings/keys

### Python
- TODO - setup for `uv`

### Node (JavaScript)
- TODO - setup for `npm`, `nvm`

### Rust
- TODO - setup

# C++
- TODO - setup


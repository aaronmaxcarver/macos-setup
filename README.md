# macos-setup
**Factory settings --> Daily driver**

## Maintenance
### Routine (~1st day of each month)
- Backup code
- Backup Chrome bookmarks
  - go to [chrome://bookmarks/](chrome://bookmarks/) > snowman at top right > export bookmarks > save file > add to [Backups](https://drive.google.com/drive/u/0/folders/1ZPrKNiOxw9zRAG6sz0WC9L2u2Um3CaLq)
- Collect credentials into an encrypted drive and backup
  - Create a credential folder > add all new credentials
  - Open the existing encrypted credentials `dmg` > add those files to the new credentials folder
  - Open `Disk Utility` > File > New Image > Image from folder
  - Select the new credentials folder > choose Encryption type of "256-bit AES ..." > enter password
  - Open the new encrypted `dmg` to ensure the password was set correctly
  - Copy the new `.dmg` to secondary storage, e.g. Google Drive
  - Delete all plaintext credentials files

## Setup

### First steps
- Connect mouse and/or keybaord (need wired or Apple brand ones), sign in to wifi and Apple ID, create MacOS user
- Download Google Chrome, sign in to Google Account
- Visit the bookmark for this page > Sign in to GitHub
- Tinker with the screen, mouse settings, etc.
- Settings > Desktop & Dock > set "Click wallpaper to reveal desktop" to "Only in Stage Manager"
  
### `homebrew`
1. [install homebrew](https://brew.sh/)
2. update homebrew
```sh
brew update
```
3. install `formulae`
```sh
brew install \
  awscli \
  mongodb-atlas-cli \
  quarto \
  uv \
  zsh
```
4. install `casks`
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
5. Setup
- Open each program, add to dock, log in, configure settings, etc.
- Settings > General > Login Items > add noTunes

### Shell
- [oh my zsh](https://ohmyz.sh/#install)
```
open ~/.zshrc
# set:
ZSH_THEME="agnoster"
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
- [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Used by
  - GitHub - 
  - HuggingFace - 

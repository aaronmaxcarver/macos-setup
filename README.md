# macos-setup
Notes of the diff between factory settings and daily driver apps and settings

- example video - https://www.youtube.com/watch?v=kIdiWut8eD8

## Maintenance
### Routine (~1st day of each month)
- Backup code
- Backup Chrome bookmarks
- Collect credentials into an encrypted drive and backup
  - Create a credential folder > add all new credentials
  - Open the existing encrypted credentials `dmg` > add those files to the new credentials folder
  - Open `Disk Utility` > File > New Image > Image from folder
  - Select the new credentials folder > choose Encryption type of "256-bit AES ..." > enter password
  - Open the new encrypted `dmg` to ensure the password was set correctly
  - Copy the new `.dmg` to secondary storage, e.g. Google Drive
  - Delete all plaintext credentials files

### Python 
- uv for all things python management

## Setup

### Shell(s) and PATH
- `zsh`
  - TODO - how to install
  - TODO - how to install `ohmyzsh`
  - `ohmyzsh` settings
- PATH sources
```sh
# system
open /etc/paths
# zsh
open ~/.zshrc
open ~/.zprofile
# bash
open /etc/bashrc
open ~/.bashrc
open ~/.bash_profile
open ~/.bash_history
# ???
open /etc/profile
open ~/.profile
```

### SSH keys
- [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Used by
  - GitHub - 
  - HuggingFace - 

### `homebrew`
- TODO - how to install
- packages installed
- listing packages

- casks
```sh
# Snowflake CLI - https://docs.snowflake.com/en/user-guide/snowsql-install-config
brew install --cask snowflake-snowsql
# Add this to .zshrc
# alias snowsql=/Applications/SnowSQL.app/Contents/MacOS/snowsql
```

### Python
- System python
- XCode python
- uv python
- homebrew python
- framework python (downloads from python.org)

### CLI tools
- AWS CLI v2
- MongoDB Atlas CLI
- Quarto

### Applications
- Cloudflare WARP
- Docker Desktop
- Google Chrome
- Discord
- Docker
- MongoDB Compass
- Mosaic + settings file
- Neo4j Desktop
- noTunes
- Ollama
- pgAdmin 4
- Postgres
- Postman
- Scrivener
- Slack
- Visual Studio Code
- Zoom
- Zotero

### Data Storage
- Repos
- Google Drive
- Cold storage backup



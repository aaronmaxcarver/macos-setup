# macos-setup
**Factory settings --> Daily driver**

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

## Setup

### `homebrew`
- [install homebrew](https://brew.sh/)
- update homebrew
```sh
brew update
```
- `formulae`
```sh
brew install \
  docker \
  mongodb-community \
  postgresql \
  zsh
```
- `casks`
```sh
brew install --cask \
  docker \
  google-chrome \
  discord \
  mongodb-compass \
  neo4j-desktop \
  notunes \
  ollama \
  pgadmin4 \
  postman \
  slack \
  visual-studio-code \
  zoom \
  zotero
```
- more `casks`
```sh
# Snowflake CLI - https://docs.snowflake.com/en/user-guide/snowsql-install-config
brew install --cask snowflake-snowsql
# Add this to .zshrc
# alias snowsql=/Applications/SnowSQL.app/Contents/MacOS/snowsql
```

### Other programs
- Cloudflare WARP
- Mosaic + settings file
- Postgres
- Scrivener
 
### CLI tools
- [uv](https://docs.astral.sh/uv/)
- [AWS CLI v2](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
- [MongoDB Atlas CLI](https://www.mongodb.com/docs/atlas/cli/current/install-atlas-cli/)
- [Quarto](https://quarto.org/docs/get-started/)



### SSH keys
- [Generating a new SSH key and adding it to the ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
- Used by
  - GitHub - 
  - HuggingFace - 

### Data Storage
- Repos
- Google Drive
- Cold storage backup



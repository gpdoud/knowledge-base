# Setup Fedora Instance

## Upgrade dnf for current packages

    dnf upgrade

## Installed with OS
- Git

## Using Software Store
- Edge
- Visual Studio Code
- Terminator (terminal)

## Github cli

### Install
    sudo dnf install 'dnf-command(config-manager)'

    sudo dnf config-manager --add-repo https://cli.github.com/packages/rpm/gh-cli.repo    

    sudo dnf install gh --repo gh-cli
   
### Upgrade

    sudo dnf update gh

## Dotnet v8.0

### Install

Installing the SDK also installs the runtime

    sudo dnf install dotnet-sdk-8.0

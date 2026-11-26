<div align="center">
<h1>
  Stoat for Desktop
  
  [![Stars](https://img.shields.io/github/stars/stoatchat/for-desktop?style=flat-square&logoColor=white)](https://github.com/stoatchat/for-desktop/stargazers)
  [![Forks](https://img.shields.io/github/forks/stoatchat/for-desktop?style=flat-square&logoColor=white)](https://github.com/stoatchat/for-desktop/network/members)
  [![Pull Requests](https://img.shields.io/github/issues-pr/stoatchat/for-desktop?style=flat-square&logoColor=white)](https://github.com/stoatchat/for-desktop/pulls)
  [![Issues](https://img.shields.io/github/issues/stoatchat/for-desktop?style=flat-square&logoColor=white)](https://github.com/stoatchat/for-desktop/issues)
  [![Contributors](https://img.shields.io/github/contributors/stoatchat/for-desktop?style=flat-square&logoColor=white)](https://github.com/stoatchat/for-desktop/graphs/contributors)
  [![License](https://img.shields.io/github/license/stoatchat/for-desktop?style=flat-square&logoColor=white)](https://github.com/stoatchat/for-desktop/blob/main/LICENSE)
</h1>
Application for Windows, macOS, and Linux.
</div>
<br/>

> [!NOTE]
> **CowMe para Desktop** — fork do [stoatchat/for-desktop](https://github.com/stoatchat/for-desktop) v1.5.4, modificado a partir de 25/11/2026: abre direto em https://cowme.net.br, nome e ícone CowMe (pasta [`cowme/`](cowme/)), Discord Rich Presence do CowMe e **sem atualização automática** (ela instalaria o Stoat oficial por cima). Servidor e client web: [17nekrotciv/cowme-server](https://github.com/17nekrotciv/cowme-server).
>
> Gerar o instalador no Windows (Node.js e pnpm 11.17.0):
>
> ```sh
> git -c submodule.assets.update=checkout submodule update --init --depth 1 assets
> pnpm install
> pnpm exec electron-forge make --targets squirrel   # out/make/squirrel.windows/x64/cowme-desktop-setup.exe
> ```
>
> Use `--targets squirrel`: com `@electron-forge/maker-squirrel` o Forge ignora a configuração e falha com "Description is required". O resto deste README é o original do Stoat.

## Installation

<a href="https://repology.org/project/stoat-desktop/versions">
    <img src="https://repology.org/badge/vertical-allrepos/stoat-desktop.svg" alt="Packaging status" align="right">
</a>

- All downloads and instructions for Stoat can be found on our [Website](https://stoat.chat/download).

## Development Guide

_Contribution guidelines for Desktop app TBA!_

<!-- Before contributing, make yourself familiar with [our contribution guidelines](https://developers.revolt.chat/contrib.html), the [code style guidelines](./GUIDELINES.md), and the [technical documentation for this project](https://revoltchat.github.io/frontend/). -->

Before getting started, you'll want to install:

- [Git](https://git-scm.com/install/)
- [mise-en-place](https://mise.jdx.dev/getting-started.html)

Then proceed to setup:

```bash
# clone the repository
git clone --recursive https://github.com/stoatchat/for-desktop stoat-for-desktop
cd stoat-for-desktop

# Install tools from mise
mise install

# install all packages
mise install:frozen

# start the application
mise dev
# ... or build the bundle
mise build
# ... or build all distributables
mise make
```

Various useful commands for development testing:

```bash
# connect to the development server
mise exec -- pnpm start -- --force-server http://localhost:5173

# test the flatpak (after `make`)
mise exec -- pnpm install:flatpak
mise exec -- pnpm run:flatpak
# ... also connect to dev server like so:
mise exec -- pnpm run:flatpak --force-server http://localhost:5173

# Nix-specific instructions for testing
nix develop
pnpm package
pnpm run:nix
# ... as before:
pnpm run:nix --force-server=http://localhost:5173
# a better solution would be telling
# Electron Forge where system Electron is
```

### Pulling in Stoat's assets

If you want to pull in Stoat brand assets after pulling, run the following:

```bash
# update the assets
mise assets
```

Currently, this is required to build, any forks are expected to provide their own assets.

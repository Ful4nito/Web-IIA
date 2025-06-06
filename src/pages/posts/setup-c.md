# Setup de Entorno para programar en C

## Instalar Chocolately

``` sh
# Windows PowerShell y CMD
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

## Instalar herramientas

``` sh
# Instalar compilador C
choco install mingw

# Instalar git
choco install git
```

## Instalar Editor

``` sh
# Neovim
choco install neovim

# Vim
choco install vim

# Nano
choco install nano
```

## Instalar Nvchad

``` sh
# Windows CMD
git clone https://github.com/NvChad/starter %USERPROFILE%\AppData\Local\nvim
nvim

# Windows PowerShell
git clone https://github.com/NvChad/starter $ENV:USERPROFILE\AppData\Local\nvim
```

## Remover Nvchad

``` sh
# Windows CMD
rd -r ~\AppData\Local\nvim
rd -r ~\AppData\Local\nvim-data

# Windows PowerShell
rm -Force ~\AppData\Local\nvim
rm -Force ~\AppData\Local\nvim-data
```

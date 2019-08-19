# Entornos virtuales

Hay dos formas básicas de trabajar con entornos virtuales. Se pueden usar entornos virtuales teniendo una sola versión de python instalada. O se puede manejar diferentes versiones de python y diferentes entornos virtuales.

## Manejar diferentes versiones de Python

Para esto necesitamos instalar pyenv.

1. Se debe asegurar tener los siguientes paquetes instalados (debian o deribadas):

```bash
sudo apt install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python-openssl git
```

2. Instalar.

```bash
curl https://pyenv.run | bash
```

3. Dependiendo del shell interpreter que se tenga instalado se debe agregar los siguientes parámetros a su archivo de configuración. La última linea se puede descomentar si se quiere que al entrar a un directoria que tenga configurado una versión de python local esta se active automáticamente.

```bash
export PATH="/home/pitmmam/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
# eval "$(pyenv virtualenv-init -)"
```

Para listar las versiones de python disponible:

```bash
pyenv install -l
```

Para instalar una version específica de python:

```bash
pyenv install 3.7.4
```

Para configurar una versión de forma global en el sistema:

```bash
pyenv global 3.7.4
```

Para configurar una versión en un directorio específico:

```bash
pyenv local 3.7.4
```

Para revisar las versiones de python instaladas

```bash
pyenv versions
```

## Manejar diferentes entornos virtuales

1. Instalar pyenv-virtualenv

```bash
git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
```

Para crear un nuevo entorno virtual de python de una versión específica:

```bash
pyenv virtualenv <version> <name-virtualenv>
```

Para crear un nuevo entorno virtual de python de la versión activa.

```bash
pyenv virtualenv <name-virtualenv>
```

Para activar un entorno virtual:

```bash
pyenv activate <name-virtualenv>
```

para desactivar un entorno virtual:

```bash
pyenv deactivate <name-virtualenv>
```

Para desinstalar un entorno virtual:

```bash
pyenv unistall <name-virtualenv>
```

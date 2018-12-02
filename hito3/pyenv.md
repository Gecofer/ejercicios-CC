## Instalar pyenv como environment

Para poder hacer uso de un environment en todo el proyecto de la asignatura Cloud Computing, se va hacer uso de **pyenv**, el cuál permite cambiar fácilmente entre múltiples versiones de Python (proporciona soporte para versiones Python por proyecto). Es simple, discreto y sigue la tradición de UNIX de herramientas de un solo propósito que hacen una cosa bien.

- **¿Qué versión de Python se va a usar?** Al comienzo del proyecto se hizo uso de la versión 3.7.0 de Python, sin embargo, dicha versión es desarrolladora y no es soportado por muchos paquetes. Es por ello, que se va hacer uso también de la versión 3.6.7, la última de Python 3.6, considerado como estable. Así, uso la 3.6.7 por la estabilidad. Además, dicha versión también es soportada por Heroku.

A continuación, se enlanzan algunos enlaces interesantes de pyenv:

- [Simple Python Version Management: pyenv](https://github.com/pyenv/pyenv)
- [Pyenv install](https://github.com/pyenv/pyenv-installer)

Para instalar un entorno, tanto en Mac como en Ubuntu, podemos hacer uso de dos alternativas, en mi caso he hecho de la primera, en donde me instalo una versión específica para un directorio concreto:

1. [Python Development on macOS with pyenv](https://medium.com/@jordanthomasg/python-development-on-macos-with-pyenv-2509c694a808)

~~~
# Install pyenv
$ brew install pyenv

# Add pyenv initializer to shell startup script
$ echo 'eval "$(pyenv init -)"' >> ~/.bash_profile

# Restart your shell for changes to take effect

# Install python
# List of available versions with pyenv install --list
$ pyenv install 3.6.7

# To set a Python version for a specific project
# cd into your project and then run
$ cd Documentos
$ mkdir proyecto-CC-18-19
$ cd proyecto-CC-18-19
$ pyenv local 3.6.7

# Will create a .python-version file in the current directory
# which pyenv will see and use to set the version 3.6.7
$ cat .python-version
~~~

2. [Python Development on macOS with pyenv-virtualenv](https://medium.com/@jordanthomasg/python-development-on-macos-with-pyenv-virtualenv-ec583b92934c)

~~~
# Install pyenv-virtualenv
$ brew install pyenv-virtualenv

# Add pyenv-virtualenv initializer to shell startup script
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile

# Create Virtual Environment
# pyenv virtualenv <python-version> <name>
$ pyenv virtualenv 3.6.7 env

# Activate Virtual Environment
$ pyenv activate env

# Deactivate Virtual Environment
$ pyenv deactivate env
~~~

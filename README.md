# pyenv
```console
mkdir ~/.ve
mkdir ~/workspace
```

# ~/.zshrc
```console
export WORKON_HOME=~/.ve
export PROJECT_HOME=~/workspace
eval "$(pyenv init -)"
#pyenv virtualenvwrapper_lazy
```

```console
curl -L https://raw.githubusercontent.com/yyuu/pyenv-installer/master/bin/pyenv-installer | bash

```

# Install python

```console
pyenv install 3.6.2
pyenv install 2.7.13
```

# Create Environment

```console
pyenv virtualenv 3.6.2 jupyter3
pyenv virtualenv 3.6.2 tools3
pyenv virtualenv 2.7.13 ipython2
pyenv virtualenv 2.7.13 tools2
```

# Install jupyter on python3

```console
pyenv activate jupyter3
pip install -U jupyter
python -m ipykernel install --user
pyenv deactivate
```

# Install jupyter on python2

```console
pyenv activate ipython2
pip install -U ipykernel
python -m ipykernel install --user
pyenv deactivate
```

# Install tools3

```console
pyenv activate tools3
pip install -U youtube-dl mps-youtube gnucash-to-beancount rows speedtest-cli
pyenv deactivate
```

# Install tools2

```console
pyenv activate tools2
pip install -U rename s3cmd fabric mercurial
pyenv deactivate
```

# Enable
```console
pyenv global 3.6.2 2.7.13 jupyter3 ipython2 tools3 tools2
```


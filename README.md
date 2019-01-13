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
pyenv install 3.7.1
pyenv install 2.7.15
```

# Create Environment

```console
pyenv virtualenv 3.7.1 jupyter3
pyenv virtualenv 3.7.1 tools3
pyenv virtualenv 3.7.1 neovim3
pyenv virtualenv 2.7.15 ipython2
pyenv virtualenv 2.7.15 tools2
pyenv virtualenv 2.7.15 neovim2
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
pip install -U youtube-dl mps-youtube gnucash-to-beancount rows speedtest-cli fast.com
pyenv deactivate
```

# Install tools2

```console
pyenv activate tools2
pip install -U rename s3cmd fabric mercurial ansible
pyenv deactivate
```

# Install jupyter on neovim2

```console
pyenv activate neovim2
pip install -U neovim
pyenv deactivate
```

# Install jupyter on neovim3

```console
pyenv activate neovim3
pip install -U neovim flake8
ln -s `pyenv which flake8` ~/bin/flake8
pyenv deactivate
```

# Enable
```console
pyenv global 3.7.1 2.7.15 jupyter3 ipython2 tools3 tools2 neovim3 neovim2
```

# ipython with pyenv
```console
curl -L http://hbn.link/hb-ipython-startup-script > ~/.ipython/profile_default/startup/00-venv-sitepackages.py
```



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

git clone https://github.com/yyuu/pyenv-virtualenvwrapper.git ~/.pyenv/plugins/pyenv-virtualenvwrapper
```

# Pre-Req
## OpenSuse
```console
zypper install gcc automake make openssl-devel ncurses-devel readline-devel zlib-devel tk-devel libffi-devel sqlite3-devel
```

## ubuntu
```console
sudo apt install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python-openssl git
```
## centos
```console
yum install gcc-plugin-devel python-devel python-six python-pygments graphviz libffi-devel bzip2-devel readline-devel openssl-devel sqlite-devel
```

# Install python

```console
pyenv install 3.7.3
pyenv install 2.7.16
```

# Create Environment

```console
pyenv virtualenv 3.7.3 jupyter3 && \
pyenv virtualenv 3.7.3 tools3 && \
pyenv virtualenv 3.7.3 neovim3 && \
pyenv virtualenv 2.7.16 ipython2 && \
pyenv virtualenv 2.7.16 tools2 && \
pyenv virtualenv 2.7.16 neovim2
```

# Install jupyter on python3

```console
pyenv activate jupyter3
pip install -U jupyter environment_kernels
python -m ipykernel install --user
jupyter notebook --generate-config
pyenv deactivate
```

# Install ipython on python2

```console
pyenv activate ipython2
pip install -U ipykernel
python -m ipykernel install --user
pyenv deactivate
```

# Install tools3

```console
pyenv activate tools3
pip install -U youtube-dl mps-youtube gnucash-to-beancount rows speedtest-cli fast.com ansible
# URL: https://www.tecmint.com/powerline-adds-powerful-statuslines-and-prompts-to-vim-and-bash/
# pip install git+git://github.com/Lokaltog/powerline
pip install vim-power
pyenv deactivate
```

# Install tools2

```console
pyenv activate tools2
pip install -U rename s3cmd fabric mercurial
pyenv deactivate
```

# Install neovim2 to python2

```console
pyenv activate neovim2
pip install -U neovim
pyenv deactivate
```

# Install neovim3 to python3

```console
pyenv activate neovim3
pip install -U neovim flake8 jedi autopep8 pep8 pyflakes isort yapf
ln -s `pyenv which flake8` ~/bin/flake8
pyenv deactivate
```

# Enable
```console
pyenv global 3.7.3 2.7.16 jupyter3 ipython2 tools3 tools2 neovim3 neovim2
```

# ipython with pyenv
```console
ipython profile create
curl -L http://hbn.link/hb-ipython-startup-script > ~/.ipython/profile_default/startup/00-venv-sitepackages.py
```

# neovim 
```console
let g:python_host_prog = expand('$HOME/.pyenv/versions/neovim2/bin/python')
let g:pythol2_host_prog = expand('$HOME/.pyenv/versions/neovim2/bin/python')
let g:python3_host_prog = expand('$HOME/.pyenv/versions/neovim3/bin/python')
```

# jupyter
nvim /root/.jupyter/jupyter_notebook_config.py
```console
c.NotebookApp.kernel_spec_manager_class = 'environment_kernels.EnvironmentKernelSpecManager'
c.EnvironmentKernelSpecManager.find_conda_envs=False
c.EnvironmentKernelSpecManager.virtualenv_env_dirs=['~/.pyenv/versions/']
c.EnvironmentKernelSpecManager.virtualenv_prefix_template = "{}"
c.EnvironmentKernelSpecManager.display_name_template = "{}"
```
 

# pyenv
```console
mkdir ~/.ve
mkdir ~/workspace
```

# ~/.zshrc
```console
export PATH=$HOME/.pyenv/bin:$PATH
export WORKON_HOME=~/.ve
export PROJECT_HOME=~/workspace
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"

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

## ubuntu/debian
```console
sudo apt install -y make build-essential libxslt1-dev libxml2-dev libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3-openssl git cython3
```
Alternative of libreadline-dev:
```sh
sudo apt install libedit-dev
```
## centos
```console
yum install @development zlib-devel bzip2 bzip2-devel readline-devel sqlite \
sqlite-devel openssl-devel xz xz-devel libffi-devel findutils
```

## centos 8
```console
dnf install readline-devel libffi-devel sqlite-devel openssl-devel bzip2-devel dnf-plugins-core  # install this to use 'dnf builddep'
dnf builddep python3
dnf update -y
```

# Install python

```console
pyenv install 3.11.9
pyenv install 2.7.18
```

# Create Environment

```console
pyenv virtualenv 3.11.9 jupyter3 && \
pyenv virtualenv 3.11.9 tools3 && \
pyenv virtualenv 3.11.9 neovim3 && \
pyenv virutalenv 3.11.9 oracle-oci && \
pyenv virtualenv 2.7.18 ipython2 && \
pyenv virtualenv 2.7.18 tools2 && \
pyenv virtualenv 2.7.18 neovim2
```

# Install jupyter on python3

```console
pyenv activate jupyter3
pip install -U jupyter==6.1.5 environment_kernels jupyterlab jupyter_ai jupyter_ai_magics jupyter_contrib_nbextensions notebook_shim python-language-server powershell_kernel bash_kernel jupyterthemes cython==0.29.30
python -m ipykernel install --user
python -m powershell_kernel.install --powershell-command pwsh
python -m bash_kernel.install
jupyter notebook --generate-config
jupyter contrib nbextension install --user
jupyter nbextension enable hinterland/hinterland
jupyter contrib nbextension install --sys-prefix
ln -s `pyenv which jupyter` ~/bin/jupyter
pyenv deactivate
```

# Install all lsp for jupyter
```bash
~/.local/bin/install-lsp.sh
```
# [jupyter Lab](https://www.linkedin.com/pulse/tensorflow-gpu-ubuntu-wsl-gerald-gibson/)
```bash
python -m pip install -q --upgrade pip setuptools pip-autoremove
python -m pip install --no-input numpy numba matplotlib pandas pandoc plotly scipy seaborn statistics tabulate line_profiler
python -m pip install --no-input tensorflow==2.9.1 tensorflow-probability tensorflow-addons tensorflow_datasets tensorflow-text==2.9.0 
python -m pip install --no-input pywebcopy bs4 PySimpleGUI display_xml gtts playsound
python -m pip install --no-input jupyterlab ipyfilechooser tqdm wget
python -m pip install -q jupyterlab-lsp python-lsp-server[all]
python -m pip install -U langchain_google_genai langchain_nvidia_ai_endpoints langchain_anthropic langchain_openai langchain_mistralai langchain_cohere cohere
python -m pip install openai num2words scikit-learn transformes
python -m pip install jupyterhub
npm install -g configurable-http-proxy
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
mkdir -p ~/bin
pyenv activate tools3
pip install -U ansible ansible-lint autoenv autopep8 black codespell colorama cookiecutter fast.com flake8 gnucash-to-beancount isort jedi-language-server jrnl mps-youtube molecule mypy pre-commit prospector pyarmor pydocstyle pyflakes pylama pylint pyls rows speedtest-cli reorder-python-imports thefuck zabbix-api youtube-dl tmuxp vulture yapf yamlfix yamllint visidata virtualenv virtualenvwrapper
# URL: https://www.tecmint.com/powerline-adds-powerful-statuslines-and-prompts-to-vim-and-bash/
# pip install git+git://github.com/Lokaltog/powerline
pip install vim-power
ln -s `pyenv which pytest` ~/bin/pytest
ln -s `pyenv which tmuxp` ~/bin/tmuxp
pyenv deactivate
```

# Install oracle-oci

```console
pyenv activate oracle-oci
pip install -U oci-cli
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
pip install -U pynvim
pyenv deactivate
```

# Install neovim3 to python3

```console
pyenv activate neovim3
pip install -U black pynvim pylint flake8 jedi autopep8 pep8 pydocstyle pyflakes isort yapf yamllint mypy
ln -s `pyenv which autopep8` ~/bin/autopep8
ln -s `pyenv which black` ~/bin/black
ln -s `pyenv which flake8` ~/bin/flake8
ln -s `pyenv which isort` ~/bin/isort
ln -s `pyenv which jedi` ~/bin/jedi
ln -s `pyenv which mypy` ~/bin/mypy
ln -s `pyenv which pydocstyle` ~/bin/pydocstyle
ln -s `pyenv which pylint` ~/bin/pylint
ln -s `pyenv which yapf` ~/bin/yapf
ln -s `pyenv which yamllint` ~/bin/yamllint

pyenv deactivate
```

# Enable
```console
pyenv global 3.11.7 2.7.18 oracle-oci jupyter3 ipython2 tools3 tools2 neovim3 neovim2
```

# ipython with pyenv
```console
ipython profile create
curl -L http://hbn.link/hb-ipython-startup-script > ~/.ipython/profile_default/startup/00-venv-sitepackages.py
```

# Python2
```console
pip2 install virtualenv
python2 -m virtualenv .venv
```

# neovim 
```console
let g:python_host_prog = expand('$HOME/.pyenv/versions/neovim2/bin/python')
let g:python2_host_prog = expand('$HOME/.pyenv/versions/neovim2/bin/python')
let g:python3_host_prog = expand('$HOME/.pyenv/versions/neovim3/bin/python')
```

# jupyter
nvim ~/.jupyter/jupyter_notebook_config.py
```console
c.ServerApp.kernel_spec_manager_class = 'environment_kernels.EnvironmentKernelSpecManager'
c.EnvironmentKernelSpecManager.find_conda_envs=False
c.EnvironmentKernelSpecManager.virtualenv_env_dirs=['~/.pyenv/versions/']
c.EnvironmentKernelSpecManager.virtualenv_prefix_template = "{}"
c.EnvironmentKernelSpecManager.display_name_template = "{}"
c.ServerApp.log_datefmt = "%Y-%m-%d %H:%M:%S"
c.ServerApp.open_browser = False
```

# ipython
```console
# Install IPython: python3 -m pip install ipython

import IPython
from traitlets.config import get_config

cfg = get_config()
cfg.InteractiveShellEmbed.colors = "Linux"  # syntax highlighting
cfg.InteractiveShellEmbed.confirm_exit = False

alias interacti IPython.embed(config=cfg)
```

# [install R](https://www.geeksforgeeks.org/how-to-fix-kernel-error-in-jupyter-notebook/)
```console
sudo apt update
sudo apt install r-base r-base-dev
```

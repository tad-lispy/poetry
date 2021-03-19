# Introduction

Poetry is a tool for dependency management and packaging in Python.
It allows you to declare the libraries your project depends on and it will manage (install/update) them for you.


## System requirements

Poetry requires Python 2.7 or 3.5+. It is multi-platform and the goal is to make it work equally well
on Windows, Linux and OSX.

!!! note

    Python 2.7 and 3.5 will no longer be supported in the next feature release (1.2).
    You should consider updating your Python version to a supported one.


## Installation

Poetry provides a custom installer that will install `poetry` isolated
from the rest of your system.

### osx / linux / bashonwindows install instructions
```bash
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py | python -
```
### windows powershell install instructions
```powershell
(Invoke-WebRequest -Uri https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py -UseBasicParsing).Content | python -
```

!!!warning

    The previous `get-poetry.py` installer is now deprecated, if you are currently using it
    you should migrate to the new, supported, `install-poetry.py` installer.

The installer installs the `poetry` tool to Poetry's `bin` directory. This location depends on you system:

- `$HOME/.local/bin` for Unix
- `%APPDATA%\Python\Scripts` on Windows

If this directory is not on you `PATH`, you will need to add it manually
if you want to invoke Poetry with simply `poetry`.

Alternatively, you can use the full path to `poetry` to use it.

Once Poetry is installed you can execute the following:

```bash
poetry --version
```

If you see something like `Poetry (version 1.2.0)` then you are ready to use Poetry.
If you decide Poetry isn't your thing, you can completely remove it from your system
by running the installer again with the `--uninstall` option or by setting
the `POETRY_UNINSTALL` environment variable before executing the installer.

```bash
python install-poetry.py --uninstall
POETRY_UNINSTALL=1 python install-poetry.py
```

By default, Poetry is installed into the user's platform-specific home directory.
If you wish to change this, you may define the `POETRY_HOME` environment variable:

```bash
POETRY_HOME=/etc/poetry python install-poetry.py
```

If you want to install prerelease versions, you can do so by passing `--preview` option to `install-poetry.py`
or by using the `POETRY_PREVIEW` environment variable:

```bash
python install-poetry.py --preview
POETRY_PREVIEW=1 python install-poetry.py
```

Similarly, if you want to install a specific version, you can use `--version` option or the `POETRY_VERSION`
environment variable:

```bash
python install-poetry.py --version 1.2.0
POETRY_VERSION=1.2.0 python install-poetry.py
```

You can also install Poetry for a `git` repository by using the `--git` option:

```bash
python install-poetry.py --git https://github.com/python-poetry/poetry.git@master
````

!!!note

    Note that the installer does not support Python < 3.6.


### Alternative installation methods

#### Installing with `pipx`

Using [`pipx`](https://github.com/pipxproject/pipx) to install Poetry is also possible.
[pipx] is used to install Python CLI applications globally while still isolating them in virtual environments.
This allows for clean upgrades and uninstalls.

```bash
pipx install poetry
```

```bash
pipx upgrade poetry
```

```bash
pipx uninstall poetry
```


#### Installing with `pip`

Using `pip` to install Poetry is possible.

```bash
pip install --user poetry
```

!!!warning

    Be aware that it will also install Poetry's dependencies
    which might cause conflicts with other packages.


## Updating `poetry`

Updating Poetry to the latest stable version is as simple as calling the `self update` command.

```bash
poetry self update
```

If you want to install pre-release versions, you can use the `--preview` option.

```bash
poetry self update --preview
```

And finally, if you want to install a specific version, you can pass it as an argument
to `self update`.

```bash
poetry self update 1.2.0
```


## Enable tab completion for Bash, Fish, or Zsh

`poetry` supports generating completion scripts for Bash, Fish, and Zsh.
See `poetry help completions` for full details, but the gist is as simple as using one of the following:


```bash
# Bash
poetry completions bash > /etc/bash_completion.d/poetry.bash-completion

# Bash (Homebrew)
poetry completions bash > $(brew --prefix)/etc/bash_completion.d/poetry.bash-completion

# Fish
poetry completions fish > ~/.config/fish/completions/poetry.fish

# Fish (Homebrew)
poetry completions fish > (brew --prefix)/share/fish/vendor_completions.d/poetry.fish

# Zsh
poetry completions zsh > ~/.zfunc/_poetry

# Oh-My-Zsh
mkdir $ZSH_CUSTOM/plugins/poetry
poetry completions zsh > $ZSH_CUSTOM/plugins/poetry/_poetry

# prezto
poetry completions zsh > ~/.zprezto/modules/completion/external/src/_poetry

```

!!! note

    You may need to restart your shell in order for the changes to take effect.

For `zsh`, you must then add the following line in your `~/.zshrc` before `compinit`:

```bash
fpath+=~/.zfunc
```

For `oh-my-zsh`, you must then enable poetry in your `~/.zshrc` plugins

```
plugins(
	poetry
	...
	)
```

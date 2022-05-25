# Poetry

[Poetry](https://python-poetry.org/) is the tool we use for dependency management, environment management, and packaging in Python.

### Prerequisites

1. Install poetry:

```shell
    curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python -
```

2. Add poetry to path:

```shell
    source $HOME/.poetry/env
```

3. Check that you have a Python version compatible with requirements for this project. See `python` under `[tool.poetry.dependencies]` in `pyproject.toml` for current dependencies. If you are not currently using Pyenv to manange Python installation, refer to our [Documentation](https://inquirer.atlassian.net/wiki/spaces/KB/pages/1763704858/How+to+manage+Python+installations+on+your+machine+with+Pyenv). Follow instructions there to install an appropriate version.

```shell
    pyenv versions
```

4. Check futher that you have Python versions installed for all that are tested by tox. See `envlist` under `[tox]` in `tox.ini` for current dependencies.

```shell
    pyenv install <version>
```

5. Create poetry virtualenv:

```shell
    poetry shell
```

6. If you are using VSCode: the `.vscode` directory in this repo contains a setting that will tell VSCode to look at poetry to find Python interpreters. You may need to restart VSCode for this setting to take effect. Once set, you can select the poetry environment from the list of interpreters by bringing up the Command Palette (Cmd+Shift+P) and searching for "Python: Select Interpreter".

### Development

#### Installation

Install `inq-data-resources` and its dependencies by running:

```shell
poetry install
```

#### Managing Dependencies

When editing the dependencies for `inq-data-resources`, you sync the dependencies from `pyproject.toml` to `poetry.lock` by running:

```shell
poetry lock
```
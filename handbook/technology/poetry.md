# Poetry

[Poetry](https://python-poetry.org/) is the tool we use for dependency management, environment management, and packaging in Python.

## System Requirements

For our purposes, you should have a Python installation with version 3.8 or greater. Refer to our [documentation on pyenv](https://inquirer.atlassian.net/wiki/spaces/KB/pages/1763704858/How+to+manage+Python+installations+on+your+machine+with+Pyenv) for instructions on downloading an appropriate installation.

## Installation

See [Poetry's documentation](https://python-poetry.org/docs/#installation) for detailed installation instructions.

After installing Poetry, you may need to restart your terminal window so that it can locate the `poetry` command

Finally, change one specific configuration setting for Poetry by running `poetry config virtualenvs.in-project true` so that when Poetry creates a virtual environment for you, it will do so inside your project's root directory. This will allow for the virtual environment to be easily discovered by development tools such as VSCode.

## Usage

Below is a list of common commands when using Poetry. See [Poetry's documentation](https://python-poetry.org/docs/cli/) for a complete list of commands.

### Install a project 

To install a project and its dependencies according to the configuration specified in the `pyproject.toml` file, run `poetry install`. If you're familiar with `pip`, then this is similar to running `pip install .`.

### Add a dependency

To add and install a required packages to your `pyproject.toml`, run `poetry install [--dev] <PACKAGE_NAME>` (specify the `--dev` flag to add the package as a development dependency). This is similar to running `pip install <PACKAGE_NAME>`.

### Bump the project's version

To increment the version of the project and write the new version back to `pyproject.toml`, run `poetry version <major|minor|patch>`

### Manage environments

Poetry will always work isolated from your global Python installation. To achieve this, it will first check if it’s currently running inside a virtual environment. If it is, it will use it directly without creating a new one. But if it’s not, it will use one that it has already created or create a brand new one for you.

By default, Poetry will try to use the currently activated Python version to create the virtual environment for the current project.

After installing your project, you can run any command from within your project's virtual environment by running `poetry run <COMMAND>`. Alternately, you can spawn a shell session within the virtual environment by running `poetry shell`.

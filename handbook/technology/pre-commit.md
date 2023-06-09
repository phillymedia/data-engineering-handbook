# pre-commit

To ensure that standardized and high-quality code is pushed to our remote repositories, we use a series of [pre-commit](https://pre-commit.com/) hooks that run upon each git commit. These hooks are configured in a `.pre-commit-config.yaml` file in the project's root folder. To install these hooks, run

```shell
poetry run pre-commit install
```

When a Pre-commit hook fails, the entire commit fails. Note, however, that the hooks will often automatically fix the file(s) that led to the failures, allowing you to simply run `git commit` again.


## Standard hooks
We use a set of out-of-the-box hooks for pre-commit in our projects. For new projects, add the following entries to your `.pre-commit-config.yaml` 

```yaml
repos:
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v2.4.0
    hooks:
      - id: check-added-large-files
      - id: check-ast
      - id: check-docstring-first
      - id: check-json
      - id: pretty-format-json
      - id: check-yaml
      - id: end-of-file-fixer
      - id: trailing-whitespace
      - id: check-merge-conflict
      - id: check-toml
  - repo: https://gitlab.com/pycqa/flake8
    rev: 3.7.9
    hooks:
      - id: flake8
        additional_dependencies: [flake8-typing-imports==1.6.0]
        args: ["--max-line-length=89"]
  - repo: https://github.com/asottile/reorder_python_imports
    rev: v1.9.0
    hooks:
      - id: reorder-python-imports
        args: [--py3-plus]
  - repo: https://github.com/psf/black
    rev: 22.3.0
    hooks:
      - id: black
  - repo: https://github.com/python-poetry/poetry
    rev: 1.5.1
    hooks:
      -id: poetry-check
```

If any of the hooks above are not relevant to a given project, then you can remove the hook for that particular project.

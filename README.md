# Python project template

This template uses `poetry` to manage your project. Poetry is a Python package and dependency manager that also handles building and publishing Python packages.

This template includes:
- Unit testing with `pytest`
- Code quality checks:
    - `black` style checking
    - `mypy` type checking
    - `flake8` linting
- Simple CI pipeline using GitHub Actions
- Jupyter notebook support

## Using Poetry to manage your project

Poetry is a Python package and dependency manager. It also nicely handles building and publishing Python packages.
To get started with Poetry using this template run 
```sh
poetry install
```
This will install all the dependencies listed in `pyproject.toml` to a virtual environment and afterwards you are ready to go.

Running python scripts with Poetry is easy:
```sh
poetry run python ./app/myscript.py
```

To add a new dependency to your Python project you can run
```sh
poetry add package-name
```
Poetry also distinguishes between development dependencies (not needed for deployment). Such dependencies can be added through `poetry add -D package-name`.

To use Pytest with poetry run:
```sh
poetry run pytest
```
Pytest will run style and type checking on all code in the `app` folder and also runs unit tests  in the `tests` folder.

## Working with Jupyter notebooks

You can launch Jupyter lab from the command line with:
```sh
poetry run jupyter lab
```
This will open a Jupyter kernel where you can create a notebook. Remember to place your notebook in the `notebooks` folder. It is also possible to use
```sh
poetry run jupyter notebook
```
which launches an instance of the old generation of the Jupyter notebook interface.

Unfortunately, notebooks are quite hard to collaborate on and to code review. It is suggested that one of these two approaches is followed in your project:

1. Once your notebook analysis is running nicely you should extract the code into a python script in the `app` folder and import the methods back into your notebook. This allows for collaborators to also make use of your code as well as introducing `pytest` capability and code review compatability.

2. Using `nbautoexport`. This one is a bit more limiting but allows for code reviews. This package will automatically export code in a jupyter notebook into a python script.
To enable it we need to run these two commands:
```sh
poetry run nbautoexport install
poetry run nbautoexport configure notebooks
```
The first line registers `nbautoexport` to run automatically while using Jupyter notebooks, while the second configures the notebooks folder in the project to automatically export code of notebooks that exist in this folder.
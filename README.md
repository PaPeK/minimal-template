# minimal-template 

**template repo**

## Install
0. optional: `conda env create -f env.yml`
1. normal: `python -m pip install .`
OR
1. **developer mode**: Install locally via `pip install -e . --user`

## How to use:
* add some bullets here 

## FILES
short explanation of all files in the repo:

* `minimal_template/`: folder contains [code, modules]
    * `__init__`: init file
* `tests/`: folder contains test files 
    * `test_with_pytest.py`: example file to test tesing via e.g. pytest
* `env.yml`: YAML environment file than specifies dependencies from other packages
* `LICENSE`: LICENSE File
* `pyproject.toml`: contains dependencies and various settings (black, ruff, ...) for the project
* `README.md`: the readme
* `setup.py`: needed for install via pip


## Explanation:
I will update the package the more I understand of the other template files and functions (poetry, tox vs. pytest, black)

* the `setup.py` file is only needed for developer mode install
    * in fact the `pyproject.toml` contains a block `[build-system]` with some flit-stuff that should enable developer-mode somehow without `setup.py` file (read)

## Developer notes

* if the package depends on a custum package `my_other_pack` that you want to edit during development
    1. specify it in the `env.yml` file (so users have it in their env)
    2. when doing `conda create -f env.yml` it will get installed via pip  (good for the users, bad for you since the path is somewhere in your env-directory)
    3. now reinstall to your local repo fo `my_other_pack` by:
        * activate environment `conda env create -f env.yml`
        * uninstall the package `pip uninstall my_other_pack`
        * change directory to your local installation `cd /PATH/to/your/local/install/or/my_other_pack`
        * pip-install it in editable mode: `pip install -e . --user`

### Git settings
If you plan having jupyter-notebooks in your repository, place them in the [./notebooks](./notebooks) folder.
The below settings are inspired by this [stackoverflow post](https://stackoverflow.com/posts/58004619/revisions)
* this folder contains the file [./notebooks/.gitattributes](./notebooks/.gitattributes) that will run at each add of an `*.ipynb` file the filter `strip-notebook-output`.
    * note that it will only remove the output for the git-commit BUT the output in your local notebook remains.
* the filter `strip-notebook-output` needs to be defined in your local `.git/config` or global `.gitconfig` as:
```
[filter "strip-notebook-output"]
    clean = "jupyter nbconvert --ClearOutputPreprocessor.enabled=True --to=notebook --stdin --stdout --log-level=ERROR"
```
* in order to run this you need to have the following packages installed
    * `conda install -c conda-forge jupyter_contrib_nbextensions`
    * `conda install nbconvert`

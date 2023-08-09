# minimal-template 

**template repo**

## Install
0. optional: `conda env create -f env.yml`
1. normal: `python -m pip install .`
OR
1. **developer mode**: Install locally via `pip install -e . --user`

## How to use:
* add some bullets here 

## Explanation:
I will update the package the more I understand of the other template files and functions (poetry, tox vs. pytest, black)

* the `setup.py` file is only needed for developer mode install
    * in fact the `pyproject.toml` contains a block `[build-system]` with some flit-stuff that should enable developer-mode somehow without `setup.py` file (read)

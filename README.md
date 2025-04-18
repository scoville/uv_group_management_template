# uv group management template
This repo is to show and summarize the group management procedures for uv.

The group manament have 2 parts:

1. Solving dependency
2. Installation
    1. Install packages to virtual python (recommended) or
    2. Install packages to system default python 

we recommended install packages to virtual python instead of system default python since this is not only sample and strictly foreward but also no extra `requirement.txt` will be generated

## Procedures

### 1. Solving dependency
1. create a `pyproject.toml` file
2. add package to main
    
    eg. 
    
    ```shell
    uv add numpy
    ```

    note:
    package related info will be added to pyproject.toml and uv.lock. Also package will be added to virtual python (.venv)

3. add package to dev group

    eg. 
    
    ```shell
    uv add --group dev ruff
    ```

    note:
    package related info will be added to pyproject.toml and uv.lock. Also package will be added to virtual python (.venv)

4. add package to other group

    eg. 
    ```shell
    uv add --group unittest
    ```

    note:
    package related info will be added to pyproject.toml and uv.lock. Also package will be added to virtual python (.venv)


After the runing above procedures,  it will result the `pyproject.toml` and `uv.lock` files in this repo

### 2. Installation 
#### 2.1 Install packages to virtual python (recommended)
* install packages in only main (recorded in uv.lock) to `.venv`
    
    eg. 
    ```shell
    uv sync --no-dev --frozen --active
    ```

* install packages in both main and dev group (recorded in uv.lock) to `.venv`

    eg. 
    ```shell
    uv sync --frozen --active
    ```

* install packages in both main and other group (recorded in uv.lock) to `.venv`

    eg.
    ```shell
    uv sync --group unittest --no-dev --frozen --active
    ```

* install packages in only dev (recorded in uv.lock) to `.venv`

    eg.
    ```shell
    uv sync --only-group dev --frozen --active
    ```

* install packages in only other group (recorded in uv.lock) to `.venv`

    eg.
    ```shell
    uv sync --only-group unittest --frozen --active
    ```

#### 2.2 Install packages to system default python 
* install packages in only main (recorded in uv.lock) to system default python (non-virual) 

    eg. 
    ```shell
    uv export --no-dev --format requirements-txt > requirements.txt
    uv pip install -r requirements.txt
    ```
    

* install packages in both main and dev group (recorded in uv.lock) to system default python (non-virual) 

    eg. 
    ```shell
    uv export --format requirements-txt > requirements_dev.txt
    uv pip install -r requirements_dev.txt
    ```

* install packages in both main and other group (recorded in uv.lock) to system default python (non-virual) 
    
    eg. 
    ```shell
    uv export --group unittest --no-dev --format requirements-txt > requirements_unittest.txt
    uv pip install -r requirements_unittest.txt
    ```

* install packages in only dev (recorded in uv.lock) to system default python (non-virual) 

    eg. 
    ```shell
    uv export --only-group dev --format requirements-txt > requirements_only_dev.txt
    uv pip install -r requirements_only_dev.txt
    ```

* install packages in only other group (recorded in uv.lock) to system default python (non-virual) 

    eg. 
    ```shell
    uv export --only-group unittest --format requirements-txt > requirements_only_unittest.txt
    uv pip install -r requirements_only_unittest.txt
    ``` 


# uv group management template
This repo is to show the group management procedures for uv


1. create a `pyproject.toml` file
2. add package to main
    
    eg. `uv add numpy`

    note:
    package related info will be added to pyproject.toml and uv.lock. Also package will be added to virtual python (.venv)

3. add package to dev group

    eg. `uv add --group dev ruff`

    note:
    package related info will be added to pyproject.toml and uv.lock. Also package will be added to virtual python (.venv)

4. add package to other group

    eg. `uv add --group unittest`

    note:
    package related info will be added to pyproject.toml and uv.lock. Also package will be added to virtual python (.venv)

5. install packages in only main to system default python (non-virual) 

    eg. 
    ```shell
    uv export --no-dev --format requirements-txt > requirements.txt`
    uv pip install -r requirements.txt`
    ```
    

6. install packages in both main and dev group to system default python (non-virual) 

    eg. 
    ```shell
    uv export --format requirements-txt > requirements_dev.txt`
    uv pip install -r requirements_dev.txt`
    ```

7. install packages in both main and other group to system default python (non-virual) 
     eg. 
    ```shell
    uv export --group unittest --no-dev --format requirements-txt > requirements_unittest.txt`
    uv pip install -r requirements_unittest.txt`
    ```

8. install packages in only dev to system default python (non-virual) 

    eg. 
    ```shell
    uv export --only-group dev --format requirements-txt > requirements_only_dev.txt`
    uv pip install -r requirements_only_dev.txt`
    ```

9. install packages in only other group to system default python (non-virual) 

    eg. 
    ```shell
    uv export --only-group unittest --format requirements-txt > requirements_only_unittest.txt`
    uv pip install -r requirements_only_unittest.txt`
    ```



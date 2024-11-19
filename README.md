# python-new-project-setup
A walkthrough for setting up a new python project.

## What is Python ?

Python is a high-level, interpreted programming language known for its readability and simplicity, which makes it accessible to both beginners and experienced developers. Unlike languages that rely on complex syntax with curly braces and semicolons, Python uses indentation to define code blocks, creating a cleaner, more readable structure. It supports multiple programming paradigms—like object-oriented, procedural, and functional programming—making it highly versatile. Additionally, Python is dynamically typed, meaning you don’t have to declare variable types explicitly, which speeds up development but may come at the cost of runtime errors that static typing could catch.

## Why would you want to use Python ?

Python is widely used for its ease of learning, readability, and the extensive ecosystem of libraries that support everything from web development and automation to data science and machine learning. It’s an ideal choice for quickly building and iterating on projects, allowing developers to prototype ideas efficiently. Additionally, Python has a supportive, active community, which provides abundant resources, tutorials, and frameworks that can help streamline the development process, especially for new learners and growing teams.

Python especially excels at **data science, machine learning, and artificial intelligence** due to its extensive libraries (e.g., Pandas, NumPy, TensorFlow) and tools that streamline data processing, analysis, and model building. Additionally, Python is highly effective for rapid prototyping and development in web and software applications, thanks to its readable syntax and frameworks like Django and FastAPI. Python’s simplicity also makes it ideal for automation and scripting, as it allows developers to automate repetitive tasks efficiently across various systems and workflows. Its ease of use and rich library ecosystem empower developers to quickly build and iterate, making Python a strong choice for projects that prioritize speed, flexibility, and a collaborative community. 

## Why wouldn't you want to use Python ? 

You might hesitate to use Python for projects where high performance is essential, as it can be slower than compiled languages like C++ or Java. Additionally, Python’s Global Interpreter Lock (GIL) can limit its efficiency for CPU-bound tasks, and its high memory usage may not be ideal for resource-constrained environments like mobile apps or embedded systems.

## Starting off

Some general tips to know when starting out with Python:
- Use only Python with major version 3.
- Python minor versions (3.9, 3.10, 3.11, ...) are usually released on a yearly basis, and have a 5 year support cycle. More info [here](https://devguide.python.org/versions/)
- When starting a new project you would try to use the newest available minor version, supported by the libraries you use (e.g Databricks Runtime LTS 15.4 uses Python 3.11, Django 5.1 supports Python versions 3.10 - 3.13)
- If a library supports a minor version e.g 3.10 then it supports all its patch versions 3.10.x
- Later we will be installing tools that will install, create and manage python and its virtual environments. It's **very important to use virtual environments** when developing with Python to not polute the global python version and to not have any dependency issues between multiple python projects.
- For installing dependencies the default (but not only. See [poetry](https://python-poetry.org/docs/), [uv](https://docs.astral.sh/uv/) option is to use pip. Pip is the package manager for Python, used to install, upgrade, and manage libraries and dependencies in your Python projects. It simplifies the process of adding third-party packages from the Python Package Index (PyPI) by automatically downloading and installing them along with any required dependencies. With pip, you can install packages using simple commands like pip install package-name, uninstall them, or even specify versions to ensure compatibility. It plays a critical role in Python development by streamlining dependency management, allowing developers to quickly set up environments and install all necessary packages for their projects.

## Installing Python

1. Install [pyenv](https://github.com/pyenv/pyenv?tab=readme-ov-file#getting-pyenv)

`pyenv` lets you install and manage multiple versions of python. You can: 
- view available versions to install with `pyenv install -l`
- install a specific version with `pyenv install 3.11.9`
- set the global system wide python version with `pyenv global 3.11.9`

With pyenv you should install the python version(-s) that you will you in your project(-s).

2. Install [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv)

`pyenv-virtualenv` is a plugin for `pyenv` that lets you create and manage virtual environments for python.

A Python virtual environment is an isolated workspace that allows you to install and manage specific versions of libraries and dependencies separately from the global Python environment on your system. This isolation is crucial because it enables each project to have its own dependencies without conflicts, even if different projects require different versions of the same library.

For example, if one project needs Django 3.2 while another relies on Django 4.0, you can use virtual environments to avoid version clashes. By creating a virtual environment, you ensure that dependencies are isolated, making projects more stable and predictable, especially when sharing code with others or deploying it in different environments. Virtual environments are essential in Python development to maintain consistent setups across projects, minimize dependency issues, and avoid cluttering the system's global Python environment.

To create a virtual environment, we would run `pyenv virtualenv <ALREADY_INSTALLED_PYTHON_VERSION> <MY_ENVIRONMENT_NAME>` e.g `pyenv virtualenv 3.11.9 my-cool-project-be`

## Creating a project

Most of the time, there are 2 ways you could start a project, based on the project size and its needs. 

A simple aproach is to use pyenv-virtualenv to create a virtualenv manualy and use pip to install and manage the dependencies yourself. This can be achieved with the following steps:
- create a new project directory
- cd into the new directory
- run `pyenv virtualenv <YOUR_VERSION> <YOUR_ENV_NAME>` to create the virtual environment
- run `pyenv activate <YOUR_ENV_NAME>` to activate the virtual environment in the current working directory
- use `pip install <DEPENDENCY>` to install any required dependencies
- use `pip freeze > requirements.txt` to list all installed dependencies inside of the virtualenv into a file called 'requirements.txt'
- when sharing the code with others or deploying the code on a server, the recipient would run `pip install -r /path/to/requirements.txt` and run the code, preferably also in a virtualenv
- or the same thing can be done on a docker image and run from a container

Another approach is to use tools like [poetry](https://python-poetry.org/docs/) and [uv](https://docs.astral.sh/uv/) that include additional tools to create and manage virtualenv's for you and also help in building, packaging and publishing your code. Additionally, these tools handle dependencies more efficiently so they are more popular on larger projects. These tools have a similar approach like the above example but use their own cli along with configuration files to achieve the same results. For information on how to use these tools please read the documentation on your own.

## Useful devtools

1. [flake8](https://flake8.pycqa.org/en/latest/) - linter
2. [mypy](https://mypy-lang.org/) - static type checker
3. [black](https://black.readthedocs.io/en/stable/) - formatter
4. [pre-commit](https://pre-commit.com/) - framework for creating and running hooks before commits
5. [isort](https://pycqa.github.io/isort/) - utility to sort and group import statements
   

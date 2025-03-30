uv workflow
============

What is uv
===========
An extremely fast Python package and project manager, written in Rust.
🚀 A single tool to replace pip, pip-tools, pipx, poetry, pyenv, twine, virtualenv, and more.
⚡️ 10-100x faster than pip
Install and manages Python version



Install uv from here: https://github.com/astral-sh/uv

uv documentation: https://docs.astral.sh/uv/getting-started/features/


To list installed python versions on macos
========================================
```sh
$ uv python list
cpython-3.14.0a5+freethreaded-macos-aarch64-none    <download available>
cpython-3.14.0a5-macos-aarch64-none                 <download available>
cpython-3.13.2+freethreaded-macos-aarch64-none      <download available>
cpython-3.13.2-macos-aarch64-none                   <download available>
---
cpython-3.11.5-macos-aarch64-none                   /Users/valentins/.pyenv/versions/3.11.5/bin/python3.11
cpython-3.11.5-macos-aarch64-none                   /Users/valentins/.pyenv/versions/3.11.5/bin/python3 -> python3.11
cpython-3.11.5-macos-aarch64-none                   /Users/valentins/.pyenv/versions/3.11.5/bin/python -> python3.11
```

To install specific python version 
===================================
```sh
$uv python install 3.12
```


init project 
============
```sh
$ uv init example
Initialized project `example` at `/home/user/example`
```

install to project required library 
==================================
```sh
$ uv add boto3
```

Configuration file will list what python version will be used and dependencies needed
==================
```sh
cat pyproject.toml
[project]
name = "boto3-test"
version = "0.1.0"
description = "Add your description here"
readme = "README.md"
requires-python = ">=3.11"
dependencies = [
    "boto3>=1.37.13",
```


after uv init project file structure 
=======================================
```sh
$ ls -la
drwxr-xr-x@  9 valentins  staff   288 Mar 17 12:09 .git
-rw-r--r--@  1 valentins  staff   109 Mar 17 12:05 .gitignore
-rw-r--r--@  1 valentins  staff     5 Mar 17 12:05 .python-version
-rw-r--r--@  1 valentins  staff     0 Mar 17 12:05 README.md
-rwxr-xr-x@  1 valentins  staff   232 Mar 30 00:20 main.py
-rw-r--r--@  1 valentins  staff   179 Mar 17 12:08 pyproject.toml
-rw-r--r--@  1 valentins  staff  4870 Mar 17 12:08 uv.lock
```

To run code with uv - this will download all requred dependency libs and run code 
================
```sh
uv run main.py 
```

Even better shebang for main file can be specified - allows to run ./main.py
===================================================
```
head main.py
#!/usr/bin/env -S uv run --script

import boto3
---
```

!!! Important note after main.py was run  .venv folder with cache will be created 
DO NOT forget to remove it after work completed 


uv-tools
========

ruff-tool  10-100x faster than existing linters (like Flake8) and formatters (like Black)
============
```sh
uvx ruff check
All checks passed!

uvx ruff check   # Lint all files in the current directory.
uvx ruff format  # Format all files in the current directory.
```

docs-tool
=========
```sh
uv tool install mkdocs --with mkdocs-material
uvx --with mkdocs-material mkdocs new .
uvx --with mkdocs-material mkdocs build
uvx --with mkdocs-material mkdocs serve
```

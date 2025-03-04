

# `uv`: A CLI Tool for Creating and Managing Virtual Environments

`uv` is a command-line interface tool designed to simplify the creation and management of virtual environments in Python.

## Adding `pip` to a `uv` Virtual Environment

In some cases, a `uv` virtual environment may not come with `pip` installed. To add `pip` to your `uv` virtual environment, you can use the following command:

```shell
python -m ensurepip --default-pip
```

This command ensures that `pip` is installed in your current Python environment, allowing you to manage packages easily.

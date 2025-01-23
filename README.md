# Example Python Package

This is an example project demonstrating how to build a Python package (wheel or sdist) using [uv](https://docs.astral.sh/uv/) with `pyproject.toml` for configuration.

> [!INFO]
> uv does not currently have a build _backend_ and defaults to using [hatchling](https://hatch.pypa.io/latest/why/#build-backend) for building packages. For most users, this will be sufficient and invisible.

## Commands

### Initialize the Project
Create a new project structure if starting from scratch:

```console
uv init --package demo-uv 
```

### Setup Project Environment 
Install project dependencies and create a virtual environment:

```console
uv sync
```

### Running Code
Execute Python code in the project environment:

```console 
uv run python -c "import demo"
```

### Building

Build both wheel and source distribution:

```console
uv build
```

To build only one format:
```console
uv build --wheel  # Build wheel only
uv build --sdist  # Build source distribution only
```

### Publishing 
Upload built distributions to PyPI:

```console
uv publish
```

For TestPyPI, configure an alternative index in `pyproject.toml`:

```toml
[[tool.uv.index]]
name = "testpypi" 
url = "https://test.pypi.org/simple/"
publish-url = "https://test.pypi.org/legacy/"
```

Then publish using:

```console
uv publish --index testpypi
```

The built distributions will be placed in the `dist/` directory by default.

{{< callout type="info" >}}
Remember to [set up authentication](https://docs.astral.sh/uv/guides/publish/) before publishing. Use `UV_PUBLISH_TOKEN` environment variable or the `--token` flag to provide your PyPI API token.
{{< /callout >}}
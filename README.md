# elixir-pre-commit-hooks

[Pre-commit](https://pre-commit.com/) hooks for Elixir.

## Usage

You'll need to have both mix and [pre-commit](https://pre-commit.com/) installed (meaning you'll need to have Python installed also, since `pre-commit` is a Python package). I'd recommend installing `pre-commit` with [pipx](https://pipxproject.github.io/pipx/), so that it's globally available across all your projects. See [pre-commit's documentation](https://pre-commit.com/#install) for more detailed installation and usage instructions.

Add the following to your .pre-commit-config.yaml:
```yaml
repos:
  - repo: https://gitlab.com/jvenom/elixir-pre-commit-hooks
    rev: v1.0.0 # replace with the version you want to use
    hooks: # specify the hooks you want to use here
      - id: mix-format
      - id: mix-test
```

Install the hooks:
```
$ pre-commit install
```

## Available Hooks

#### `mix-format`
Runs `mix format` when an `.ex` or `.exs` file is included in the commit.

#### `mix-test`
Runs `mix test` when an `.ex` or `.exs` file is included in the commit.

## Passing Options to Hooks

If you want to pass additional options to the hook, you can include an `args` key in the hook's configuration in .pre-commit-config.yaml. The value of the key should be a list of the arguments you want to pass.
```yaml
hooks:
  - id: mix-test
    args: [--trace, --exclude, my-exclude-filter]
```

## Other Projects

[elixir-pre-commit](https://github.com/dwyl/elixir-pre-commit) is an Elixir module that provides a pure-Elixir implementation of pre-commit Git hooks. You might want to use that if you only want mix tasks as your pre-commit hooks. If you want to use other, non-mix pre-commit hooks (like [these](https://github.com/pre-commit/pre-commit-hooks)) _and_ mix tasks, you should use this repo.

# Yamllint Composite Action

A [GitHub composite action][gh-composite-action] to run [yamllint][yamllint], a linter for YAML files.

[gh-composite-action]: https://docs.github.com/en/actions/creating-actions/creating-a-composite-action
[yamllint]: https://yamllint.readthedocs.io/en/stable/index.html

## Usage

A simplified example on how this action can be utilized, could look like this.

```yaml
on: [pull_request]

jobs:
  lint_yaml:
    runs-on: ubuntu-latest
    name: Lint YAML files
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Lint YAML
        id: yamllint
        uses: beiertu/yamllint-composite-action@master

      - name: Use linter output
        run: echo ${{ steps.yamllint.outputs.lint_output }}
```

### Version

This action also provide specific versions to be used with. For example

```yaml
- uses: beiertu/yamllint-composite-action@v1.0.0
```

See [this action releases][releases] for all available versions.

[releases]: https://github.com/beiertu-mms/yamllint-composite-action/releases

## Inputs

This action accepts the following inputs.

| Name            | Description                                                                                 | Required |          Default          |
|-----------------|---------------------------------------------------------------------------------------------|:--------:|:-------------------------:|
| `files_or_dirs` | A space separated list of files or directories to be linted                                 |    no    | current working directory |
| `config_file`   | Path to a custom configuration file                                                         |    no    |            ""             |
| `config_data`   | Custom configuration (as YAML source)                                                       |    no    |            ""             |
| `strict`        | Return non-zero exit code on warnings as well as errors                                     |    no    |           false           |
| `no_warnings`   | Output only error level problems                                                            |    no    |           false           |
| `format`        | The format for parsing output. Available options: parsable, standard, colored, github, auto |    no    |           auto            |

## Outputs

This action returns the following outputs.

| Name          | Description                |
|---------------|----------------------------|
| `lint_output` | Result from yamllint check |

## License

Distributed under the MIT License. See [LICENSE](./LICENSE) for more information.

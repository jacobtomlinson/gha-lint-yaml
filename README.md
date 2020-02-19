# YAML linter Action

[![GitHub Marketplace](https://img.shields.io/badge/Marketplace-Lint%20YAML-blue.svg?colorA=24292e&colorB=0366d6&style=flat&longCache=true&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAYAAAAfSC3RAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAM6wAADOsB5dZE0gAAABl0RVh0U29mdHdhcmUAd3d3Lmlua3NjYXBlLm9yZ5vuPBoAAAERSURBVCiRhZG/SsMxFEZPfsVJ61jbxaF0cRQRcRJ9hlYn30IHN/+9iquDCOIsblIrOjqKgy5aKoJQj4O3EEtbPwhJbr6Te28CmdSKeqzeqr0YbfVIrTBKakvtOl5dtTkK+v4HfA9PEyBFCY9AGVgCBLaBp1jPAyfAJ/AAdIEG0dNAiyP7+K1qIfMdonZic6+WJoBJvQlvuwDqcXadUuqPA1NKAlexbRTAIMvMOCjTbMwl1LtI/6KWJ5Q6rT6Ht1MA58AX8Apcqqt5r2qhrgAXQC3CZ6i1+KMd9TRu3MvA3aH/fFPnBodb6oe6HM8+lYHrGdRXW8M9bMZtPXUji69lmf5Cmamq7quNLFZXD9Rq7v0Bpc1o/tp0fisAAAAASUVORK5CYII=)](https://github.com/jacobtomlinson/gha-lint-yaml)
[![Actions Status](https://github.com/jacobtomlinson/gha-lint-yaml/workflows/Lint/badge.svg)](https://github.com/jacobtomlinson/gha-lint-yaml/actions)
[![Actions Status](https://github.com/jacobtomlinson/gha-lint-yaml/workflows/Integration%20Test/badge.svg)](https://github.com/jacobtomlinson/gha-lint-yaml/actions)

This action will lint YAML files in your project.

## Usage

Describe how to use your action here.

### Example workflow

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: Run action
      uses: jacobtomlinson/gha-lint-yaml@master
      with:
        path: path/to/my/yaml/file.yaml
```

### Inputs

| Input                                             | Description                                        |
|------------------------------------------------------|-----------------------------------------------|
| `path`  | Path to the YAML file to be linted.    |
| `strict` _(optional)_  | Run the linter in strict mode (error on warnings).    |

### Outputs

| Output                                             | Description                                        |
|------------------------------------------------------|-----------------------------------------------|
| `warnings`  | The number of warnings raised if successful.    |

## Examples

### Running in strict mode

Here is an example of a very strict linting job.

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Run action
      uses: jacobtomlinson/gha-lint-yaml@master
      with:
        path: path/to/my/yaml/file.yaml
        strict: true
```

### Using outputs

Here is an example of using the warnings outputs.

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Run action
      id: yamllint
      uses: jacobtomlinson/gha-lint-yaml@master
      with:
        path: path/to/my/yaml/file.yaml

    - name: Check outputs
      run: |
        echo "There were ${{ steps.yamllint.outputs.warnings }} YAML linting warnings."
```

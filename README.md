# Workflows

My collection of GitHub Actions workflows.

## Structure

- `.github/workflows/` - GitHub Actions workflow files

## Usage

Place your GitHub Actions workflow YAML files in `.github/workflows/` directory.

### Example workflow

```yaml
name: My Workflow
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run a script
        run: echo "Hello, world!"
```

## Documentation

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow syntax reference](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)

## License

See [LICENSE](LICENSE) file for details.

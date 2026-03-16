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

## Workflows

### Release and Publish ([`release-and-publish.yml`](.github/workflows/release-and-publish.yml))

A reusable workflow for releasing and publishing packages to NPM.

**Features:**
- ✅ Supports npm, pnpm, yarn (auto-detected)
- ✅ Tag validation (v{major}.{minor}.{patch}[-{prerelease}])
- ✅ Automatic npm dist-tags (latest, next)
- ✅ GitHub Release creation with auto-generated notes
- ✅ Prerelease detection

**Usage in your repos:**

Create `.github/workflows/release.yml`:

```yaml
name: Release

on:
  push:
    tags:
      - "v*.*.*"
      - "v*.*.*-*"

jobs:
  release:
    uses: lalexdotcom/workflows/.github/workflows/release-and-publish.yml@main
    secrets: inherit
    with:
      publish: true
```

**Requirements:**
- `package.json` with version field
- `build` script in package.json (e.g., `"build": "...your build command..."`)
- `NPM_TOKEN` secret configured in your repo (for NPM publish)

**Inputs:**
- `npm-registry` (optional, default: `https://registry.npmjs.org`)
- `publish` (optional, default: `true` - set to `false` to skip NPM publish)

## Documentation

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow syntax reference](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- [Reusable workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows)

## License

See [LICENSE](LICENSE) file for details.

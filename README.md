# action-restrict-head-branch

[![license](https://img.shields.io/badge/License-MIT-green.svg)](https://github.com/praha-inc/action-restrict-head-branch/blob/main/LICENSE)
[![Github](https://img.shields.io/github/followers/praha-inc?label=Follow&logo=github&style=social)](https://github.com/orgs/praha-inc/followers)

Restrict pull requests to only be able to be created on specific branches.

## 👏 Getting Started

Create a workflow file under ```.github/workflows``` directory.

```yaml
name: Restrict head branch
on:
  pull_request_target:
    types: [opened, edited, synchronize]

jobs:
  restrict-head-branch:
    runs-on: ubuntu-latest
    permissions:
      pull-requests: write
    steps:
      - uses: praha-inc/action-restrict-head-branch@v1
        with:
          rules: |
            main staging development
            feature/* bugfix/* refactor/* chore/* deps/*
```

## 🔧 Configurations

### `rules`

A list of rules that restrict pull requests to be created from only certain branches.

Each rule is a list of branch patterns separated by spaces.

If you want to create pull requests only from the main, staging, and development branches, configure as follows.

```yaml
rules: |
  main staging development
```

You can also use Glob to specify the branch name.

[Minimatch](https://github.com/isaacs/minimatch) is used for the matching process.

If you want to create only pull requests from feature and bug fix branches, configure as follows.

```yaml
rules: |
  feature/* bugfix/*
```

Also, line breaks can be inserted for readability, as shown below.

```yaml
rules: |
  main staging development
  feature/* bugfix/* refactor/* chore/* deps/*
```

This is equivalent to the following rule.

```yaml
rules: |
  main staging development feature/* bugfix/* refactor/* chore/* deps/*
```

## 🤝 Contributing

Contributions, issues and feature requests are welcome.

Feel free to check [issues page](https://github.com/praha-inc/action-restrict-head-branch/issues) if you want to contribute.

## 📝 License

Copyright © 2024 [PrAha](https://www.praha-inc.com/).

This project is [```MIT```](https://github.com/praha-inc/action-restrict-head-branch/blob/main/LICENSE) licensed.

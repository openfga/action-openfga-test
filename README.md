# OpenFGA Github Action - Test

[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fopenfga%2Faction-openfga-test.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fopenfga%2Faction-openfga-test?ref=badge_shield)

This action can be used to test your authorization model using store test files.

## Parameter

| Parameter            | Description                                                                                                                                                   | Required | Default      |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|--------------|
| `test_path`          | The path to your store test file or folder relative to the root of your project.                                                                              | No       | `.`          |
| `test_files_pattern` | The pattern to match test files.                                                                                                                              | No       | `*.fga.yaml` |
| `fga_server_url`     | The OpenFGA server to test the Authorization Model against. If empty (which is the default value), the tests are run using the cli built-in OpenFGA instance. | No       | _empty_      |
| `fga_api_token`      | The api token to use for testing against an OpenFGA server. Ignored if `fga_server_url` is not provided.                                                      | No       | _empty_      |

> Note: the action will fail if no test is found in the specified test path with the given pattern

## Examples

### Running tests of `*.fga.yaml` files present in the repository

```yaml
name: Test Action

on:
  workflow_dispatch:

jobs:
  test:
    name: Run test
    runs-on: ubuntu-latest
    steps:
      - uses: openfga/action-openfga-test@v0.1
```

### Running tests of `*.fga.yaml` files present in a given folder

```yaml
name: Test Action

on:
  workflow_dispatch:

jobs:
  test:
    name: Run test
    runs-on: ubuntu-latest
    steps:
      - uses: openfga/action-openfga-test@v0.1.0
        with:
          test_path: example
```

### Running tests of a single file

```yaml
name: Test Action

on:
  workflow_dispatch:

jobs:
  test:
    name: Run test
    runs-on: ubuntu-latest
    steps:
      - uses: openfga/action-openfga-test@v0.1
        with:
          test_path: example/model.fga.yaml
```

### Running tests against a given version of OpenFGA

```yaml
name: Test Action

on:
  workflow_dispatch:

jobs:
  test:
    name: Run test
    runs-on: ubuntu-latest
    services:
      postgres:
        image: postgres:14
        env:
          POSTGRES_USER: openfga
          POSTGRES_PASSWORD: '1234'
        ports:
          - 5432:5432
        options: --health-cmd pg_isready --health-interval 10s --health-timeout 5s --health-retries 5
    env:
      OPENFGA_DATASTORE_ENGINE: 'postgres'
      OPENFGA_DATASTORE_URI: 'postgres://openfga:1234@127.0.0.1:5432/openfga'
      OPENFGA_LOG_LEVEL: debug
    steps:
      - name: Install OpenFGA server v1.5.3
        uses: jaxxstorm/action-install-gh-release@v1.11.0
        with:
          repo: openfga/openfga
          tag: v1.5.3
          cache: enable
      - name: Migrate OpenFGA database
        shell: bash
        run: openfga migrate
      - name: Start OpenFGA server in background
        shell: bash
        run: openfga run &
      - name: Run tests
        uses: openfga/action-openfga-test@v0.1
        with:
          fga_server_url: 'http://localhost:8080'
```

## License

[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fopenfga%2Faction-openfga-test.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fopenfga%2Faction-openfga-test?ref=badge_large)

# OpenFGA Github Action - Test
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fopenfga%2Faction-openfga-test.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fopenfga%2Faction-openfga-test?ref=badge_shield)


This action can be used to test your authorization model using a store file.

## Parameter

| Parameter  | Description   |
|----------|--------------|
| `store-file-path` | The path to your store file relative to the root of your project     | 

## Example

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
          store-file-path: ./example/model.fga.yaml
```


## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fopenfga%2Faction-openfga-test.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fopenfga%2Faction-openfga-test?ref=badge_large)

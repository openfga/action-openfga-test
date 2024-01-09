# OpenFGA Github Action - Test

This action can be used to test your authorization model using a store file.

## Parameter

| Parameter  | Description   |
|----------|--------------|
| The path to your store file relative to the root of your project     | 

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
      - uses: actions/checkout@v4
      - uses: openfga/action-openfga-test
        with:
          store-file-path: ./example/model.fga.yaml
```

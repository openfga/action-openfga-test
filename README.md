# OpenFGA Github Action - Test

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
      - uses: openfga/action-openfga-test@v0.1
        with:
          store-file-path: ./example/model.fga.yaml
```

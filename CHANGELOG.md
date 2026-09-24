# Changelog

## [0.1.3](https://github.com/openfga/action-openfga-test/compare/v0.1.2...v0.1.3) (2026-09-24)


### Added

* support `allow-external-files` flag ([4090fa6](https://github.com/openfga/action-openfga-test/commit/4090fa6439a9b7613ae1ea026a17af70fc51e347))

### Fixed

* update floating references to pinned and wrap inside tag ([ab5748c](https://github.com/openfga/action-openfga-test/commit/ab5748c6c09f24bf1cb1f92a5a702e9d3f6c2f17))

## [0.1.2](https://github.com/openfga/action-openfga-test/compare/v0.1.1...v0.1.2) (2025-11-05)


### Added

* Ability to specify the FGA CLI version via `fga_cli_version` input parameter ([#33](https://github.com/openfga/action-openfga-test/issues/33)) - thanks @Angelchev

## [0.1.1](https://github.com/openfga/action-openfga-test/compare/v0.1.0...v0.1.1) (2024-06-03)


### Added

* Support running tests against a configurable external fga server ([#11](https://github.com/openfga/action-openfga-test/issues/11)) - thanks @le-yams. Note that when running against an external server, the model defined in the file is ignored, and the tuples are limited to 20
* Support multiple test files ([#8](https://github.com/openfga/action-openfga-test/issues/8)) - thanks @le-yams. This adds support for 2 optional parameters that specify what tests the action will run: `test_path` to specify a test file or folder (default value `.`) and `test_files_pattern` to specify the pattern used to match test files (default value `*.fga.yaml`)

## [0.1.0](https://github.com/openfga/action-openfga-test/releases/tag/v0.1.0) (2024-01-09)


Initial OpenFGA Test Action release.

This action can be used to run tests against an OpenFGA store file with a model.

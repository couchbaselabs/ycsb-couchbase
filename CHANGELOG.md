# Changelog

All notable changes to this project will be documented in this file.

## [Unreleased]

### Added

- Nothing was added in this release

### Changed

- Updated Couchbase Java SDK (java-client) to 3.13.1
- Updated dcp-client to 0.58.0
- Updated reactor-core to 3.6.9 and reactor-extra / reactor-adapter to 3.5.2 to match the SDK

### Fixed

- No bug fixes in this release

### Removed

- Nothing was removed in this release

## [2.0.5]

### Added

- Nothing was added in this release

### Changed

- Changed scan logic
- Updated Couchbase SDK driver revision to current

### Fixed

- No bug fixes in this release

### Removed

- Nothing was removed in this release

## [2.0.4]

### Added

- Added Certificate Auth (mTLS) support for Couchbase
- Added the ability to provide the CA certificate for Couchbase (which enables cert validation)

### Changed

- Changed the scan method logic in the Couchbase driver

### Fixed

- Fixed issue where Couchbase Workload E would not log errors
- Fixed issue with non-default scopes and collections

### Removed

- Nothing was removed in this release

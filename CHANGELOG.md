# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/)
and this project adheres to [Semantic Versioning](http://semver.org/).

## 2.0.6 - 2017-05-27
### Changed

* Fix for https://github.com/rust-lang/rust/pull/42125

## 2.0.5 - 2017-05-15
### Changed

* Relicense under MPL/Apache/MIT

## 2.0.4 - 2017-05-05
### Fixed

* Documentation improvements

## 2.0.3 - 2017-05-05
### Fixed

* Documentation fixes

## 2.0.2 - 2017-04-12
### Fixed

* Compile time logging level filtering

## 2.0.0 - 2017-04-11
### Changed (since v1; bigger picture)

* Unified and simplified logging macros structure and ordering.
* Added logging Record `tags`.
* Refactored key-value pairs traits and structures and overall handling.
  * It's now possible to `impl KV for MyStruct`.
  * `kv!` can be used to create on stack key-value list.
  * `KV`-implementing data can appear on the key-value list directly.
* Support chaining of `OwnedKVList`s. Existing `Logger` can be used as a `Drain`
  to allow custom handling logic for a part of the logging hierarchy.
* Added associated `Ok` type to `Drain`.
* Support for `Drain`s unwind safety.
* Refactored `Record` to optimize performance on async operations.
* `slog-extra` has been renamed to `slog-async` since that's the only functionality it contained.
* `slog-stream` is obsoleted and won't be used in `slog v2` at all. It was a wrong abstraction.
  `Decorators` functionality was moved to `slog-term`.
* `slog-term` provides open `Decorator` traits to allow multiple terminal / file writing backends.
* `slog-term` default `Decorator`s use `term` crate and should work correctly on all supported OSes.
* `DrainExt` has been removed and utility methods moved directly to `Drain`
* `slog-stdlog` utilizes `slog-scope` directly.
* Support for "typed" `Logger`s to allow squeezing last drops of performance possible,
  at the cost of `T` in `Logger<T>`.

## 2.0.0-3.1 - 2017-03-25
### Added

* Support for `fmt::Display` values with `%` in `kv!`


## 2.0.0-3.0 - 2017-03-25
### Changed

* Added support for own `KV` and `Value` implementations
* Streamlined the formatting syntax for `log!` and friends; **BREAKING**
* Lazy values need explicit `FnValue` wrapper; **BREKING**

### Added

* `kv!` macro

## 2.0.0-2.2 - 2017-03-19
### Fixes

* Bunch of trait-related fixes

## 2.0.0-2.1 - 2017-03-11
### Fixed

* Require `MapErr` and `Filter` to be `UnwindSafe`

## 2.0.0-2.0 - 2017-03-11
### Changed

* Make `Logger::root` return "erased" version
* Introduce `Logger::root_typed` for "non-erased" `Logger` creation

## 2.0.0-1.0 - 2017-02-23

### Fixed

* `fmt::Debug` for `MutexDrainError`

### Changed
* Parametrize `Logger` over the `Drain` it holds and introduce "erased" version
* Enforcing `UnwindSafe` `Drain`s for `Logger`s
* Refactored key-value pairs traits and structures
* Renamed some types
* Support chaining of `OwnedKVList`s
* Added associated `Ok` type to `Drain`
* Refactored `Record` to optimize performance on async
  operations
* Minimal rustc version required: `1.15.0`
* `DrainExt` has been removed and utility methods moved directly to `Drain`

### Added

* Macros to create `OwnedKV` and `BorrowedKV`
* `Logger` implements `Drain`

## 1.5.0 - 2017-01-19
### Changed

* Order of key-value pairs is now strictly defined

### Added

* `Logger` implements `Drain`

### Deprecated

* Creation of `OwnedKeyValueList`

## 1.4.1 - 2017-01-19
### Fixed

* Fix an invalid syntax exposed by nightly rust change (Issue #103)

## 1.4.0 - 2016-12-27
### Changed

* Updated documentation

### Deprecated

* `OwnedKeyValueList::id`

## 1.3.2 - 2016-11-19
### Added

* `slog_o` as an alternative name for `o`

## 1.3.1 - 2016-11-19
### Fixed

* Cargo publishing mistake.

## 1.3.0 - 2016-10-31
### Changed

* **BREAKING**: Removed default `Send+Sync` from `Drain`

## 1.2.1 - 2016-10-27
### Added

* `OwnedKeyValueList::id` for owned key value unique identification

## 1.2.0 - 2016-10-21
### Changed

* **BREAKING**: `Serializer` takes `key : &'static str` now

### Fixed

* Corner cases in `info!(...)` and other macros

## 1.1.0 - 2016-10-17
### Changed

* **BREAKING**: Rewrite handling of owned values.

## 1.0.1
### Fixed

* `use std` in `o!`

### Added

* Implement `fmt::Debug` for `Logger`

## 1.0.0 - 2016-09-21

First stable release.

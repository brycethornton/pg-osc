## [0.9.2] - 2023-07-03

- Dependency updates
- Create shadow and audit with auatovacuum default turned off. Should avoid lock queues when disabling vacuum on audit table. #97
## [0.9.1] - 2023-06-24

- Dependency updates and refresh docker release process with multi-platform build

## [0.9.0] - 2023-05-22

- Fix typo in README.md https://github.com/shayonj/pg-osc/pull/87
- Support for views https://github.com/shayonj/pg-osc/pull/88

## [0.8.1] - 2023-05-13

- Gem path and CI fixes

## [0.8.0] - 2023-05-13

- Ruby 3.1.3 and prettier/ruby https://github.com/shayonj/pg-osc/pull/83
- Ruby matrix in ci and require ruby 2.7+ https://github.com/shayonj/pg-osc/pull/84
- Re-enable autovacuum by @jfrost https://github.com/shayonj/pg-osc/pull/85

## [0.7.5] - 2023-03-12

- Bump google-protobuf from 3.21.6 to 3.21.7 https://github.com/shayonj/pg-osc/pull/76
- Supports tablenames containing uppercase letters https://github.com/shayonj/pg-osc/pull/77
- Update rubocop todo https://github.com/shayonj/pg-osc/pull/78
- Ensure original triggers are carried over from parent table https://github.com/shayonj/pg-osc/pull/79

## [0.7.4] - 2022-09-24

- off-by-one: Don't skip PK sequence value by one https://github.com/shayonj/pg-osc/pull/74

## [0.7.3] - 2022-09-24

- Update primary key sequence on shadow table https://github.com/shayonj/pg-osc/pull/72
  - Thanks to @brycethornton for the report
- Only refresh primary key when a sequence is attached https://github.com/shayonj/pg-osc/pull/73

## [0.7.2] - 2022-09-17

**NOTE: Skip to 0.7.3. 0.7.2 release missed the change.**

- Update primary key sequence on shadow table https://github.com/shayonj/pg-osc/pull/72
  - Thanks to @brycethornton for the report

## [0.7.1] - 2022-03-13

- Bump pg to `1.3.4` https://github.com/shayonj/pg-osc/commit/d086c19d4f273dc960491cbedf9e0602d812896b

## [0.7.0] - 2022-03-13

- Move CI to Github Actions in https://github.com/shayonj/pg-osc/pull/64
- Set --password as optional since it is deprecated in https://github.com/shayonj/pg-osc/pull/66
- Smoke tests in https://github.com/shayonj/pg-osc/pull/65
- Add foreign keys to parent during swap in https://github.com/shayonj/pg-osc/pull/67

## [0.6.0] - 2022-02-26

- Delete items by audit table PK when replaying by @shayonj @jfrost in https://github.com/shayonj/pg-osc/pull/60
  - Fixes a race condition issue: https://github.com/shayonj/pg-osc/issues/58

## [0.5.0] - 2022-02-26

- Share some preliminary load test figures in https://github.com/shayonj/pg-osc/pull/54
- Reuse existing transaction open for reading table columns in https://github.com/shayonj/pg-osc/pull/53
- Start to deprecate --password with PGPASSWORD in https://github.com/shayonj/pg-osc/pull/56
- Introduce configurable PULL_BATCH_COUNT and DELTA_COUNT in https://github.com/shayonj/pg-osc/pull/57

## [0.4.0] - 2022-02-22

- Lint sourcecode, setup Rubocop proper and Lint in CI by @shayonj in https://github.com/shayonj/pg-osc/pull/46
- Uniquely identify operation_type column by @shayonj in https://github.com/shayonj/pg-osc/pull/50
- Introduce primary key on audit table for ordered reads by @shayonj in https://github.com/shayonj/pg-osc/pull/49
  - This addresses an edge case with replay.
- Uniquely identify trigger_time column by @shayonj in https://github.com/shayonj/pg-osc/pull/51
- Abstract assertions into a helper function by @shayonj in https://github.com/shayonj/pg-osc/pull/52

## [0.3.0] - 2022-02-21

- Explicitly call dependencies and bump dependencies by @shayonj https://github.com/shayonj/pg-osc/pull/44
- Introduce Dockerfile and release process https://github.com/shayonj/pg-osc/pull/45

## [0.2.0] - 2022-02-17

- Use ISOLATION LEVEL SERIALIZABLE ([#42](https://github.com/shayonj/pg-osc/pull/42)) (props to @jfrost)

## [0.1.0] - 2022-02-16

Initial release

pg-online-schema-change (`pg-osc`) is a tool for making schema changes (any `ALTER` statements) in Postgres tables with minimal locks, thus helping achieve zero downtime schema changes against production workloads.

`pg-osc` uses the concept of shadow table to perform schema changes. At a high level, it copies the contents from a primary table to a shadow table, performs the schema change on the shadow table and swaps the table names in the end while preserving all changes to the primary table using triggers (via audit table).

Checkout [Readme](https://github.com/shayonj/pg-osc#readme) for more details.

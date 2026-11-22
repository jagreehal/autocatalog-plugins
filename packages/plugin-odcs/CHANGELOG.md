# autocatalog-plugin-odcs

## 0.1.0

### Minor Changes

- 2185135: New plugin `autocatalog-plugin-odcs`.

  - `ac from-odcs` writes the tables each contract declares into `.autocatalog/models.json`, so the scan publishes them as table resources. A server `schema` qualifies the table id. Naming contracts replaces only their tables. A failed run writes nothing. A contract or product without `status` reads, as ODCS and ODPS allow.
  - `--base` pairs contracts by id and major version, fails on a base contract that does not read or is declared twice, and fails a breaking change released under too small a version bump, or a contract removed before it was retired.
  - `--check` fails when the committed models are stale.
  - `--consumers <checkouts...>` checks other repositories' expected contracts and names the consumer a change breaks. A data product that does not read fails the run, as does an ODPS input pinned to a contract version no data product publishes.

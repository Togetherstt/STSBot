# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog, and this project currently follows a simple manual versioning flow.

## [0.1.0] - 2026-06-05

### Added

- Extracted the standalone `STSBot` project from the larger private bot workspace.
- Added the `sts_card_guess` NoneBot2 plugin as an independent open-source unit.
- Included built-in `Slay the Spire 2` card JSON data for local use.
- Added a local interactive test script for manual gameplay verification.
- Added unit tests covering repository loading, hints, reveal logic, and command parsing.
- Added independent project scaffolding, including `bot.py`, `pyproject.toml`, `requirements.txt`, `.env.example`, and `README.md`.
- Added repository metadata files for open-source publishing: `.gitignore` and `LICENSE`.

### Changed

- Polished the public README for standalone GitHub release and deployment guidance.

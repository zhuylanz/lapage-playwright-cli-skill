# Changelog

All notable changes to `lapage-playwright-cli` are recorded here.

## [1.0.0] - 2026-10-22

### Added

- Published the LaPage Digital distribution of the Playwright CLI agent skill, based on `@playwright/cli` 0.1.15.
- Added `scripts/check-update.mjs`, which compares the installed version with the version published on GitHub and caches the result for 24 hours.
- Added LaPage browser profile conventions: in-memory profiles for anonymous work and a shared persistent profile for logged-in services.
- Added headed-mode guidance and a pointer to the upstream repository for undocumented options.

# Changelog

All notable changes to this plugin are documented here. The format follows
Keep a Changelog, and the release workflow publishes each version's section
as its GitHub release notes.

## [Unreleased]

## [0.3.1] - 2026-09-20

- Development installs (built from `dist/dev` via `scripts/package.py` or the Nix `default.nix`) now stamp themselves with an identifiable version like `X.Y.Z-dev.<commit>` (with a `.dirty` suffix for uncommitted changes), so a dev build can be told apart from a real release without touching the tracked plugin version. Release packaging still requires a clean checkout at the exact `vX.Y.Z` tag.
- Refreshed the README and screenshot to reflect the AI chat search engines added in 0.3.0.

## [0.3.0] - 2026-06-01

- Added three AI chat engines alongside the existing web search engines: T3 Chat (`t3`), ChatGPT (`gpt`), and Claude (`cl`), so typing a prefixed query from the launcher opens a new chat with that prompt instead of only searching the web.
- Updated the README and screenshot to document the new AI chat prefixes.

## [0.2.1] - 2026-05-03

- Fixed the Nix installation snippet in the README: the option is `programs.dank-material-shell.plugins.dankQuickSearch` (camelCase plugin id), not `DankQuickSearch`, so following the documented example now actually enables the plugin.
- Documented the dev/main release workflow and a docs-only release exception in the contribution guide.

## [0.2.0] - 2026-04-23

- Renamed the plugin from DankWebSearch to DankQuickSearch to avoid confusion with another, more feature-rich "Web Search" plugin, and trimmed it down to four search engines (DuckDuckGo, Google, GitHub, YouTube), dropping Wikipedia to keep it minimal.
- Added a screenshot to the README.
- Moved the version to `plugin.json` as the single source of truth, removing the separate `VERSION` file so CI, the Nix flake, and the test suite can no longer drift out of sync when bumping a release.
- Added a 17-test suite (`test.sh`) covering `plugin.json` validation, plugin id consistency, engine definitions, and URL construction.
- Added a collapsible Support section to the README with crypto donation addresses.

## [0.1.1] - 2026-04-22

- Fixed multi-character engine prefixes such as `!yt` and `!gh`, which the DMS launcher's built-in text-matching scorer was silently filtering out because they didn't look like a match for the typed query. Trigger-activated results are now marked as pre-scored so the launcher shows them regardless of the scorer's text match.

## [0.1.0] - 2026-04-22

- Initial release: a launcher plugin for DankMaterialShell that adds web search from the DMS launcher, triggered with `!`.
- Supports DuckDuckGo, Google, Wikipedia, GitHub, and YouTube, each reachable via its own prefix (e.g. `g` for Google, `w` for Wikipedia, `gh` for GitHub, `yt` for YouTube), plus a configurable default engine used when no prefix is given.
- Detects and opens direct URLs typed into the launcher instead of searching for them.

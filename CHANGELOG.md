# Changelog

## Unreleased

- Added a `colored-output` setting which sets `DOTNET_SYSTEM_CONSOLE_ALLOW_ANSI_COLOR_REDIRECTION` and `TERM` to force color output. This is set to `true` by default.

## 1.1.0

- List installed SDKs after running `actions/setup-dotnet`

## 1.0.0

- Use `actions/setup-dotnet` 2.0.0
- Set `DOTNET_INSTALL_DIR` based on the OS
  - Prevents pre-installed SDKs from being downloaded and installed a second time
  - Fixes the issue of losing access to pre-installed SDKs after installing a new one
- Strip comments from the `global.json` so `actions/setup-dotnet` can read the SDK version from it

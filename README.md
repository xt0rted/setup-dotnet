# setup-dotnet

A wrapper around the official [actions/setup-dotnet](https://github.com/actions/setup-dotnet) action with extra features that aren't yet implemented.

1. Sets `DOTNET_INSTALL_DIR` based on the OS so existing sdks are used when available (https://github.com/actions/setup-dotnet/issues/284, https://github.com/actions/setup-dotnet/pull/208)
2. Strips comments from the `global.json` before calling `actions/setup-dotnet` and then restores them (https://github.com/actions/setup-dotnet/pull/257)
3. Sets `DOTNET_SYSTEM_CONSOLE_ALLOW_ANSI_COLOR_REDIRECTION` and `TERM` to force color output by default (https://github.com/actions/setup-dotnet/issues/288).

## Usage

Basic usage with SDK version from the `global.json`.

```yml
- name: Set up .NET
  uses: xt0rted/setup-dotnet@v1.0.0
```

Specifying a single SDK version to use.

```yml
- name: Set up .NET
  uses: xt0rted/setup-dotnet@v1.0.0
  with:
    dotnet-version: 6.0.201
```

Specifying multiple SDK versions to use.

```yml
- name: Set up .NET
  uses: xt0rted/setup-dotnet@v1.0.0
  with:
    dotnet-version: |
      3.1.417
      5.0.406
      6.0.201
```

Specifying a custom source and auth token.

```yml
- name: Set up .NET
  uses: xt0rted/setup-dotnet@v1.0.0
  with:
    source-url: https://nuget.pkg.github.com/xt0rted/index.json
    nuget_auth_token: ${{ secrets.GITHUB_TOKEN }}
```

## Options

Name | Default value | Description
-- | -- | --
`colored-output` | `true` | Sets the required environment variables to force color output from dotnet.
`nuget_auth_token` | `""` | Optional authentication token used with `source-url`.
`strip-comments-from-global-json` | `true` | Whether to strip comments from the `global.json` file.

> ℹ️ This action requires passing `nuget_auth_token` as an input not an environment variable.

All inputs supported by `actions/setup-dotnet` are supported and passed through to it.
The full list of supported inputs can be seen in the [action.yml](action.yml) file.

## Known issues

1. The step to strip comments from the `global.json` file uses [`npx`](https://docs.npmjs.com/cli/v8/commands/npx) and requires Node.js 16 or newer to work. If you're using an older version of node and don't need this step to run you can disable it with the `strip-comments-from-global-json` setting.

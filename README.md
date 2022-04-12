# setup-dotnet

A wrapper around the official [ations/setup-dotnet](https://github.com/actions/setup-dotnet) action with extra features that aren't yet implemented.

1. Sets `DOTNET_INSTALL_DIR` based on the OS so existing sdks are used when available (https://github.com/actions/setup-dotnet/issues/284, https://github.com/actions/setup-dotnet/pull/208)
2. Strips comments from the `global.json` before calling `actions/setup-dotnet` and then restores them (https://github.com/actions/setup-dotnet/pull/257)

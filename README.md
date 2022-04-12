# setup-dotnet

A wrapper around the official actions/setup-dotnet action with extra features.

1. Sets `DOTNET_INSTALL_DIR` based on the OS so existing sdks are used when available.
2. Strips comments from the `global.json` before calling `actions/setup-dotnet` and then restores them.

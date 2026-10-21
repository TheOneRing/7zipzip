# 7zipzip

Repackaged `7za.exe` for use in CI.

A GitHub Action watches [ip7z/7zip](https://github.com/ip7z/7zip/releases) for new releases and republishes the standalone `7za.exe` from the `-extra` package as one small zip per architecture.

## Releases

Each release is tagged like the upstream release and contains:

- `7zip-extra-<tag>-x86.zip`
- `7zip-extra-<tag>-x86_64.zip`
- `7zip-extra-<tag>-arm64.zip`
- `SHA256.txt` with the checksums of the zips

Each zip contains only `7za.exe` and `License.txt`. `7za.exe` is self-contained, so the DLLs, help file, history, readme and Far plugin from the upstream package are left out.

## How it works

`.github/workflows/repackage.yml` runs every 6 hours and can be started manually with an optional upstream tag. It skips tags that already have a release here.

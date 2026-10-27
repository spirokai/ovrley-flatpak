# OVRLEY Flatpak repository

Flatpak repository for [OVRLEY](https://github.com/spirokai/OVRLEY), served at https://flatpak.ovrley.cc/.

## Install

```bash
flatpak install --user https://flatpak.ovrley.cc/ovrley.flatpakref
```

Updates then arrive through `flatpak update` or your software centre. The `.flatpak` bundles attached to OVRLEY releases update from this repository too.

## How it works

`.github/workflows/publish.yml` checks OVRLEY's releases every six hours (or on demand from the Actions tab). When the newest published release carries a newer `OVRLEY-linux-*.flatpak` than the live repository, it imports that bundle into a fresh OSTree repository, signs it and deploys it to GitHub Pages.

The repository is signed with the key in `ovrley-flatpak.gpg`:

```
B427 292B 9F13 708C 4CE1  4EBE DD3B B8CE 23CD B95C
```

Its private half is the `FLATPAK_GPG_PRIVATE_KEY` secret, shared with the OVRLEY repository, which signs the bundles.

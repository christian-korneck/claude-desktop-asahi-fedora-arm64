# Claude Desktop for Asahi Fedora Linux (arm64)

An RPM spec file that downloads and repackages the Claude Desktop Windows Electron app to run natively on Fedora Linux.

Status: Works on Fedora Asahi 42 arm64 (as of 1.1.2321 / 08-Feb-2026). Claude Code and MCPs are working. Other Fedora versions and x86_64 might be working, too but are untested.

I aim to update this repo at least once per month for new Claude Desktop versions.

## Build requirements

prereqs for building:

```
sudo dnf install rpmdevtools p7zip-plugins icoutils nodejs npm desktop-file-utils
```

build the RPM:
```
spectool -g -R claude-desktop.spec
rpmbuild -bb claude-desktop.spec
```
The resulting RPM will be in `~/rpmbuild/RPMS/aarch64/` and can get installed with:

```
sudo dnf install ~/rpmbuild/RPMS/aarch64/claude-desktop-*.rpm
```

## Alternative: Use `mock`

The `mock` tool provides a sandbox that allows building rpms in a clean chroot without polluting the host. It also allows to target different Fedora versions.

prereqs for building:

```
sudo dnf install mock rpmdevtools
```
build the RPM:

```
spectool -g -R claude-desktop.spec

mock -r fedora-42-aarch64 --enable-network --spec claude-desktop.spec --sources ~/rpmbuild/SOURCES/
```

The `--enable-network` flag is required because `%prep` runs `npm install` to fetch electron and asar.

The resulting RPM will be in `/var/lib/mock/fedora-42-aarch64/result/` and can get installed with:

```
sudo dnf install /var/lib/mock/fedora-42-aarch64/result/claude-desktop-*.rpm
```

## Disclaimer

This is an educational project. Use at your own risk. The closed-source Claude Desktop binaries are not part of this repo and if you want to use them be aware of the terms and licenses that apply.

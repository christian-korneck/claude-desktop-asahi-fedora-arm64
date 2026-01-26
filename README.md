# Claude Desktop for Asahi Fedora Linux (arm64)

A shell script that downloads and repackages the Claude Desktop for Windows arm64 Electron app and installs it on Asahi Linux Fedora 42 arm64.

Status: works on Fedora Asahi 42 arm64 (as of 1.1.886 / 26-Jan-2026). Claude Code and MCPs are working.

I aim to update this repo at least once per month for new Claude Desktop versions.

## Usage:

```
sudo ./build-fedora.sh
sudo dnf install ./claude-desktop-1.1.886-1.fc42.aarch64.rpm

```

Note: To install, you currently always need to run the build script *and* install the rpm. It is not sufficient to only install the rpm as it depends on node packages that get installed on the system by the build script. (Needs improvement, contributions welcome).

## Disclaimer

This is an educational project. Use at your own risk. The closed-source Claude Desktop binaries are not part of this repo and if you want to use them be aware of the terms and licenses that apply.

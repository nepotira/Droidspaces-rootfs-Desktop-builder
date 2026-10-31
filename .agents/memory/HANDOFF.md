# Handoff: Droidspaces RootFS for Poco F7 (onyx)

## Release Download & Installation
- Release Tag: `v20261031-230106`
- Download URL: https://github.com/nepotira/Droidspaces-rootfs-Desktop-builder/releases/tag/v20261031-230106
- File: `Ubuntu-26-gnome-Wayland-Droidspaces-rootfs-aarch64-v20261031-230106.tar.xz` (607.56 MiB)

## Instructions on Device (Poco F7 / onyx)
1. Import the rootfs archive into Droidspaces.
2. In Droidspaces advanced settings, verify the bind mount:
   `/data/local/tmp/display_daemon.sock -> /run/display.sock`
3. Launch container and connect via Anland.
4. Default user: `nepo` (initial password `1234`).
   - Run `passwd nepo` to update to `pedroca`.
   - Hostname is pre-configured to `onyx`.
5. Testing Checklist:
   - Check GPU: `eglinfo | grep -i -E "renderer|driver"` and `vulkaninfo --summary`
   - Test GNOME desktop stability.
   - Test Google Chrome (and Google Chrome Safe Mode if needed).

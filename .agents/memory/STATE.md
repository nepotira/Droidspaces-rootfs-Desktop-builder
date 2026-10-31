# Project State: GooglebookOS / Droidspaces RootFS for Poco F7 (onyx)

## Status: Completed & Published

- Release: [v20261031-230106](https://github.com/nepotira/Droidspaces-rootfs-Desktop-builder/releases/tag/v20261031-230106)
- Artifact: `Ubuntu-26-gnome-Wayland-Droidspaces-rootfs-aarch64-v20261031-230106.tar.xz` (607.56 MiB)
- Target: Ubuntu 26.04 / GNOME / Anland Wayland
- User: `nepo` (in `sudo`, `shadow`, `droidspaces-gpu`, etc.)
- Hostname: `onyx` (injected in `/etc/hostname` and `/etc/hosts`)

### Applied Mitigations
1. **Qualcomm Adreno Turnip UBWC Workaround**:
   - `enable_8gen2_wayland=true`, `FD_DEV_FEATURES=enable_tp_ubwc_flag_hint=1`, `TU_DEBUG=noconform`.
2. **Wayland Anland Synchronization**:
   - `ANLAND_SKIP_IMPLICIT_SYNC_WAIT=1`, `XWAYLAND_GBM_DEVICE=/dev/dri/renderD128`, `MESA_VK_DEVICE_SELECT_FORCE_DEFAULT_DEVICE=1`.
3. **GNOME Session Stability**:
   - GSettings overrides disabled `idle-delay`, screen lock, and power inactivity suspend.
   - `desktop-session.service` updated to `Restart=always` with 10s socket wait loop.
4. **Chrome Wayland & Fallback**:
   - Wrapper reads `~/.config/chrome-flags.conf` and handles `--disable-gpu`.
   - "Google Chrome (Safe Mode)" desktop shortcut available.
5. **Diagnostics Pre-installed**:
   - `mesa-utils-bin` provides `eglinfo`.

# Project State: GooglebookOS / Droidspaces RootFS for Poco F7 (onyx)

## Status: Ready for RootFS Build

### Configured Device & Credentials
- Target Distribution: Ubuntu 26.04 (Ubuntu-26)
- Desktop Environment: GNOME on Anland Wayland
- User: `nepo` (UID 1000, added to `sudo`, `shadow`, `droidspaces-gpu`, `input`, `video`, etc.)
- Hostname: `onyx` (configured in `/etc/hostname` and `/etc/hosts`)
- Sudo Password: Set via GitHub Actions secret `ROOTFS_PASSWORD` (never stored in repository files, commits, or logs).

### Implemented Fixes for Turnip, Anland, and Desktop
1. **Snapdragon UBWC Display Corruption Workaround**:
   - `enable_8gen2_wayland` enabled by default (`true`).
   - Injects `FD_DEV_FEATURES=enable_tp_ubwc_flag_hint=1` and `TU_DEBUG=noconform` into `/etc/environment`.
2. **GNOME Anland Wayland Tuning**:
   - Added `ANLAND_SKIP_IMPLICIT_SYNC_WAIT=1`, `XWAYLAND_GBM_DEVICE=/dev/dri/renderD128`, and `MESA_VK_DEVICE_SELECT_FORCE_DEFAULT_DEVICE=1` to `/etc/environment`.
   - Added `mesa-utils-bin` to default apt packages for out-of-the-box `eglinfo` diagnostics.
3. **GNOME Session Exit / Timeout Prevention**:
   - Fixed the issue where GNOME session exited after ~1m36s by adding GSettings overrides disabling `idle-delay` (0), power daemon sleep, screensaver lock, and lockdown lock-screen.
   - Updated `desktop-session.service` to `Restart=always` (3s delay) and made `start-desktop-session` probe for `/run/display.sock`.
4. **Google Chrome Wayland & Safe Fallback**:
   - Chrome wrapper now supports flags from `~/.config/chrome-flags.conf` and `/etc/chrome-flags.conf`.
   - Dedicated "Google Chrome (Safe Mode)" `.desktop` launcher created with `--disable-gpu`.

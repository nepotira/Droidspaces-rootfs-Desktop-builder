# Project State: GooglebookOS / Droidspaces RootFS for Poco F7 (onyx)

## Status: Build in progress on GitHub Actions

- Workflow Run: [41250153215](https://github.com/nepotira/Droidspaces-rootfs-Desktop-builder/actions/runs/41250153215)
- Branch: `main` (commit `4647f8d`)
- Target: Ubuntu-26 / GNOME (Anland Wayland)
- Device Hostname: `onyx`
- Default User: `nepo`
- Turnip & Adreno UBWC Workarounds: Enabled (`enable_8gen2_wayland=true`, `FD_DEV_FEATURES=enable_tp_ubwc_flag_hint=1`, `TU_DEBUG=noconform`)
- Desktop Stability Fixes: Applied (90s GNOME idle/power sleep disabled, `Restart=always` in service, socket wait loop, Chrome Wayland wrapper & safe mode shortcut)

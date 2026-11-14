# Unreleased

## API Changes

- **Breaking**: Remove the `CFG_TUSB_RHPORT0_MODE`/`CFG_TUSB_RHPORT1_MODE` fallback (superseded in 0.14.0). Defining either is now a compile error. Migrate:
  - `CFG_TUSB_RHPORTx_MODE (OPT_MODE_DEVICE | speed)` -> `CFG_TUD_ENABLED 1` and `CFG_TUD_MAX_SPEED speed`
  - `CFG_TUSB_RHPORTx_MODE (OPT_MODE_HOST | speed)` -> `CFG_TUH_ENABLED 1` and `CFG_TUH_MAX_SPEED speed`
- **Breaking**: Remove `tusb_init(void)` (deprecated in 0.18.0); calling it is a compile error. Use `tusb_init(rhport, &rh_init)` with a `tusb_rhport_init_t` giving role and speed.
- **Breaking**: Rename port option `TUP_RHPORT_HIGHSPEED` to `CFG_TUSB_HIGH_SPEED_DEFAULT`. It resolves to `CFG_TUSB_HIGH_SPEED`, which `tusb_config.h` may override, and sets `TUD_OPT_HIGH_SPEED`/`TUH_OPT_HIGH_SPEED` while `CFG_TUD_MAX_SPEED`/`CFG_TUH_MAX_SPEED` is left at default.

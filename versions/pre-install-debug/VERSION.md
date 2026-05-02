# pre-install-debug

Version: `2026.05.02-pre-install-debug`

This is the installer and first-boot debug EFI. Use it before macOS is installed, when booting Recovery/Installer, or when you still need verbose logs to diagnose APFS, graphics, or OpenCore issues.

## Status

- Target machine: Huawei MateBook X Pro 2019
- Target macOS: Sonoma 14.x
- OpenCore: 1.0.7 core files
- SMBIOS: public placeholders only, generate your own values before use
- MX250: disabled with `-wegnoegpu`
- APFS compatibility: `MinDate = -1`, `MinVersion = -1`

## Debug profile

```text
boot-args = -igfxblt -igfxonln=1 -igfxmlr -igfxblr -no_compat_check ipc_control_port_options=0 -amfipassbeta revpatch=sbvmm -wegnoegpu debug=0x100 keepsyms=1 -v
AppleDebug = true
Target = 67
DisplayLevel = 2147483650
LogModules = *
```

## Use

Copy this directory's `EFI` folder to the EFI partition of the installer USB or recovery disk.

After macOS is installed and the machine can boot reliably, switch to `versions/post-install-nvme-stable/EFI` to reduce verbose output and OpenCore file logging.

# post-install-nvme-stable

Version: `2026.05.02-post-install-nvme-stable`

This is the post-install EFI captured from a successful internal NVMe boot after migrating macOS from an external USB disk to the internal 128 GB NVMe. Public SMBIOS identifiers have been removed.

## Verified boot state

- macOS: Sonoma 14.8.5 (`23J423`)
- Boot disk: internal PCIe NVMe, `disk0`
- EFI boot path: internal `disk0s1` -> `\EFI\BOOT\BOOTx64.efi`
- APFS physical store: internal `disk0s2`
- Root volume: sealed APFS system snapshot
- Volume group: System/Data with Preboot, Recovery, and VM present
- Disk health: SMART Verified
- TRIM: supported

## Debug profile

```text
boot-args = -igfxblt -igfxonln=1 -igfxmlr -igfxblr -no_compat_check ipc_control_port_options=0 -amfipassbeta revpatch=sbvmm -wegnoegpu
AppleDebug = false
Target = 0
DisplayLevel = 0
LogModules =
```

## Use

Copy this directory's `EFI` folder to the internal NVMe EFI partition after installation is complete and the machine can already boot through OpenCore.

Before use, generate your own SMBIOS values and replace the public placeholders in `EFI/OC/config.plist`.

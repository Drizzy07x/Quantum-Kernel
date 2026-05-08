# Quantum-Kernel

Quantum-Kernel is a Pixel Tensor kernel project based on Sultan’s Pixel kernel work, focused on clean daily-use builds for Google Pixel Tensor devices.

The goal is not to turn the kernel into a random tweak collection. Quantum-Kernel prioritizes stability, reliable boot behavior, efficiency, smoothness, battery life, and thermal consistency.

## Focus

Quantum-Kernel is designed around a simple priority order:

1. Stability
2. Efficiency
3. Smoothness
4. Battery behavior
5. Thermal consistency
6. Optional root-related features when they do not compromise the base kernel

This project follows the philosophy of keeping the base kernel clean and practical. Risky performance hacks, unsafe voltage changes, thermal bypasses, and benchmark-only changes are not part of the goal.

## Primary Target

Current development focus:

- Google Pixel 9 Pro XL
- Codename: `komodo`
- Platform: `zumapro`
- Android 16 stock firmware
- Sultan-based Tensor kernel source

Other Pixel Tensor devices may build or boot depending on source compatibility, but they should not be considered fully supported unless tested.

## Variants

Quantum-Kernel is intended to support clean build variants.

### Stock

The stock variant is based on Sultan’s kernel source without KernelSU, Wild KSU, or SUSFS integration.

Recommended for users who want the cleanest and most stable Quantum-Kernel build.

## Repository Structure

This repository mainly contains:

- GitHub Actions workflows
- Kernel build automation
- Patch integration logic
- Sultan compatibility patches
- Optional feature variant support
- Release and artifact handling

The upstream kernel source is not stored directly in this repository.

Quantum-Kernel currently uses Sultan’s Pixel Tensor kernel source as the main upstream base.

## Source Base

Main upstream kernel source:

- Sultan / kerneltoast Pixel Tensor kernel:
  - https://github.com/kerneltoast/android_kernel_google_tensynos

Quantum-Kernel is based on this work and keeps Sultan’s stability-first approach as the foundation.

## Optional Root Feature Sources

Optional root-related variant work may reference or integrate resources from:

- WildKernels / Wild KSU:
  - https://github.com/WildKernels/Sultan_KernelSU_SUSFS

- KernelSU:
  - https://github.com/tiann/KernelSU

- SUSFS for KernelSU:
  - https://github.com/sidex15/susfs4ksu
  - https://github.com/simonpunk/susfs4ksu

- SUSFS KernelSU module:
  - https://github.com/sidex15/ksu_module_susfs

Additional community resources may be used when clearly credited in commits, patches, or release notes.

## Build Philosophy

Quantum-Kernel should remain small, reviewable, and maintainable.

Changes should be:

- Easy to audit
- Easy to revert
- Clearly scoped
- Tested before release
- Compatible with the selected Sultan base
- Safe for daily use whenever possible

Changes should not be added only because they sound faster.

## What This Kernel Is Not

Quantum-Kernel is not intended to be:

- A benchmark-only kernel
- A thermal bypass kernel
- An overclocking project
- A random tweak collection
- A replacement for proper testing

## Credits

Quantum-Kernel exists because of the work of the Android kernel community.

Special credit to:

- Sultan / kerneltoast for the Pixel Tensor kernel base
- WildKernels for Wild KSU and Sultan KernelSU/SUSFS-related work
- tiann and KernelSU contributors for KernelSU
- simonpunk for SUSFS work
- sidex15 for SUSFS for KernelSU and related module work
- TheWildJames and related community resources where applicable
- Google and the Android kernel community

Testing credit:

- Ne0ns4l4m4nder for testing Quantum-Kernel builds and helping validate real-device behavior

This project is maintained by Drizzy_07.

## Flashing Warning

Flash at your own risk.

A custom kernel can cause:

- Bootloops
- Failed boot
- Broken root
- Broken Wi-Fi or mobile data
- Broken camera or audio
- SELinux issues
- Battery drain
- Thermal problems
- Failed OTA updates
- Data loss if recovery steps are handled incorrectly

Always keep a known-good boot or recovery path before flashing.

## Recommended Testing Checklist

After flashing, verify:

```sh
adb shell getprop ro.product.device
adb shell getprop ro.build.version.release
adb shell getprop ro.build.version.sdk
adb shell uname -a
adb shell getenforce

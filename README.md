<div align="center">

<img src="bakasu-edition-banner.webp" alt="Equinox Infinity X BakaSU Edition by Nanairo8890" width="100%">

# Equinox Infinity X BakaSU Edition by Nanairo8890

**POCO F5 Pro / Redmi K60** · `mondrian` · Snapdragon 8+ Gen 1 · **Project Infinity-X 4.1**

**Developer:** [LF52406](https://github.com/LF52406) · **[Download builds](../../releases)**

</div>

---

> [!NOTE]
> **This fork is the Project Infinity-X build of the BakaSU edition of Equinox**, made by **Nanairo** with
> LF52406's permission. It is Equinox 5.10.269 as released, with these changes:
>
> - **[BakaSU](https://github.com/Baka-SU/BakaSU)** (formerly ReSukiSU) instead of KernelSU-Next, as the `KernelSU/` submodule at `f308ed09` (35233), the latest version of BakaSU's [PR #624](https://github.com/Baka-SU/BakaSU/pull/624), which brings SUSFS builds back. Use the BakaSU manager 35217 or newer (35231 recommended): this kernel uses UAPI 5, and older ReSukiSU managers (UAPI 4) ask to be updated before modules and `su` start.
> - **SUSFS v2.3.0** from [simonpunk's](https://gitlab.com/simonpunk/susfs4ksu) `gki-android12-5.10` branch at `ca7093a1`, through BakaSU's built-in SUSFS support.
> - **BBR** as the default TCP congestion control.
> - **[NoMount](https://github.com/maxsteeel/nomount) v2.1.1** by maxsteeel built in (`fs/nomount`), which
>   includes deref3046's fix `7e7342c`. Use it with the official NoMount metamodule. Processes that BakaSU/SUSFS
>   umount modules for see the stock filesystem, and NoMount is hidden from `/sys/module` and `/proc/kallsyms`.
>
> Everything else, DroidSpaces included, is LF52406's work, described below. The official Equinox
> builds are at [LF52406/Equinox-Kernel-sm8450](https://github.com/LF52406/Equinox-Kernel-sm8450), and the
> BakaSU edition for MistOS is at [nanairo8890/Equinox-Kernel-sm8450](https://github.com/nanairo8890/Equinox-Kernel-sm8450).
> Report problems with this edition to Nanairo8890, not to LF52406.
>
> Build: `CLANG_DIR=/path/to/clang/bin scripts/equinox/build-bakasu.sh` · Changes: [release notes](scripts/equinox/release-notes/5.10.269-bakasu-r4-infinityx.md) · Changelog: [English](CHANGELOG.en.txt) · [Español](CHANGELOG.es.txt) · [Português (Brasil)](CHANGELOG.pt-BR.txt) · [Русский](CHANGELOG.ru.txt)

---

## Current Build

| Component | Current |
|:--|:--|
| **Linux** | `5.10.269-Equinox` |
| **Compatibility** | Project Infinity-X 4.1 (Android 17, build of 17 October 2026) |
| **BakaSU** | `v4.2.0-rc3-62-gf308ed09` (35233) |
| **SUSFS** | `2.3.0` (`ca7093a1`) |
| **NoMount** | `v2.1.1` built in |
| **DroidSpaces** | Supported |
| **TCP** | BBR default · CUBIC available |
| **Toolchain** | AOSP Clang `22.0.0` (r584948) |
| **Build** | ThinLTO · Clang CFI · MODVERSIONS |
| **KMI** | Verified against clean Equinox 5.10.269 |

---

## Features

| Group | Included |
|:--|:--|
| **Root & hiding** | BakaSU integration · SUSFS |
| **Containers** | DroidSpaces · PID namespaces · IPC / SYSVIPC |
| **Networking** | TCP BBR · runtime congestion-control switching |
| **Device** | mondrian production config · Goodix touch stability fixes |
| **Packaging** | Verified AnyKernel3 release package |

---

## Latest Changes

### 5.10.269 r4 for Project Infinity-X 4.1

- Separate package for Project Infinity-X 4.1: vendor module CRCs checked against its 337 `vendor_boot` and 390 `vendor_dlkm` modules
- SUSFS updated to `ca7093a1`, with a fix for a SELinux status leak in `sel_open_handle_status()`
- BakaSU updated to 35233 (latest PR #624); on this 5.10 kernel its code is the same as in r3
- BakaSU manager 35231, signed with the same key as 35217 and 35229
- KMI verified against clean Equinox 5.10.269

[View full release notes](../../releases)

---

## Downloads & Flashing

Builds are published through **GitHub Releases**, with the SHA256 of each file on the release page.

**Current package:** `Equinox-5.10.269-BakaSU-mondrian-InfinityX-20261017.zip`

Download the release asset and flash the AnyKernel3 ZIP using a compatible recovery or kernel flasher. The ZIP only replaces the kernel `Image`; if you update Infinity-X, flash it again afterwards.

> GitHub-generated `Source code` archives are not flashable kernel packages.

---

## Reporting Issues

When reporting a problem to Nanairo8890, include the kernel version, a short reproduction description and relevant logs such as `dmesg`, `logcat`, `pstore / ramoops`, or watchdog / panic logs when available.

---

## Support Development

If you find **Equinox Kernel** useful and would like to support its continued development, donations are always appreciated but entirely optional.

<div align="center">

[![PayPal](https://img.shields.io/badge/PayPal-Support-003087?style=for-the-badge&logo=paypal&logoColor=white)](https://www.paypal.me/LF52406)
[![Patreon](https://img.shields.io/badge/Patreon-Support-FF424D?style=for-the-badge&logo=patreon&logoColor=white)](https://patreon.com/InfernalGT)
[![Boosty](https://img.shields.io/badge/Boosty-Support-F15F2C?style=for-the-badge&logo=boosty&logoColor=white)](https://boosty.to/infernalgt/donate)

</div>

---

## Credits & Upstreams

- [**LineageOS/android_kernel_xiaomi_sm8450**](https://github.com/LineageOS/android_kernel_xiaomi_sm8450) — primary kernel base used by Equinox
- [**LineageOS/android_kernel_qcom_sm8450**](https://github.com/LineageOS/android_kernel_qcom_sm8450) — Qualcomm common-kernel upstream used by Equinox
- [**Android Common Kernel**](https://android.googlesource.com/kernel/common) / [**Linux Kernel**](https://www.kernel.org/) — Android kernel infrastructure and upstream Linux
- [**KernelSU-Next**](https://github.com/KernelSU-Next/KernelSU-Next) — kernel root implementation
- [**SUSFS**](https://gitlab.com/simonpunk/susfs4ksu) by **simonpunk** / [**Zhanfg/susfs4ksu**](https://github.com/Zhanfg/susfs4ksu) — SUSFS integration for Linux 5.10
- [**DroidSpaces**](https://github.com/ravindu644/Droidspaces-OSS) by **ravindu644** — container runtime and kernel requirements
- [**Neutron Toolchains**](https://github.com/Neutron-Toolchains/clang-build-catalogue) — LLVM/Clang toolchain
- [**AnyKernel3**](https://github.com/osm0sis/AnyKernel3) by **osm0sis** — flashable kernel packaging
- [**BakaSU**](https://github.com/Baka-SU/BakaSU) (formerly ReSukiSU) — kernel root implementation of the BakaSU edition
- [**NoMount**](https://github.com/maxsteeel/nomount) by **maxsteeel**, with a fix by **deref3046** — VFS path redirection for the NoMount metamodule in the BakaSU edition
- [**Nanairo8890**](https://github.com/nanairo8890) — BakaSU, SUSFS, BBR and NoMount integration of the BakaSU edition, and this Project Infinity-X build

Thanks to Qualcomm, LineageOS contributors, Android Common Kernel contributors, and the broader Linux kernel community for the upstream kernel, platform, and driver work that Equinox builds upon.

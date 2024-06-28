# Stratosphere (xanmod-kernel) for Windows Subsystem for Linux (WSL2)
![Kernel CI](https://github.com/taalojarvi/xanmod-kernel-WSL2/actions/workflows/build.yml/badge.svg?branch=main)
![Kernel LTS CI](https://github.com/taalojarvi/xanmod-kernel-WSL2/actions/workflows/build-lts.yml/badge.svg?branch=main)
![](https://img.shields.io/github/license/taalojarvi/xanmod-kernel-WSL2)
![version](https://badgen.net/github/release/taalojarvi/xanmod-kernel-WSL2)

This project provides an unofficial [XanMod](https://github.com/xanmod/linux) kernel for the Windows Subsystem for Linux 2 (WSL2).

It uses **GitHub Actions** to automatically build and release XanMod kernel images for WSL2. It checks for updates twice a month and builds new versions if available.

We are currently releasing both latest stable (mainline) and LTS Xanmod kernels, LTS kernel builds are released with extra `-lts` suffix.

## Features
- Support for [dxgkrnl](https://github.com/microsoft/WSL2-Linux-Kernel/tree/linux-msft-wsl-5.15.62.1/drivers/hv/dxgkrnl) patched for **WSL2**
- Compiled with [clang](https://clang.llvm.org/) with full Clang Link Time Optimization (LTO).
- Compile-time optimized for AMD Ryzen Processors


## Usage

### Manual Installation

* Visit the [releases](https://github.com/taalojarvi/xanmod-kernel-WSL2/releases) page and download the desired kernel image.
* Put the downloaded file in a convenient location, for example, C:\WSL\bzImage
* Create a file named .wslconfig in your home directory with the following content, replacing the path with the actual location of your kernel file:
```ini
[wsl2]
kernel = the\\path\\to\\bzImage
; e.g.
; kernel = C:\\WSL\\bzImage
;
; Note that all `\` should be escaped with `\\`.
```
* Restart your WSL2 instance to use the new kernel.

> For more information about `.wslconfig`, see microsoft's official [documentation](https://docs.microsoft.com/en-us/windows/wsl/wsl-config#configure-global-options-with-wslconfig).

### Update kernel

TBD

## Miscs

### Systemd
This kernel works with the [built-in systemd support](https://devblogs.microsoft.com/commandline/systemd-support-is-now-available-in-wsl/) available since WSL 0.67.6. For older WSL versions, you can use [wsl-distrod](https://github.com/nullpo-head/wsl-distrod).

However, some tools like [sorah/subsystemctl]((https://github.com/sorah/subsystemctl)) and [arkane-systems/genie]((https://github.com/arkane-systems/genie)) might not work due to a modified kernel version string. These tools require "microsoft" in the string, which is not included here. However, WSL2 is sufficient identification, and you can verify this using systemd-detect-virt (should return wsl).

## Credits

* The Linux community
* Microsoft (WSL2 and dxgkrnl patches)
* XanMod project
* Locietta for maintaining the parent source tree

## Contributing

Let us know about any bugs, missing features, or suggestions by opening an issue. You can also contribute code improvements by creating a pull request.

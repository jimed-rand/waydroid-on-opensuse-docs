---
description: >-
  Welcome to my GitBook pages. These pages are a handy guide to help you install
  Waydroid on openSUSE.
icon: android
---

# Waydroid on openSUSE

Before reading this guide, make sure you have fulfilled the requirements below on your hardware.

* All types of CPUs with x86\_64 and aarch64 architectures (ARM is reserved for Tumbleweed users)
* Intel Integrated GPU, Intel Arc GPU series, AMD GPU (for some Radeon models, software rendering must be enabled), and NVIDIA GPU (software rendering must be enabled for NVIDIA GPU).
* For ARM (aarch64) users, the GPU options can be adjusted according to the type of GPU used.
* The minimum RAM requirement is 2 GB (4 GB or more is recommended for better performance).
* Have disabled Secure Boot to face the issues with `binder` modules in the kernel (Especially for NVIDIA GPU users who have issues communicating with the `binder` modules due to encryption on enabled Secure Boot hardware).
* openSUSE Tumbleweed or openSUSE Slowroll are installed on your hardware.
* For openSUSE Leap users, you can follow the guide pages right after the Slowroll pages.
* Have a Wayland session on your preferred desktop environment or Wayland compositor on your X11 desktop sessions.
* Have AppArmor and SELinux installed on your openSUSE systems.
* For stability, I recommend that you install the `kernel-longterm` or LTS kernel for long-term use (But if you want to use `kernel-default` or Default SUSE kernel, it's your choice).

After making sure you're following the requirements above, you can proceed it for installation. These pages have severe sub-pages for installation and troubleshooting while running Waydroid on your openSUSE systems.

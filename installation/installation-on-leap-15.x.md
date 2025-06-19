---
description: >-
  These sub-pages on the installation pages are the installation guide for Leap
  15.x users. Be careful following this guide, and make sure to follow the guide
  carefully.
icon: sign-posts-wrench
---

# Installation on Leap 15.x

## Add the PSI argument to the GRUB configuration

First, you need to add a PSI (Pressure Stall Information) argument to your GRUB configuration. These steps are required as Waydroid needs them for communicating `binder` with the kernel you are using on your systems. To add it, you need to open your preferred terminal emulator and type the command below.

```sh
sudo nano /etc/default/grub
```

After typing it, it will look like in the image below.

<figure><img src="../.gitbook/assets/Jepretan layar_20250618_103307.png" alt="Nano accessing GRUB configuration file (sudo nano /etc/default/grub)"><figcaption><p>GRUB configuration file</p></figcaption></figure>

While you're accessing the GRUB configuration file, you need to find those arguments like this.

```
GRUB_DISTRIBUTOR=
GRUB_DEFAULT=saved
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=8
GRUB_CMDLINE_LINUX_DEFAULT="mitigations=auto quiet security=apparmor"
GRUB_CMDLINE_LINUX=""
```

After you've found `GRUB_CMDLINE_LINUX_DEFAULT` arguments, make changes with an added argument `psi=1` into `GRUB_CMDLINE_LINUX_DEFAULT` arguments. It looks like this when you have added the argument `psi=1` .

```
GRUB_CMDLINE_LINUX_DEFAULT="mitigations=auto quiet security=apparmor psi=1"
```

After that, you need to apply the changes by refreshing the GRUB configuration file (use this command `sudo grub2-mkconfig -o /boot/grub2/grub.cfg` to refresh the GRUB configuration) and reboot your systems after making these changes.

## Installing AppArmor

_If you have already installed AppArmor, you can skip this step._

The next steps are installing AppArmor. For these steps, you can use YaST Software or `zypper`. For these sections, I'll show you how to install it via `zypper`. Open your terminal emulator again and type the command below.

```sh
sudo zypper in -y patterns-base-apparmor
```

After that, it will automatically install AppArmor. You can reboot your system after installation is complete.

## Adding JWR repositories to your systems

These steps involve adding my own maintained Waydroid repository, called Jim Waydroid Repository (JWR), which is required for installing Waydroid on your system. Follow these steps below to add repositories.

<pre class="language-sh"><code class="lang-sh"># Add the repositories for Leap 15.6 and refresh the repositories lists
<strong>sudo zypper ar -f https://raw.githubusercontent.com/jimed-rand/waydroid-obs-repo/refs/heads/main/repo/tumbleweed/jim-waydroid.repo
</strong><strong>sudo zypper refresh --gpg-auto-import-keys
</strong><strong>
</strong><strong># Add the repositories for Leap 15.5 and refresh the repositories lists
</strong><strong>sudo zypper ar -f  https://raw.githubusercontent.com/jimed-rand/waydroid-obs-repo/refs/heads/main/repo/slowroll/jim-waydroid.repo
</strong><strong>sudo zypper refresh --gpg-auto-import-keys
</strong></code></pre>

## Installing Waydroid

After adding JWR repositories, you can install it. Before installing Waydroid, make sure you're in a Wayland session on your desktop environment. If you're on X11, you need a Wayland compositor such as `weston` or `cage`. Follow these steps below to install it.

```sh
# Install it directly if you're on Wayland session
sudo zypper in waydroid

# Install it with Wayland compositor if you're on X11 session
sudo zypper in waydroid cage # If you want to use Cage
sudo zypper in waydroid weston # If you want to use Weston
```

After installation is completed, you need to enable the Waydroid container service.

```sh
sudo systemctl enable --now waydroid-container
```

The last step for installing Waydroid is adding WayDroid permission config on AppArmor. Follow these steps below to add it.

```sh
# Open configuration file from /etc/apparmor.d/usr.sbin.dnsmasq
sudo nano /etc/apparmor.d/usr.sbin.dnsmasq

# Then, you'll see the file like the image below
```

<figure><img src="../.gitbook/assets/Jepretan layar_20250619_070046.png" alt=""><figcaption><p>AppArmor permission config file</p></figcaption></figure>

<pre class="language-sh"><code class="lang-sh"># You need to find a permission config section like below
  # waydroid lxc-net pid file
  @{run}/waydroid-lxc/dnsmasq.pid rw,

# After finding it, add the permission config into the section like this
  # waydroid lxc-net pid file
  @{run}/waydroid-lxc/dnsmasq.pid rw,
  @{run}/waydroid-lxc/ r,
<strong>  @{run}/waydroid-lxc/* rw,
</strong></code></pre>

After that, save it. Also, make sure you have followed the installation entirely, and Waydroid has been installed with the check app menu. After checking and it's installed correctly, congrats! You should restart your PC/laptop after following this installation step to make Waydroid work on your system.

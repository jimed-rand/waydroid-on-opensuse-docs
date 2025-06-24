---
description: >-
  This sub-pages are the same as Installation pages, but it's uninstallation
  steps if you don't want to use Waydroid anymore on your openSUSE systems or
  you want to reinstall it.
icon: bin-recycle
---

# Uninstallation

These steps are useful if you want to remove a Waydroid from your systems because you don't want to use it anymore, or you want to reinstall it for some reason. Follow these steps below.

## Remove Waydroid's data

First, you need to remove all your Waydroid data from your systems before you remove the packages. Use the command below to use it.

```sh
sudo rm -rf /var/lib/waydroid /home/.waydroid ~/waydroid ~/.share/waydroid ~/.local/share/applications/*aydroid* ~/.local/share/waydroid 
```

## Remove the installed packages

After that, you can remove the packages you've already installed. Use the command below to do it. After the process is done, these packages are not installed anymore on your systems.

```sh
sudo zypper rm -y --clean-deps waydroid*
```


---
description: >-
  These sub-pages are additional options for enabling ARM translation layer for
  Waydroid.
icon: brain-circuit
---

# Add the ARM translation layer for Waydroid

By default, Waydroid only recognises apps that support the CPU architecture you've used. For example, if you only have Waydroid running on x86\_64, it will only support Android apps that are also x86\_64. Sometimes, it stops users from installing some popular Android apps on Google Play (for GAPPS users). To extend the limit, you need to add the ARM translation layer. This is the layer that provides the translation layer for running some Android apps with extended Application Binary Interfaces (ABIs). It lets you use it just like your tablet or smartphone. Follow the steps below to add it.

## Prepare the Waydroid Script

You'll need to use Waydroid Script for these steps. It's a tool that lets you add an add-on to enhance your Waydroid experience. Casualsnek and all you other folks who worked on this project have helped to improve the experience of using Waydroid, so thanks! <a href="https://github.com/casualsnek/waydroid_script" class="button secondary" data-icon="github">Click this button to access Waydroid Script</a>

Follow these steps below to prepare the Waydroid Script.

```sh
# Make a directory "Git" and change it to "Git" path
mkdir Git && cd Git

# Clone the Git into "waydroid_script" folder and change the path
git clone https://github.com/casualsnek/waydroid_script && cd waydroid_script

# After entering the path "waydroid_script", prepare the Python virtual environment on this path to make the script work
python3 -m venv venv && venv/bin/pip install -r requirements.txt
```

After preparing these, you can run the scripts.

## Run the Waydroid Script and enable the ARM translation layer

Before running this script, ensure that a Waydroid session is active. After turning on Waydroid, you can run this script with the command below.

```sh
sudo venv/bin/python3 main.py
```

It will show like this when the script is running.

<figure><img src=".gitbook/assets/Jepretan layar_20250624_150105.png" alt=""><figcaption><p>Android version options (Lineage 20 for Android 13 while Lineage 18.1 for Android 11)</p></figcaption></figure>

Depending on the Lineage version you deployed before, you choose the Android version you've used. Then, choose "Install" and you have a choice depending on the CPU you have. Here are the options you have to choose it below.

* If you're using AMD CPUs, you should choose `libndk`.
* If you're using Intel CPUs, you should choose `libhoudini`.

After you have made your choices, install it and wait for the installation process, then if completed, you may see Waydroid session restarted, but don't worry. It will bring you back to the Waydroid session with `libhoudini` or `libndk` support.

And now, you can install any Android apps you want after following these steps on this sub-page.

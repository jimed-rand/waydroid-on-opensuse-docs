---
description: >-
  These sub-pages on the initialisation for deploying Waydroid images and
  initiate user experiences before Waydroid is ready to use.
icon: compress
---

# Waydroid Initialisation

## Initialisation without OTA links

You've got Waydroid on your openSUSE systems, but you can't use it straight away because you need to set up Android images for Waydroid first. In this section, you'll get it going with our maintained packages from the JWR repo, which it updated semi-rolling, and you don't need OTA (Over-The-Air) links for these steps.

In these steps, there are many options for you to deploy which images you want. Here is the list of packages that contain Waydroid images for you to deploy.

* Lineage 20 Vanilla images for Waydroid (or the package name is `waydroid-image`), where it doesn't contain Google Play (GAPPS) services, and it's a de-googled variant of images for Waydroid. It's based on Android 13.
* Lineage 18.1 Vanilla image for Waydroid (or the package name is `waydroid-image-lineage18`), where it same as Lineage 20 Vanilla image, but it's still based on Android 11. Official OTA links are still picking these images for manual deployment with OTA links.
* Lineage 20 with Google Play (GAPPS) images for Waydroid (or the package name is `waydroid-image-gapps`), where it contains Google Play services included in images, and it's a Google-d variant of images for Waydroid. Google Play will detect Waydroid as a tablet in Device management when you have already registered the GSF (Google Services Framework) ID and logged in your account into deployed Waydroid images. It's also based on Android 13 with Google Play (GAPPS) included.
* Lineage 18.1 with Google Play (GAPPS) images for Waydroid (or the package name is `waydroid-image-gapps-lineage18`), where it same as Lineage 20 with Google Play images, but it's still based on Android 11. Also, official OTA links are still picking these images for manual deployment, with OTA links, and when you choose GAPPS on manual deployment, these images will be used for deployment into your Waydroid.

If you want to use Waydroid with De-Googled experiences, you can use Vanilla images. If you want to get the same experience as on your smartphone or tablet, you can use GAPPS images. You'll also need to submit the GSF (Google Services Framework) ID and register it for the GAPPS variant, which we'll cover later on in the next sub-pages.

Just to remind you, if you're using these steps, don't use these commands (`sudo waydroid upgrade`) when you're using these steps to deploy Waydroid images. Instead, just upgrade your systems at your usual time for doing that.

### Initiating and deploying Vanilla images

Now, if you want to deploy Lineage 20 Vanilla or Lineage 18.1 Vanilla, type the commands below to install the packages that contain images to deploy them.

```sh
sudo zypper in waydroid-image # Choose this when you want Lineage 20 Vanilla
sudo zypper in waydroid-image-lineage18 # Choose this when you want Lineage 18.1 Vanilla
```

After installation is completed, you simply type the command below, and your Waydroid has been initiated and is ready to use with De-Googled experiences.

```sh
sudo waydroid init # Init it when installation is completed
waydroid show-full-ui # Launches Waydroid in full UI
```

### Initiating and deploying GAPPS images

Well, if you want an experience as same to your tablet or your smartphone with Google Play for your daily use, you need to deploy GAPPS images. Type the command below to install the packages that contain images to deploy them.

```sh
sudo zypper in waydroid-image-gapps # Choose this when you want Lineage 20 GAPPS
sudo zypper in waydroid-image-gapps-lineage18 # Choose this when you want Lineage 18.1 GAPPS
```

After installation is complete, you simply type the command below,  and your Waydroid has been initiated, but you still need to register your GSF ID, which will be explained on the next sub-pages.

```sh
sudo waydroid init # Init it when installation is completed
waydroid show-full-ui # Launches Waydroid in full UI
```

## Initialisation manually with OTA links

These steps are different from the previous ones, which needed OTA (Over-The-Air) links. With those, you need to deploy the images by downloading the ZIP files containing them and then deploying them using Waydroid. It's also still using Lineage 18.1, with both the Vanilla and GAPPS versions. If you want to use Lineage 20 for now, just follow the previous steps. This initialisation method will give you updates every week for the images, while our packages, which we mentioned in previous steps, are semi-rolling with an update time between two weeks and monthly.

If you want to do a manual deployment, you can follow these steps and just remember to update them whenever there's a new version of the images. Just follow these steps.

```sh
# If you want to deploy Vanilla images, use these commands to deploy them
sudo waydroid init -s VANILLA -c https://ota.waydro.id/system -v https://ota.waydro.id/vendor -f 

# If you want to deploy GAPPS images, use these commands to deploy them
sudo waydroid init -s GAPPS -c https://ota.waydro.id/system -v https://ota.waydro.id/vendor -f 

# If you got an updates notification from Waydroid Updater services on your deployed images, type these commands to upgrade them
sudo waydroid upgrade # Also, do not use these commands when you're using previous steps.
```


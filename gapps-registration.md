---
description: >-
  These sub-pages are showing about how to register GSF ID into Google's server
  for making Google Play usable on Waydroid. These steps are only for users with
  GAPPS images deployed.
icon: google-play
---

# GAPPS Registration

## Boot on Waydroid and get the GSF ID

Once you've got GAPPS images up and running, you won't be able to use Google Play directly because Waydroid will be flagged as an unknown device. Then Google Play Protect will flag it as "untrusted devices", and it'll show as "This device is not certified". Also, the notification sound is really annoying in this situation. To sort it, you just need to register the GSF (Google Services Framework) ID with Google's server. To fix it, follow the steps below

```sh
# Enter the Waydroid shell
sudo waydroid shell

# Copy the command below inside the Waydroid shell
ANDROID_RUNTIME_ROOT=/apex/com.android.runtime ANDROID_DATA=/data ANDROID_TZDATA_ROOT=/apex/com.android.tzdata ANDROID_I18N_ROOT=/apex/com.android.i18n sqlite3 /data/data/com.google.android.gsf/databases/gservices.db "select * from main where name = \"android_id\";"

# And, you'll get the GSF ID, which is required to submit it
```

## Register the GSF ID on Google's server

Once you've got your GSF ID, \[click this]\([https://www.google.com/android/uncertified](https://www.google.com/android/uncertified)) to register it with Google's server. Just make sure you've logged in to your account before submitting it.




# DroidBox

Run Android apps on an iPhone or iPad. DroidBox is a fork of [UTM SE](https://github.com/utmapp/UTM) (Apache 2.0). It emulates an x86_64 PC and runs [Android-x86](https://www.android-x86.org/) inside it. It needs no JIT and no jailbreak.

> **It's slow.** iOS doesn't let sideloaded apps generate code at runtime, so QEMU runs in interpreter mode (TCI). Simple apps work. Games and anything heavy won't run well.

## Get the IPA (no Mac needed)

1. Push this repo to GitHub. The **Build DroidBox IPA** workflow runs automatically.
   - The first run compiles QEMU and its dependencies, which takes **several hours**. After that the result is cached, and builds take about 20–30 minutes.
   - You can also start it by hand under **Actions → Build DroidBox IPA → Run workflow**.
2. When the run turns green, open it and download the **DroidBox-ipa** artifact (a zip containing `DroidBox.ipa`).
3. Sign and install it with your sideloading tool (AltStore, SideStore, Sideloadly, etc.).

## Run Android

1. Download an Android-x86 ISO, for example `android-x86_64-9.0-r2.iso` from the [Android-x86 releases](https://sourceforge.net/projects/android-x86/files/Release%209.0/). The app also has a link to it.
2. Open DroidBox, tap **+**, then **Android** under *Quick Start*.
3. Pick the ISO and tap **Next** until you reach **Save**. The preset is 2 GB of RAM and an 8 GB disk.
4. Start the VM. In the boot menu, choose **Live CD** to try it, or **Installation** to install onto the 8 GB disk so your apps persist.
5. To install apps, use the browser inside Android to download APKs, or use an app store like F-Droid.

## What's changed from UTM

- `Platform/Shared/VMWizardStartViewTCI.swift`: added a *Quick Start → Android* button and an ISO download link.
- `Platform/Shared/VMWizardState.swift`: added `startAndroid()`, which presets x86_64 / 2 GB RAM / 8 GB disk / CD boot.
- `Platform/iOS/Info.plist`: the home-screen name is **DroidBox**.
- `.github/workflows/build-ipa.yml`: builds only the unsigned UTM SE IPA. The upstream workflows were removed.

The upstream README is kept as [UTM-README.md](UTM-README.md).

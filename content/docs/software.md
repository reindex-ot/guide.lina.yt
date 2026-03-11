---
weight: 300
title: Optional software
---

# Optional software

> [!NOTE]
> When installing software from Discover, you might have a choice of software source in the upper right corner. I generally recommend using **Install from Fedora Linux**   , which means you will be the RPM version of the software, instead of Flatpak.

## Steam

Since you have RPM Fusion, Steam will be available in the Discover app. Just search for it and install it! Make sure you choose **Install from Fedora Linux** in the top right corner, to avoid trouble later.

## Google Chrome

Fedora KDE comes with Firefox as the default browser, which is a great choice! You can also choose Chromium, which is the open source version of Google Chrome. You will find Chromium in the **Discover** software app.

However, if for whatever reason you really want the official version of Google Chrome, you can install it with these commands:

    sudo dnf config-manager setopt google-chrome.enabled=1

    sudo dnf install google-chrome-stable

Since this uses an RPM package repository, Google Chrome will be updated alongside the rest of your OS.

Alternatively, you can also enable Flathub as mentioned earlier, then you will find Google Chrome listed as a Flatpak app in **Discover**.


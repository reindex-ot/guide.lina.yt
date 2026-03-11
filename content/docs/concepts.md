---
weight: 300
title: Basic concepts
---

# Basic concepts

For those new to Linux and Fedora, here is a quick overview of some concepts you might not be familiar with. For more detailed information, feel free to search around, as there are many comprehensive Linux guides and tutorials around! The [Fedora Documentation](https://docs.fedoraproject.org) site is a great place to start.

## Directories and paths

The default file browser in Fedora KDE is called **Dolphin**, which you can access from your applications menu.

On Linux, paths are delimited with forward slashes, `/like/this`. The root directory, which is where your OS is installed, is just called `/` (this is like `C:\` on Windows). When you first install the system and create a user, you will have a *home directory* at `/home/username`, where **username** is your username. Your home directory is where you keep all your files, and also where the system and applications store all your personal settings. Dolphin shows your home folder in the top bar as simply **Home**, but if you click on the arrow to the left, you will be able to browse up into the rest of the filesystem. You can also click to the right of the breadcrumbs (in the empty space) to change to an editable text path, and type a path to quickly go to any folder.

As a shortcut, your home directory is also called `~` (the tilde character). For example, a file called **hello.txt** on a system where the main user is named **lina** will have the path `/home/lina/hello.txt`, and this same path can be written as `~/hello.txt` for short. This guide will use the `~` shortcut a lot, to make things shorter and also as a way of making paths and commands work regardless of what your username is. You can use this shortcut in the command line terminal, and also in most graphical applications. For example, typing a file name of `~/hello.txt` in a "save as" dialog and hitting enter will usually write that file exactly where you specified, regardless of what folder is currently selected in the dialog. This also works in Dolphin, and you can click to the right of the top bar and replace the path with `~/.config/` to go to your user's `.config` folder (where most apps store their configuration files). 

Files and folders that begin with `.` (a period) are hidden. These files are often used to store application configuration settings inside your home folder, without showing up by default. To show hidden files in Dolphin and in most KDE file open/save dialogs, press **Ctrl+H**.

> [!TIP]
> Linux allows pretty much every character to be used in file names except `/`, though using really funny stuff can cause confusion. Also, Linux doesn't have "file extensions" as a built-in concept. A file called `text.txt` is just 8 characters, the dot isn't special. Extensions are still used to make sense of the type of files, but this is mostly just as convention and apps may or may not care about the extension.

Files outside your home directory are generally system files, and your user will not have *permission* to access them. To modify system files, you will have to *act as administrator*. In Dolphin, you can do this with **Ctrl+Alt+Shift+A**. This will prompt for your password, for security. You will almost never need to do this, so be careful!

When you plug in an external drive (or if you have other system partitions), it will be *mounted* somewhere by the system, usually `/run/media/diskname` for a disk called **diskname**. This happens automatically when you open up the drive in Dolphin or from the *Disks & Devices* icon in the system tray. macOS users might know the equivalent place as `/Volumes/`. Mounted drives appear as part of your root filesystem when they are mounted but are still separate drives (instead of there being separate roots like Windows drive letters). You might have also heard of `/mnt`: This path is usually used for extra drives that you *manually* configure to mount on startup yourself, but that's outside the scope of this guide.

> [!TIP]
> Advanced users beware: Although you can technically mount anything anywhere, you will run into problems with various things like Steam and Flatpak apps if you use a completely custom path outside your home directory and `/mnt`. Try to keep any custom shenanigans to those directories (or just use the default `/run/media` setup, which is also safe).

## Command line terminal

You may have heard about using the command line (or "terminal") on Linux. Don't worry, for the most part you won't have to use it! However, a few things will require it. It's also a lot easier to describe how to do things in the command line, since you can just copy and paste commands instead of having to follow instructions on how to follow graphical prompts. This guide will generally prefer avoiding the command line where possible and show you how to set things up so you don't need to use it on a daily basis, although it will sometimes be required for certain setup tasks.

To launch a terminal in Fedora KDE, open up the **Konsole** application from your application launcher. Here are some quick tips:

* The terminal always has a "current directory" which is the folder you are currently working from. This is shown on the prompt to the left. The prompt `lina@diamond:~$` means you are running as the user `lina` on the computer named `diamond` and the current directory is `~` (which means your home directory).
* Type **Enter** after a command to execute it.
* Type **Ctrl+C** if you want to cancel what you're currently doing. This erases a half-typed command, and also stops (**C**ancels) a command that is currently running and doing something.
* To copy and paste, since **Ctrl+C** is taken, you have to use **Ctrl+Shift+C** and **Ctrl+Shift+V**.
* You can also use the mouse to copy and paste. Select text to copy, and press the middle mouse button (the scroll wheel) to paste. This also works in almost all other applications too. The clipboard used by the mouse (called the "selection") is separate from the one used by `Ctrl+C` and `Ctrl+V`, so you actually have two separate clipboards, which can be convenient (or perhaps confusing).
* To list the files in the current directory, type `ls`. Use `ls -a` to show hidden files, `ls -l` to show a detailed list with file sizes and other info, and `ls -al` for both.
* To change to a directory within the current one, type `cd dirname`. To change to the parent directory, type `cd ..`. You can also use a complete path starting with `/` to jump to a completely different directory, like `cd /home/lina/.config`, or use the `~` shortcut as above, like `cd ~/.config`. In general, any file name you use will be *relative* to the current directory if it starts with a filename or directory name, and *absolute* (ignoring the current directory) if it starts with `/` (or `~` to start at your home directory). If you just type `cd` all on its own, it'll take you to your home directory (another shortcut).
* There is autocomplete for filenames. You can press **Tab** at any point to complete the current name if it is unique, or do it twice to show a list of options.
* To type paths with spaces or weird special characters, either put a `\` (backslash) before each space, or enclose the path or part of the path in `'quotes'`. `~` won't work within quotes, but you can mix them together, like `~/'My Stuff'/file.txt` to access a file called `file.txt` inside a directory called `My Stuff` in your home directory.

## Packages and package managers

Unlike Windows and macOS, Linux distributions like Fedora are collections of software developed by *many third parties*. Instead of a single entity (like Microsoft or Apple) developing the OS and core applications and distributing them to users, what distributions like Fedora do is collect software *largely developed by others* and package it in a single place, making sure everything works together.

This means that distributions come with a *huge* variety of software available all in one place from a trusted source, so you largely don't have to worry about malware risks, software messing up your OS, or compatibility issues. Since the installed software is managed by a central package system, uninstalling is easy and you can be confident that it won't leave any leftovers behind. You also don't have to worry about third-party updaters, launchers, nag screens, or any of that, and in general also you won't find any ads or privacy-invasive features, and any telemetry options are usually opt-in (and genuinely designed to help developers, not just mindlessly collect all your data).

What this means is that, by and large, you will not be downloading software for Fedora Linux from websites. Instead, you get software via your *package manager*. On Fedora, there are two package managers you will use: [DNF](https://docs.fedoraproject.org/en-US/quick-docs/dnf/) and [Flatpak](https://docs.fedoraproject.org/en-US/flatpak/).

> [!TIP]
> If you've ever used Chocolatey on Windows or Brew on macOS, you already know what a package manager is. It works the same on Linux, but comes preinstalled with the OS, and the entire OS is itself managed the same way.

### DNF and RPM

DNF is the "native" package manager for Fedora. DNF works with a package format called RPM, and your entire Fedora system is built out of a large number of installed RPM packages. If you managed to uninstall everything, there would quite literally be no operating system left, just a blank hard disk (mostly)!

RPM packages installed via DNF work together to build up the system as a whole, and each package will have *dependencies* that are automatically installed where needed. For example, if you try to install an OBS plugin but you don't have OBS installed yet, installing the plugin will install OBS. This goes much further though, and you will find that packages depend on many libraries and other helper packages built by different people. You generally don't have to worry about that though, as it will be handled automatically for you.

### Flatpak and Flathub

Flatpak is a software packaging format that is intended to be "universal", similar to the way you download and install app bundles on macOS. Flatpak apps work on many different Linux distributions. They are also sandboxed to varying degrees, so they can be more secure than natively installed apps. However, for the same reason, they also tend to integrate less well into the rest of the system.

The main Flatpak "app store" is [Flathub](https://flathub.org/). Some application developers provide "official" Flatpaks, and these will be listed as **Verified** with a blue checkmark on Flathub.

### Flatpak or native?

As there are two package managers, you might find that lots of software is available both ways: natively via DNF, and as a Flatpak. Which should you choose?

There is no single answer. Native packages usually integrate better with the rest of the system, but can bring bugs specific to the system. Flatpaks work the same on every Linux distribution, but sometimes they don't work as well as native packages, and you can run into complications due to the sandboxing system.

When a package is only available natively or as a Flatpak, of course, that is your only option. What should you do when you have both?

* For applications that integrate with the rest of the system in complex ways or use plugins, you should prefer native packages. Flatpak apps can't "see" plugins and add-ons installed natively and don't integrate as well with the system.
* When a Flathub apps is **Unverified**, you should prefer the native version. In this case, both the Fedora package and the Flathub package are "unofficial", but at least the Fedora package will have to follow the Fedora standards, and is more likely to work better. For example, you should always prefer the native package for Steam, since the Flatpak is known to cause headaches.
* When a Flahub app is **Verified** and it is mostly a stand-alone app (that just does one thing and doesn't try to extend/integrate with other apps), then the Flathub version might have more features or fewer issues.

Which option you choose also determines how you should get help if you find a bug. If you install a package natively, you should report bugs to [Fedora](https://docs.fedoraproject.org/en-US/quick-docs/bugzilla-file-a-bug/) or [RPM Fusion](https://rpmfusion.org/ReportingBugs). If you install a Flathub app, you should report bugs at the **Report an Issue* link in the Flathub app page (which should take you to the bug reporting page for the Flatpak packager or the original app developer, if it is verified).

In general, when in doubt, prefer the Fedora native version. That way, Fedora volunteers and packagers like myself can help you more directly!

## Installing software

On Fedora KDE Plasma, you can easily install software using the **Discover** app. This works for both DNF (native Fedora) software and Flatpak software.

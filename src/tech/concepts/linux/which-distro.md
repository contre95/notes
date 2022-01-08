# A basic compilation of concepts before choosing your Linux distribution

This post is a compilation of Wikipedia, ArchWiki and Stackoverflow posts. I took a small but tasty bite of each post in order to gather a base knowledge in order to start your research for the Linux distribution that best suits you. Beware you might found your self researching a bit of history you might forget, reading specific  documentation of software you might not use and maybe running some tests on your local machine in order to fully understand all of these concepts.

## X

The **X Window System** (**X11**, or simply **X**) is a [windowing system](https://en.wikipedia.org/wiki/Windowing_system) for [bitmap](https://en.wikipedia.org/wiki/Bitmap) displays (aka. "the pix-map", which refers to a map of pixels), common on [Unix-like](https://en.wikipedia.org/wiki/Unix-like) [operating systems](https://en.wikipedia.org/wiki/Operating_systems). X provides the basic [framework](https://en.wikipedia.org/wiki/Software_framework) for a [GUI](https://en.wikipedia.org/wiki/Graphical_user_interface) environment: drawing and moving [windows](https://en.wikipedia.org/wiki/Window_(computing)) on the [display device](https://en.wikipedia.org/wiki/Display_device) and interacting with a [mouse](https://en.wikipedia.org/wiki/Computer_mouse) and [keyboard](https://en.wikipedia.org/wiki/Computer_keyboard). X does not mandate the user interface – this is handled by individual programs. As such, the visual styling of X-based environments varies greatly; different programs may present radically different interfaces.

The [X protocol](https://en.wikipedia.org/wiki/X_protocol) (clearly the protocol that X Window System implements) has been at version 11 (hence "X11") since September 1987. The [X.Org Foundation](https://en.wikipedia.org/wiki/X.Org_Foundation) leads the X project, with the current reference implementation, [X.Org Server](https://en.wikipedia.org/wiki/X.Org_Server), available as [free and open source software](https://en.wikipedia.org/wiki/Free_and_open_source_software) under the [MIT License](https://en.wikipedia.org/wiki/MIT_License) and similar [permissive licenses](https://en.wikipedia.org/wiki/Permissive_free_software_licences).

The X Window System is based on a [client–server model](https://en.wikipedia.org/wiki/Client–server_model): a single [server](https://en.wikipedia.org/wiki/Server_(computing)) controls the [input/output](https://en.wikipedia.org/wiki/Input/output) hardware, such as the [screen](https://en.wikipedia.org/wiki/Computer_screen), the [keyboard](https://en.wikipedia.org/wiki/Computer_keyboard), and the [mouse](https://en.wikipedia.org/wiki/Computer_mouse); all application [programs](https://en.wikipedia.org/wiki/Computer_program) act as [clients](https://en.wikipedia.org/wiki/Client_(computing)), interacting with the [user](https://en.wikipedia.org/wiki/User_(computing)) and with the other clients via the server.

**Xorg**

Xorg (commonly referred as simply **X**) is the most popular display server among Linux users. Its ubiquity has led to making it an ever-present requisite for GUI applications, resulting in massive adoption from most distributions. See the [Xorg](https://en.wikipedia.org/wiki/X.Org_Server) Wikipedia article or visit the [Xorg website](https://www.x.org/wiki/) for more details.

In other words, **X** is an **application** that manages one or more graphics displays and one or more input devices (keyboard, mouse, etc.) connected to the computer.

**It works as a server** and can run on the local computer or on another computer on the network. Services can communicate with the X server to display graphical interfaces and receive input from the user.

It's worth noting, a common component used with an X server is the Window Manager, an application that manages the resizing and moving of windows and decorative elements of windows such as title bars, minimize, and close buttons.

The X server can be started with the `startx` command, or more commonly, from a **display manager** such as gdm, lightdm etc...

`~/.xinitrc` is a shell script used by xinit, that starts the X server when not using a display manager, to define some application to start automatically in the X server.

`/etc/X11/xorg.conf` is a configuration file used to give the X server information about the hardware components used, but now the X server can avoid using it, because it is capable of autoconfiguring itself.

**X is a server** (meaning a program which other programs call upon and be called by) which is responsible for creating a graphical environment and if it fails for whatever reason, you'll be greeted by Command Line Interface (CLI).

The term **server** can also be said to apply to PulseAudio, which is the sound server, and it calls applications and is called upon to produce sound.



## Sound Server

In a [Unix-like](https://en.wikipedia.org/wiki/Unix-like) operating system, a sound server mixes different data streams and sends out a single unified audio to an output device. The mixing is usually done by software, or by hardware if there is a supported [sound card](https://en.wikipedia.org/wiki/Sound_card).

**Layer**

The "sound stack" can be visualized as follows, with programs in the upper layers calling elements in the lower layers:

- Applications (e.g. mp3 player, web video)

- Sound server (e.g. aRts, ESD, [JACK](https://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit), [PulseAudio](https://en.wikipedia.org/wiki/PulseAudio))

- Sound subsystem (described as kernel modules or drivers; e.g. [OSS](https://en.wikipedia.org/wiki/Open_Sound_System), [ALSA](https://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture))

- Operating system kernel (e.g. [Linux](https://en.wikipedia.org/wiki/Linux), [Unix](https://en.wikipedia.org/wiki/Unix))

  

## GUI Toolkits

**What is KDE, GTK, GTK+, QT, and/or GNOME?**

**GTK**, **GTK+**, and **Qt** are **GUI toolkits**. These are libraries that developers use to design graphical interfaces, all running on top of the X Server. These are things that you need to install as dependencies. They're the Linux "equivalent" to Windows' **GDI/GDI+**. When an application uses any of these, it will always have a general "look and feel".

**GNOME** and **KDE** are **Desktop Environment**s. **GNOME** primarily uses the **GTK+** toolkit, while **KDE** primarily uses the **Qt** toolkit. *There are applications designed for GNOME or KDE, such as a settings menu or a default music player, usually in the appropriate toolkit*. These Desktop Environments have a set of utilities/window managers/design specification to create a more unified desktop. You can mix the two if you feel like it, but you may run into issues with colliding standards and applications (which you might occasionally run into on systems like Arch).

Unity, another desktop environment, uses many of the GNOME utilities (Nautilus, Rhythmbox, etc.), so Unity is more GNOME than KDE.

*Source: https://askubuntu.com/questions/249150/what-is-kde-gtk-gtk-qt-and-or-gnome*

*For more information: https://wiki.archlinux.org/index.php/Uniform_look_for_Qt_and_GTK_applications*



## Desktop Environments

A [desktop environment](https://en.wikipedia.org/wiki/Desktop_environment) (**DE**) is an implementation of the [desktop metaphor](https://en.wikipedia.org/wiki/Desktop_metaphor) made of a bundle of programs, which share a common graphical user interface (GUI).

A desktop environment bundles together a variety of components to provide common graphical user interface elements such as icons, toolbars, wallpapers, and desktop widgets. Additionally, most desktop environments include a set of integrated applications and utilities. Most importantly, desktop environments provide their own [window manager](https://wiki.archlinux.org/index.php/Window_manager), which can however usually be replaced with another compatible one.

The user is free to configure their GUI environment in any number of ways. Desktop environments simply provide a complete and convenient means of accomplishing this task. Note that users are free to mix-and-match applications from multiple desktop environments. For example, a [KDE](https://wiki.archlinux.org/index.php/KDE) user may install and run [GNOME](https://wiki.archlinux.org/index.php/GNOME) applications such as the [Epiphany](https://wiki.archlinux.org/index.php/Epiphany) web browser, should he/she prefer it over KDE's Konqueror web browser. One drawback of this approach is that many applications provided by desktop environment projects rely heavily upon their DE's respective underlying libraries. As a result, installing applications from a range of desktop environments will require installation of a larger number of dependencies. Users seeking to conserve disk space often avoid such mixed environments, or chose alternatives which do depend on only few external libraries.

Furthermore, DE-provided applications tend to integrate better with their native environments. Superficially, mixing environments with different widget toolkits will result in visual discrepancies (that is, interfaces will use different icons and widget styles). In terms of usability, mixed environments may not behave similarly (e.g. single-clicking versus double-clicking icons; drag-and-drop functionality) potentially causing confusion or unexpected behavior.

Prior to installing a desktop environment, a functional X server installation is required. See [Xorg](https://wiki.archlinux.org/index.php/Xorg) for detailed information. Some desktop environments may also support [Wayland](https://wiki.archlinux.org/index.php/Wayland) as an alternative to X, but most of these are still experimental.



## Windows Manager

A [window manager](https://en.wikipedia.org/wiki/Window_manager) (WM) is system software that controls the placement and appearance of windows within a windowing system in a graphical user interface (GUI). It can be part of a [desktop environment](https://wiki.archlinux.org/index.php/Desktop_environment) (DE) or be used standalone. Window managers are X clients that control the appearance and behavior of the frames ("windows") where the various graphical applications are drawn. They determine the border, title bar, size, and ability to resize windows, and often provide other functionality such as reserved areas for sticking [dockapps](http://windowmaker.org/dockapps/) like [Window Maker](https://wiki.archlinux.org/index.php/Window_Maker), or the ability to tab windows like [Fluxbox](https://wiki.archlinux.org/index.php/Fluxbox). Some window managers are even bundled with simple utilities like menus to start programs or to configure the WM itself.

**There are 3 types of window managers**

- [Stacking](https://wiki.archlinux.org/index.php/Window_manager#Stacking_window_managers) (aka floating) window managers provide the traditional desktop metaphor used in commercial operating systems like Windows and OS X. Windows act like pieces of paper on a desk, and can be stacked on top of each other.
- [Tiling](https://wiki.archlinux.org/index.php/Window_manager#Tiling_window_managers) window managers "tile" the windows so that none are overlapping. They usually make very extensive use of key-bindings and have less (or no) reliance on the mouse. Tiling window managers may be manual, offer predefined layouts, or both. 
- [Dynamic](https://wiki.archlinux.org/index.php/Window_manager#Dynamic_window_managers) window managers can dynamically switch between tiling or floating window layout.

Source: https://wiki.archlinux.org/index.php/Window_manager



## Display Manager

A [display manager](https://en.wikipedia.org/wiki/X_display_manager_(program_type)), or login manager, is typically a graphical user interface that is displayed at the end of the boot process in place of the default shell. There are various implementations of display managers, just as there are various types of [window managers](https://wiki.archlinux.org/index.php/Window_managers) and [desktop environments](https://wiki.archlinux.org/index.php/Desktop_environments). There is usually a certain amount of customization and theme-ability available with each one. Some display manager are LightDM, Gdm, Greetd and XDM



## Init Systems

In [Unix](https://en.wikipedia.org/wiki/Unix)-based computer [operating systems](https://en.wikipedia.org/wiki/Operating_system), **init** (short for *initialization*) is the first [process](https://en.wikipedia.org/wiki/Process_(computer_science)) started during [booting](https://en.wikipedia.org/wiki/Booting) of the computer system. Init is a [daemon](https://en.wikipedia.org/wiki/Daemon_(computing)) process that continues running until the system is shut down. It is the direct or indirect [ancestor](https://en.wikipedia.org/wiki/Parent_process) of all other processes and automatically adopts all [orphaned processes](https://en.wikipedia.org/wiki/Orphan_process). Init is started by the [kernel](https://en.wikipedia.org/wiki/Kernel_(computing)) during the [booting](https://en.wikipedia.org/wiki/Booting) process; a [kernel panic](https://en.wikipedia.org/wiki/Kernel_panic) will occur if the kernel is unable to start it. 

The init *scripts* (or *rc*) are launched by the init process to guarantee basic functionality on system start and shutdown. This includes (un)mounting of [file systems](https://wiki.archlinux.org/index.php/File_system) and launching of [daemons](https://wiki.archlinux.org/index.php/Daemons). A *service manager* takes this one step further by providing active control over launched processes, or [process supervision](https://en.wikipedia.org/wiki/Process_Supervision). An example is to monitor for crashes and restart processes accordingly.

Several additional init implementations have been created, attempting to address design limitations in the traditional versions. These include [launchd](https://en.wikipedia.org/wiki/Launchd), the [Service Management Facility](https://en.wikipedia.org/wiki/Service_Management_Facility), [systemd](https://en.wikipedia.org/wiki/Systemd) and [OpenRC](https://en.wikipedia.org/wiki/OpenRC).

Various efforts have been made to replace the traditional init daemons to address this and other design problems, including:

- [BootScripts](https://en.wikipedia.org/wiki/GoboLinux#Boot_system) in [GoboLinux](https://en.wikipedia.org/wiki/GoboLinux)
- [busybox-init](https://en.wikipedia.org/wiki/Busybox), suited to [embedded operating systems](https://en.wikipedia.org/wiki/Embedded_operating_system), employed by [OpenWrt](https://en.wikipedia.org/wiki/OpenWrt) before it was replaced with [procd](https://en.wikipedia.org/wiki/OpenWrt#procd)
- [Daemons](https://en.wikipedia.org/wiki/Daemon_(computing)), by a modification of the init start process by [KahelOS](https://en.wikipedia.org/w/index.php?title=KahelOS&action=edit&redlink=1), daemons are started only when the DE (desktop environment) started
- eINIT, a full replacement of init designed to start processes [asynchronously](https://en.wikipedia.org/wiki/Asynchrony_(computer_programming)), but with the potential of doing it without [shell scripts](https://en.wikipedia.org/wiki/Shell_scripts)
- [Epoch](https://en.wikipedia.org/w/index.php?title=Epoch_(init_system)&action=edit&redlink=1), a single-threaded Linux init system focused on simplicity and service management[[14\]](https://en.wikipedia.org/wiki/Init#cite_note-14)
- [Initng](https://en.wikipedia.org/wiki/Initng), a full replacement of init designed to start processes asynchronously
- [launchd](https://en.wikipedia.org/wiki/Launchd), a replacement for init in [Darwin](https://en.wikipedia.org/wiki/Darwin_(operating_system))/[macOS](https://en.wikipedia.org/wiki/MacOS)/[iOS](https://en.wikipedia.org/wiki/IOS)/[tvOS](https://en.wikipedia.org/wiki/TvOS) starting with [Mac OS X v10.4](https://en.wikipedia.org/wiki/Mac_OS_X_v10.4) (it launches SystemStarter to run old-style 'rc.local' and SystemStarter processes)
- [Mudur](https://web.archive.org/web/20071211041543/http://www.pardus.org.tr/eng/projeler/comar/SpeedingUpLinuxWithPardus.html), an init replacement written in [Python](https://en.wikipedia.org/wiki/Python_(programming_language)) and designed to start process asynchronously in use by the [Pardus](https://en.wikipedia.org/wiki/Pardus_(operating_system)) Linux distribution
- [procd](https://lede-project.org/docs/guide-developer/procd) is used in LEDE/OpenWRT
- [some unnamed proofs-of concept](https://web.archive.org/web/20070824084840/http://www-128.ibm.com/developerworks/linux/library/l-boot.html) based on [Make](https://en.wikipedia.org/wiki/Make_(software)) (since makefiles can easily express dependencies and be launched in parallel)
- nosh, a suite of system-level utilities for initializing and running a BSD or Linux system, for managing daemons, terminals and logging
- [OpenRC](https://en.wikipedia.org/wiki/OpenRC), a process spawner that utilizes system-provided init, while providing process isolation, parallelized startup, and service dependency; used by [Gentoo](https://en.wikipedia.org/wiki/Gentoo_Linux) and its derivatives and available as an option in [Devuan](https://en.wikipedia.org/wiki/Devuan)
- [runit](https://en.wikipedia.org/wiki/Runit), a [cross-platform](https://en.wikipedia.org/wiki/Cross-platform) full replacement for init with parallel starting of services, used by default in [Void Linux](https://en.wikipedia.org/wiki/Void_Linux) and Artix Linux.
- s6, another cross-platform full replacement for init, similar to runit, based on clear principled architecture design choices.
- Sun [Service Management Facility](https://en.wikipedia.org/wiki/Service_Management_Facility) (SMF), a complete replacement/redesign of init from the ground up in [illumos](https://en.wikipedia.org/wiki/Illumos)/[Solaris](https://en.wikipedia.org/wiki/Solaris_(operating_system)) starting with Solaris 10, but launched as the only service by the original System V-style init
- [Shepherd](https://en.wikipedia.org/wiki/Guix_System_Distribution#GNU_Shepherd), the [GNU](https://en.wikipedia.org/wiki/GNU) service and daemon manager which provides asynchronous, dependency-based initialisation; written in [Guile Scheme](https://en.wikipedia.org/wiki/Guile_(programming_language)) and meant to be interactively hackable during normal system operation
- [systemd](https://en.wikipedia.org/wiki/Systemd), a software suite, full replacement for init in Linux that includes an init daemon, with concurrent starting of services, service manager, and other features.
- [SystemStarter](https://en.wikipedia.org/wiki/SystemStarter), a process spawner started by the BSD-style init in [Mac OS X](https://en.wikipedia.org/wiki/Mac_OS_X) prior to Mac OS X v10.4
- [Upstart](https://en.wikipedia.org/wiki/Upstart_(software)), a full replacement of init designed to start processes asynchronously. Initiated by [Ubuntu](https://en.wikipedia.org/wiki/Ubuntu_(operating_system)) and used by them until 2014. It was also used in Fedora 9, Red Hat Enterprise Linux 6 and [Google](https://en.wikipedia.org/wiki/Google)'s [Chrome OS](https://en.wikipedia.org/wiki/Chrome_OS).

As of February 2019, systemd has been [adopted](https://en.wikipedia.org/wiki/Systemd#Adoption_and_reception) by most major Linux distributions.


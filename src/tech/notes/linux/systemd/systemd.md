# Systemd


Systemd is a system and service manager for Linux operating systems. When run as first process on boot (as PID 1), it acts as init system that brings up and maintains userspace services. Separate instances are started for logged-in users to start their services.
Systemd is usually not invoked directly by the user, but is installed as the /sbin/init symlink and started during early boot. The user manager instances are started automatically through the user@.service(5) service.

## Before systemd (SysV init)
Before systemd, the init system used previously in Linux was called SysVinit. A script used to manage a service in SysVinit was known as a SysV init script, which were "*imperative*". Backwards compatibility for legacy scripts remains 99.9% intact with systemd.

[Example for the sshd SysV init script](http://www.styma.org/SunAtHome/sample_files/sshd.html)

Nowadays the Systemd unit files are "*declaratives*" and systemd simply
interprets them and hanldes the initialization of the service. For example the sshd.service unit file

Just `cat $(pkg-config systemd --variable=systemdsystemunitdir)/sshd.service` :

```toml
[Unit]
Description=OpenSSH Daemon
Wants=sshdgenkeys.service
After=sshdgenkeys.service
After=network.target

[Service]
ExecStart=/usr/bin/sshd -D
ExecReload=/bin/kill -HUP $MAINPID
KillMode=process
Restart=always

[Install]
WantedBy=multi-user.target
```

# Unit files

The unit files on your system determine how systemd will start and run. Each corresponds to a single activity or component — or unit in systemd terms. Each unit file is a simple text file describing a unit, what it does, what needs to run before or afterward, and other details.

To see a list of all the unit files installed in the system.

```shell
systemctl list-unit-files
```

## System unit directories 
(from the man page)

The systemd system manager reads unit configuration from various directories. Packages that want to install unit files shall place them in the directory returned by `pkg-config systemd --variable=systemdsystemunitdir`. Other directories checked are `/usr/local/lib/systemd/system` and `/usr/lib/systemd/system`.
User always take precedence. `pkg-config systemd --variable=systemdsystemconfdir` returns the path of the system configuration directory

Packages should alter the content of these directories only with the enable and disable commands of the systemctl(1) tool

## User unit directories
Applications should place their unit files in the directory returned by `pkg-config systemd --variable=systemduserunitdir`. Global configuration is done in the directory reported by `pkg-config systemd --variable=systemduserconfdir`. The enable and disable commands of the systemctl(1) tool can handle both global (i.e. for all users) and private (for one user) enabling/disabling of units.


# Unit types

There are numerous types of units systemd understands. The two most common for system owners to deal with are service units and target units. To list unit files on your system of each of these types, use the systemctl command:

```shell
systemctl list-unit-files --type service
systemctl list-unit-files --type target
```

## Service units

```shell
man systemd.service
```

One interesting feature of systemd is that it monitors processes it **starts with service units**.

For example: `/usr/lib/systemd/system/sshd.service`

```shell
sudo systemctl [command] NAME.service
```

Typical commands include:

* **start**: starts a systemd unit
* **stop**: attempts to “nicely” end a service
* **status**: provides detailed information on a service
* **restart**: restarts (stops and then starts) the specified service
* **enable**: hooks (links) a unit to various places, for instance to run at boot
* **disable**: unhooks (unlinks) a unit, so it is not activated
* **kill**: when a service refuse to cooperate :eyes:

## Target units

Target units are used to link and group other units together to describe a desired system state. Some of these units may be services. Others may be additional target units with their own groups of units.

```shell
man systemd.target
```

Example 1. Simple standalone target

```toml
# emergency-net.target
[Unit]
Description=Emergency Mode with Networking
Requires=emergency.target systemd-networkd.service
After=emergency.target systemd-networkd.service
AllowIsolate=yes
```

#### Source
* These series of blog posts: https://fedoramagazine.org/what-is-an-init-system/
* Systemd man pages: https://man7.org/linux/man-pages/man1/systemd.1.html

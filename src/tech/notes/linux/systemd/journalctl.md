# Systemd's Journal



Before systemd-journald was [syslog](https://en.wikipedia.org/wiki/Syslog)

**systemd-journald** is a system service that collects and stores logging data. It creates and maintains structured, indexed journals based on logging information that is received from a variety of sources:

* Kernel log messages, via kmsg
* Simple system log messages, via the libc syslog(3) call
* Structured system log messages via the native Journal API, see sd_journal_print(3)
* Standard output and standard error of service units. For further details see below.
* Audit records, originating from the kernel audit subsystem

The daemon will implicitly collect numerous metadata fields for each log messages in a secure and unfakeable way

## Data Store

The journal service stores log data either persistently below **/var/log/journal** or in a volatile way below **/run/log/journal/** (in the latter case it is lost at reboot).
By default, log data is stored persistently if /var/log/journal/ exists during boot, with an implicit fallback to volatile storage otherwise
Use `Storage=` in `/etc/systemd/journald.conf` (see `man journald.conf`) to configure where log data is placed, independently of the existence of /var/log/journal/

Logs are store in the following files: 

* `/run/log/journal/machine-id/*.journal`
* `/run/log/journal/machine-id/*.journal~`
* `/var/log/journal/machine-id/*.journal`
* `/var/log/journal/machine-id/*.journal~`

**Note:** If the daemon is stopped uncleanly, or if the files are found to be corrupted, they are renamed using the **".journal~"**

## journalctl

`journalctl` is the command line tool to query the systemd journal (`man journalctl`)

If called without parameters, it will show the full contents of the journal, starting with the oldest entry collected


## Some my most used journal commands:

```bash
journalctl -e # to start from last to old
# or
journalctl -r # to reverse it
# or
journalctl -o <output-mode>
# Output modes: short, short-precise, short-iso, short-iso-precise, short-full, short-monotonic, short-unix, verbose, export, json, json-pretty, json-sse, json-seq, cat, with-unit
journalctl -b <boot-id|empty> -u <UnitName> # If boot-id may be empty, in which case logs for the current boot will be shown.
# or
journalctl -p <priority> # priority: "emerg", "alert", "crit", "err", "warning", "notice", "info", "debug".
```


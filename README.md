# Jadloop

A script for displaying package tracking info from
[Jadlog](http://www.jadlog.com.br/)'s API.

```
Usage: jadloop <command> <tracking_number>

Commands:
   get          Display the current tracking info.
   get-changes  Display only new info (i.e., changes since last called).
   notify       Same as 'update', but also show a desktop notification.
   reset        Reset the cached info used by 'update' and 'notify'.
```

## Requirements

On Debian/Ubuntu based systems:

```sh
apt install curl libnotify-bin pandoc
```

* [curl](https://curl.haxx.se/)
* [libnotify](https://developer.gnome.org/libnotify/)
* [pandoc](https://pandoc.org/)

## Systemd service and timer

Also included in this repo are a couple of systemd unit files that
enable notifications of tracking updates to your desktop.
To install them, put them in the `~/.config/systemd/user` directory,
and activate the timer like so, substituting in your tracking number:

```sh
systemctl enable --now --user jadloop@TRACKING_NUMBER.timer
```

You may edit the timer unit file to change the update period.
By default, it checks for new information every 20 minutes.

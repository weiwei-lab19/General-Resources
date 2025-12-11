# Cheat Sheet

Fetch latest version of package list from distro software repo and any third-party repos, will not install any of those updates
```bash
$ sudo apt-get update
```

Download and install the updates for each outdated package and dependency on system, you will be asked if you want to download updates if they are available.
```bash
$ sudo apt-get upgrade
```

Display useful information about USB buses and devices connected to them
```bash
$ lsusb
```

Go back to the previous directory
```bash
$ cd ..
```

Search list of paths in`$PATH` environment variable and output the full path of the command specified
```bash
$ which <command>
```
- EXAMPLE
    ```bash
    $ which lsusb/usr/bin/lsusb
    ```
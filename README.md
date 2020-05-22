# swiftbox: Use Swift out of the Box on Ubuntu, CentOS(RHEL) and Amazon Linux

![Release](https://img.shields.io/github/v/release/stevapple/swiftbox?logo=github) ![CI Status](https://github.com/stevapple/swiftbox/workflows/CI/badge.svg)

Inspired by [pyenv](https://github.com/pyenv/pyenv) and [rbenv](https://github.com/rbenv/rbenv), and having different APIs. 

## Installation

By default, `swiftbox` will be installed at `/usr/bin`. The working directory will be set to `/opt/swiftbox` for `root` and `~/.swiftbox` for other users. 

There will be two sets of Swift environments if you use both. The local one is in favor by default unless you access `swiftbox` with `sudo`. Toolchains installed by `root` can be used by all users. 

```bash
# With curl (Recommended)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/stevapple/swiftbox/master/install.sh)"
swiftbox version

# With git
git clone https://github.com/stevapple/swiftbox && cd swiftbox
chmod +x install.sh
./install.sh
```

Or if you'd like to use it as a script (do not support `update` yet):

```bash
# With wget
wget https://raw.githubusercontent.com/stevapple/swiftbox/master/swiftbox.sh
chmod +x swiftbox.sh
./swiftbox.sh version

# With curl
curl -o swiftbox.sh https://raw.githubusercontent.com/stevapple/swiftbox/master/swiftbox.sh
chmod +x swiftbox.sh
./swiftbox.sh version

# With git
git clone https://github.com/stevapple/swiftbox && cd swiftbox
chmod +x swiftbox.sh
./swiftbox.sh version
```

You can designate a release version by using jsDelivr or git, which also has wider availability:

```bash
# With wget
wget https://cdn.jsdelivr.net/gh/stevapple/swiftbox@0.10/swiftbox.sh
chmod +x swiftbox.sh
./swiftbox.sh version

# With curl
curl -o swiftbox.sh https://cdn.jsdelivr.net/gh/stevapple/swiftbox@0.10/swiftbox.sh
chmod +x swiftbox.sh
./swiftbox.sh version

# With git
git clone https://github.com/stevapple/swiftbox && cd swiftbox
git checkout v0.10
chmod +x swiftbox.sh
./swiftbox.sh version
```

You can later install it to `/usr/bin`:

```shell
$ sudo ./swiftbox.sh install
Successfully installed swiftbox at /usr/bin
$ which swiftbox
/usr/bin/swiftbox
```

## Example Usage

### Lookup `swiftbox` version

```shell
$ swiftbox version
0.9
```

### Check the availability of Swift versions

```shell
$ swiftbox lookup 5.1
Swift 5.1 is available for Ubuntu 18.04
$ swiftbox lookup nightly
Swift nightly build 2020-05-11-a is available for Ubuntu 18.04
$ swiftbox lookup 2.1
Swift 2.1 does not exist or does not support your Ubuntu version. 
```

### Manage Swift versions

Both release builds and the latest nightly build are available. 

```shell
$ swiftbox get 5.2.2
$ swiftbox get nightly
$ swiftbox remove 5.0
```

### Switch to a Swift version

```shell
$ swiftbox use 5.2.2
Now using Swift 5.2.2 
```

### Disable Swift

```shell
$ swiftbox close
Swift 5.2.2 is now disabled. 
```

### Lookup installed Swift versions

The active one is marked with `*`. 

```shell
$ swiftbox list
- 2020-05-10-a
- 4.2.1
* 5.2.2
```

### Clear download cache

```shell
$ swiftbox clean
Successfully cleaned the cache. 
```

### Update `swiftbox`

Update to the latest version if `swiftbox` is installed in `/usr/bin`. 

```shell
$ swiftbox update
Successfully upgraded swiftbox from 0.6.2 to 0.9
```

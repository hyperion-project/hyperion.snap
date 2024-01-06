# Hyperion Snap
[![Get it from the Snap Store](https://snapcraft.io/static/images/badges/en/snap-store-black.svg)](https://snapcraft.io/hyperion-ng)

This repository contains snap packaging for Hyperion.

## Installation

### Installing snapd
The snap can be installed on any system that supports snaps. You can see how to install 
snaps on your system [here](https://snapcraft.io/docs/installing-snapd).

### Installing Hyperion as a snap
The snap is published in the snap store at https://snapcraft.io/hyperion-ng.
You can see the current revisions available for your machine's architecture by running the command:

```bash
snap info hyperion-ng
```

The snap can be installed using `snap install`. To install the snap from the edge channel:

```bash
sudo snap install hyperion-ng --edge
```

## Building

> [!NOTE]  
> The following instructions were written for Linux.

The snap is built with [snapcraft](https://snapcraft.io) and the snapcraft.yaml recipe is located in the snap directory.
So the first step to building it is to clone this repository:

```bash
git clone https://github.com/hyperion-project/hyperion.snap.git
cd hyperion.snap
```

### Installing Snapcraft

To install snapcraft, first install the [snap deamon (snapd)](https://snapcraft.io/docs/installing-snapd), then install snapcraft as a classic snap with:

```bash
sudo snap install snapcraft --classic
```

### Installing LXD and Multipass

LXD is required under Linux during the snap-build process. 
However, since we prefer Multipass as a provider, we also install Multipass and connect it to LXD with the following commands:

```bash
sudo snap install lxd
sudo snap install multipass --classic
sudo snap connect multipass:lxd lxd
```

### Building

Now you can build the snap with the following command:

```bash
SNAPCRAFT_BUILD_ENVIRONMENT=multipass snapcraft --debug
```

### Developing the snap

After building the snap, you will have a binary snap package called `hyperion-ng_<latest version>_<arch>.snap`, which can be installed locally with the `--devmode` flag:

```bash
sudo snap install --devmode hyperion-ng*.snap
```

And uninstalling is done with this command:

```bash
sudo snap remove hyperion-ng
```

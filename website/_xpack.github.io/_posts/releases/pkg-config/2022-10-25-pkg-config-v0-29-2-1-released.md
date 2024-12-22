---

title:  xPack pkg-config v0.29.2-1 released

summary: "Version **0.29.2-1** is the first release of xPack pkg-config."

pkg_config_version: "0.29.2"
pkg_config_date: "2017-03-20"
version: "0.29.2-1"
npm_subversion: 1

download_url: https://github.com/xpack-dev-tools/pkg-config-xpack/releases/tag/v0.29.2-1/

date: 2022-10-25 14:02:09 +0300

redirect_to: https://xpack-dev-tools.github.io/pkg-config-xpack/blog/2022/10/25/pkg-config-v0-29-2-1-released/

# For Jekyll releases selection.
comments: true

categories:
  - releases
  - pkg-config

# For navigation; use scripts/createtag.sh in Jekyll.
tags:
  - releases
  - pkg-config

---

The [xPack pkg-config](https://xpack.github.io/dev-tools/pkg-config/)
is a standalone cross-platform binary distribution of
[pkg-config](https://www.freedesktop.org/wiki/Software/pkg-config/).

There are separate binaries for
**macOS** (x64 and arm64)
and **GNU/Linux** (x64, arm64 and arm).

{% include note.html content="The main targets for the GNU/Linux Arm
binaries are the **Raspberry Pi** class devices (armv7l and aarch64;
armv6 is not supported)." %}

## Download

The binary files are available from [GitHub Releases]({{ page.download_url }}).

## Prerequisites

- x64 GNU/Linux: any system with **GLIBC 2.27** or higher
  (like Ubuntu 18 or later, Debian 10 or later, RedHat 8 or later,
  Fedora 29 or later, etc)
- arm64/arm GNU/Linux: any system with **GLIBC 2.27** or higher
  (like Raspberry Pi OS, Ubuntu 18 or later, Debian 10 or later, RedHat 8 or later,
  Fedora 29 or later, etc)
- x64 macOS: 10.13 or later
- arm64 macOS: 11.6 or later

## Install

The full details of installing the **xPack pkg-config** on various platforms
are presented in the separate [Install]({{ site.baseurl }}/dev-tools/pkg-config/install/) page.

### Easy install

The easiest way to install pkg-config is with
[`xpm`]({{ site.baseurl }}/xpm/)
by using the **binary xPack**, available as
[`@xpack-dev-tools/pkg-config`](https://www.npmjs.com/package/@xpack-dev-tools/pkg-config)
from the [`npmjs.com`](https://www.npmjs.com) registry.

With the `xpm` tool available, installing
the latest version of the package and adding it as
a dependency for a project is quite easy:

```sh
cd my-project
xpm init # Only at first use.

xpm install @xpack-dev-tools/pkg-config@latest

ls -l xpacks/.bin
```

To install this specific version, use:

```sh
xpm install @xpack-dev-tools/pkg-config@{{ page.version }}.{{ page.npm_subversion }}
```

It is also possible to install Meson Build globally, in the user home folder,
but this requires xPack aware tools to automatically identify them and
manage paths.

```sh
xpm install --global @xpack-dev-tools/pkg-config@latest --verbose
```

### Uninstall

To remove the links created by xpm in the current project:

```sh
cd my-project

xpm uninstall @xpack-dev-tools/pkg-config
```

To completely remove the package from the central xPacks store:

```sh
xpm uninstall --global @xpack-dev-tools/pkg-config
```

## Compliance

The xPack pkg-config generally follows the official
[pkg-config](https://pkgconfig.freedesktop.org/releases/) releases.

The current version is based on:

- pkg-config version {{ page.pkg_config_version }}
from {{ page.pkg_config_date }}.

## Changes

Compared to the upstream version, there are no functional changes.

## Bug fixes

- none

## Enhancements

- none

## Known problems

- none

## Shared libraries

On all platforms the packages are standalone, and expect only the standard
runtime to be present on the host.

All dependencies that are build as shared libraries are copied locally
in the `libexec` folder (or in the same folder as the executable for Windows).

### `DT_RPATH` and `LD_LIBRARY_PATH`

On GNU/Linux the binaries are adjusted to use a relative path:

```console
$ readelf -d library.so | grep runpath
 0x000000000000001d (RPATH)            Library rpath: [$ORIGIN]
```

In the GNU ld.so search strategy, the `DT_RPATH` has
the highest priority, higher than `LD_LIBRARY_PATH`, so if this later one
is set in the environment, it should not interfere with the xPack binaries.

Please note that previous versions, up to mid-2020, used `DT_RUNPATH`, which
has a priority lower than `LD_LIBRARY_PATH`, and does not tolerate setting
it in the environment.

### `@rpath` and `@loader_path`

Similarly, on macOS, the binaries are adjusted with `install_name_tool` to use a
relative path.

## Documentation

The original documentation is available
[online](https://people.freedesktop.org/~dbn/pkg-config-guide.html).

## Build

The binaries for all supported platforms
(Windows, macOS and GNU/Linux) were built using the
[xPack Build Box (XBB)](https://xpack.github.io/xbb/), a set
of build environments based on slightly older distributions, that should be
compatible with most recent systems.

The scripts used to build this distribution are in:

- `distro-info/scripts`

For the prerequisites and more details on the build procedure, please see the
[README-MAINTAINER](https://github.com/xpack-dev-tools/pkg-config-xpack/blob/xpack/README-MAINTAINER.md) page.

## CI tests

Before publishing, a set of simple tests were performed on an exhaustive
set of platforms. The results are available from:

- [GitHub Actions](https://github.com/xpack-dev-tools/pkg-config-xpack/actions/)
- [Travis CI](https://app.travis-ci.com/github/xpack-dev-tools/pkg-config-xpack/builds/)

## Tests

TBD

## Checksums

The SHA-256 hashes for the files are:

```txt
64e411380f9b51271015573f32191657e5fec92106c84cbd08227b497a483882
xpack-pkg-config-0.29.2-1-darwin-arm64.tar.gz

9d998eaaa6328eb5aff985d83f90f15d89a1bfedab0e0c8e48b5ff6d87f64076
xpack-pkg-config-0.29.2-1-darwin-x64.tar.gz

09e3a3d8ed82bd0bfdebf0b4893cfafebe902f026872699676c7e267cabd60fe
xpack-pkg-config-0.29.2-1-linux-arm.tar.gz

92f8a608328af736cd84fccd316190af862b9354b960ac853a4fe2fabab72271
xpack-pkg-config-0.29.2-1-linux-arm64.tar.gz

066a6f55165c6cc6082c8dfabf9c5573938f680e71a125b874d7176557db2497
xpack-pkg-config-0.29.2-1-linux-x64.tar.gz

```

## Deprecation notices

### 32-bit support

Support for 32-bit x86 GNU/Linux and x86 Windows was
dropped in 2022. Support for 32-bit Arm GNU/Linux (armv7l) will be preserved
for a while, due to the large user base of 32-bit Raspberry Pi systems.

### GNU/Linux minimum requirements

Support for RedHat 7 was dropped in 2022 and the
minimum requirement was raised to GLIBC 2.27, available starting
with Ubuntu 18, Debian 10 and RedHat 8.

## Download analytics

- GitHub [xpack-dev-tools/pkg-config-xpack](https://github.com/xpack-dev-tools/pkg-config-xpack/)
  - this release [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/pkg-config-xpack/v{{ page.version }}/total.svg)](https://github.com/xpack-dev-tools/pkg-config-xpack/releases/v{{ page.version }}/)
  - all xPack releases [![Github All Releases](https://img.shields.io/github/downloads/xpack-dev-tools/pkg-config-xpack/total.svg)](https://github.com/xpack-dev-tools/pkg-config-xpack/releases/)
  - [individual file counters](https://somsubhra.github.io/github-release-stats/?username=xpack-dev-tools&repository=pkg-config-xpack) (grouped per release)
- npmjs.com [@xpack-dev-tools/pkg-config](https://www.npmjs.com/package/@xpack-dev-tools/pkg-config)
  - latest releases [![npm](https://img.shields.io/npm/dw/@xpack-dev-tools/pkg-config.svg)](https://www.npmjs.com/package/@xpack-dev-tools/pkg-config/)
  - all @xpack-dev-tools releases [![npm](https://img.shields.io/npm/dt/@xpack-dev-tools/pkg-config.svg)](https://www.npmjs.com/package/@xpack-dev-tools/pkg-config/)

Credit to [Shields IO](https://shields.io) for the badges and to
[Somsubhra/github-release-stats](https://github.com/Somsubhra/github-release-stats)
for the individual file counters.

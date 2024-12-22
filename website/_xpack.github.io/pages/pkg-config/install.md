---

title: How to install the xPack pkg-config binaries
permalink: /dev-tools/pkg-config/install/

summary: "The recommended method is via xpm."

version: "0.29.2"
xpack-subversion: "2"

comments: true
toc: false

date: 2022-10-04 10:32:00 +0300

redirect_to: https://xpack-dev-tools.github.io/pkg-config-xpack/docs/install/

---

## Overview

The **xPack pkg-config** can be installed automatically, via `xpm` (the
recommended method), or manually, by downloading and unpacking one of the
portable archives.

{% capture easy_install %}

## Easy install

The easiest way to install pkg-config is by using the **binary xPack**, available as
[`@xpack-dev-tools/pkg-config`](https://www.npmjs.com/package/@xpack-dev-tools/pkg-config)
from the [`npmjs.com`](https://www.npmjs.com) registry.

### Prerequisites

The only requirement is a recent
xpm, which is a portable
[Node.js](https://nodejs.org) command line application. To install it,
follow the instructions from the
[xpm install]({{ site.baseurl }}/xpm/install/) page.

### Install

With xpm available, installing
the latest version of the package is quite easy:

```sh
cd my-project
xpm init # Only at first use.

xpm install @xpack-dev-tools/pkg-config@latest --verbose
```

This command will always install the latest available version,
in the global xPacks store, which is a platform dependent folder
(check the output of the `xpm` command for the actual folder used on
your platform).

{% capture include_1 %}
The install location can be configured using the
`XPACKS_STORE_FOLDER` environment variable; for more details please check the
[xpm folders]({{ site.baseurl }}/xpm/folders/) page.
{% endcapture %}

{% include tip.html content=include_1 %}

{% include tip.html content="The archive content is unpacked into a folder
named `.content`. On some platforms
this might be hidden for normal browsing, and require
separate options (like `ls -A`) or, in file browsers, to enable
settings like **Show Hidden Files**." %}

### Uninstall

To remove the links from the current project:

```sh
cd my-project

xpm uninstall @xpack-dev-tools/pkg-config
```

To completely remove the package from the central xPacks store:

```sh
xpm uninstall --global @xpack-dev-tools/pkg-config --verbose
```

{% endcapture %}

{% capture manual_install %}

## Manual install

For all platforms, the **xPack pkg-config** binaries are released as portable
archives that can be installed in any location.

The archives can be downloaded from the
GitHub [releases](https://github.com/xpack-dev-tools/pkg-config-xpack/releases/)
page.

{% endcapture %}

{% capture windows %}

Binaries are available only for GNU/Linux and macOS.

{% endcapture %}

{% capture macos %}

{{ easy_install }}

### Test

To check if the xpm installed pkg-config starts, use something like:

```console
$ ~/Library/xPacks/@xpack-dev-tools/pkg-config/{{ page.version }}-{{ page.xpack-subversion }}.1/.content/bin/pkg-config --version
{{ page.version }}
```

{{ manual_install }}

### Download

The macOS versions of **xPack pkg-config**
are packed as `.tar.gz` archives.
Download the latest version named like:

- `xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}-darwin-x64.tar.gz`
- `xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}-darwin-arm64.tar.gz`

### Unpack

To manually install the xPack pkg-config,
unpack the archive and move it to
`~/.local/xPacks/pkg-config/xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}`:

```sh
mkdir -p ~/.local/xPacks/pkg-config
cd ~/.local/xPacks/pkg-config

tar xvf ~/Downloads/xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}-darwin-x64.tar.gz
chmod -R -w xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}
```

{% include note.html content="For manual installs, the recommended
install location is different from the xpm install folders." %}

The result is a structure like:

```console
$ tree -L 2 /Users/ilg/.local/xPacks/pkg-config/xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}
/Users/ilg/.local/xPacks/pkg-config/xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}/
├── README.md
├── bin
│   └── pkg-config
├── distro-info
│   ├── CHANGELOG.md
│   ├── licenses
│   ├── patches
│   └── scripts
├── libexec
│   └── libiconv.2.dylib
└── share
    ├── aclocal
    └── doc

9 directories, 4 files
```

### Test

To check if the manually installed pkg-config starts, use something like:

```console
$ ~/.local/xPacks/pkg-config/xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}/bin/pkg-config --version
{{ page.version }}
```

{% endcapture %}

{% capture linux %}

{{ easy_install }}

### Test

To check if the xpm installed pkg-config starts, use something like:

```console
$ ~/.local/xPacks/@xpack-dev-tools/pkg-config/{{ page.version }}-{{ page.xpack-subversion }}.1/.content/bin/pkg-config --version
{{ page.version }}
```

{{ manual_install }}

### Download

The GNU/Linux versions of **xPack pkg-config**
are packed as `.tar.gz` archives.
Download the latest version named like:

- `xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}-linux-x64.tar.gz`

As the name implies, these are GNU/Linux `tar.gz` archives; they were build on
Ubuntu, but can be executed on most recent GNU/Linux distributions.

### Unpack

To manually install the xPack pkg-config,
unpack the archive and move it to
`~/.local/xPacks/pkg-config/xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}`:

```console
mkdir -p ~/.local/xPacks/pkg-config
cd ~/.local/xPacks/pkg-config

tar xvf ~/Downloads/xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}-linux-x64.tar.gz
chmod -R -w xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}
```

{% include note.html content="For manual installs, the recommended
install location is slightly different from the xpm install folders,
which use the scope (like `@xpack-dev-tools`) to group different tools,
and `.content` to store the unpacked archive." %}

```console
$ tree -L 2 '/home/ilg/.local/xPacks/pkg-config/xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}'
/home/ilg/.local/xPacks/pkg-config/xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}/
├── README.md
├── bin
│   └── pkg-config
├── distro-info
│   ├── CHANGELOG.md
│   ├── licenses
│   ├── patches
│   └── scripts
├── libexec
│   ├── libiconv.so.2 -> libiconv.so.2.6.1
│   └── libiconv.so.2.6.1
└── share
    ├── aclocal
    └── doc

9 directories, 5 files
```

### Test

To check if the manually installed pkg-config starts, use something like:

```console
$ ~/.local/xPacks/pkg-config/xpack-pkg-config-{{ page.version }}-{{ page.xpack-subversion }}/bin/pkg-config --version
{{ page.version }}
```

{% endcapture %}

{% include platform-tabs.html %}

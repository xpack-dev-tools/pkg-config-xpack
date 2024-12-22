---

title: The xPack pkg-config
permalink: /dev-tools/pkg-config/

summary: "A binary distribution of pkg-config."

keywords: pkg-config

comments: true

date: 2022-10-04 10:32:00 +0300

redirect_to: https://xpack-dev-tools.github.io/pkg-config-xpack/

---

## Quicklinks

If you already know the general facts about the xPack pkg-config, you can
directly skip to the desired pages.

User pages:

- [install]({{ site.baseurl }}/pkg-config/install/)
- [support]({{ site.baseurl }}/pkg-config/support/)
- [releases]({{ site.baseurl }}/pkg-config/releases/)

Developer & maintainer pages:

- [GitHub](https://github.com/xpack-dev-tools/pkg-config-xpack/)
- [README-MAINTAINER](https://github.com/xpack-dev-tools/pkg-config-xpack/blob/xpack/README-MAINTAINER.md)

## Overview

The **xPack pkg-config** is a cross-platform binary distribution of the
[pkg-config](https://www.freedesktop.org/wiki/Software/pkg-config/) project,
an open source project hosted on
[freedesktop.org](https://gitlab.freedesktop.org/pkg-config/pkg-config.git).

## Benefits

The main advantages of using the **xPack pkg-config** are:

- a convenient, uniform and portable install/uninstall/upgrade procedure
- a better integration with development environments
- a more convenient integration with CI environment

All binaries are self-contained, they include all required libraries,
and can be installed in any location.

## Compatibility

The **xPack pkg-config** is fully compatible with the original **pkg-config**
distribution.

## Install

The details of installing the **xPack pkg-config** on various platforms are
presented in the separate
[install]({{ site.baseurl }}/pkg-config/install/) page.

## Documentation

The current version specific pkg-config documentation is available online from:

- [https://people.freedesktop.org/~dbn/pkg-config-guide.html](https://people.freedesktop.org/~dbn/pkg-config-guide.html)

## Support

For the various support options, please read the separate
[support]({{ site.baseurl }}/pkg-config/support/) page.

## Change log

The release and change log is available in the repository
[`CHANGELOG.md`](https://github.com/xpack-dev-tools/pkg-config-xpack/blob/xpack/CHANGELOG.md) file.

## Build details

For those interested in building the binaries, please read the
[README-MAINTAINER](https://github.com/xpack-dev-tools/pkg-config-xpack/blob/xpack/README-MAINTAINER.md)
page.
However, the ultimate source for details are the build scripts themselves,
all available from the
[`pkg-config-xpack.git/scripts`](https://github.com/xpack-dev-tools/pkg-config-xpack/tree/xpack/scripts/)
folder.

## Releases

See the [releases]({{ site.baseurl }}/pkg-config/releases/) pages.

# Gentoo Ebuilding Guide
___

## Custom repository

```
root # eselect repository create my_repository
```

## Write an Ebuild

```sh
user $ mkdir --parents /var/db/repos/my_repository/{CATEGORY}/{PN}
user $ cp /var/db/repos/gentoo/skel.ebuild /var/db/repos/my_repository/{CATEGORY}/{PN}
user $ cd /var/db/repos/my_repository/{CATEGORY}/{PN}
user $ nano {P}.ebuild
```

### Ebuild File Structure
```py
my-package-1.0.0.ebuild
________________________

# Copyright 1999-2023 Gentoo Authors
# Distributed under the terms of the GNU General Public License v2

EAPI=8

DESCRIPTION="Some description here"
HOMEPAGE="https://github.com/some/repo"
SRC_URI="https://github.com/some/repo/releases/download/2.6.1/my-package-1.0.0.ebuid"

LICENSE="GPL-2"
SLOT="0"
KEYWORDS="~amd64 ~x86"
IUSE=""

DEPEND=""
RDEPEND="${DEPEND}"
BDEPEND=""
```

## Test Fetching and Unpacking of the Package
___

```sh
user $ GENTOO_MIRRORS="" ebuild ./my-package-1.0.0.ebuild manifest clean unpack
```

### Run a test suite
```sh
root # ebuild my-package-1.0.0.ebuild clean test install
```
### Install new ebuild into the system
```sh
root # ebuild my-package-1.0.0.ebuild clean install merge
```


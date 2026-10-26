# positron-ide-daily-bin

<!-- badges: start -->
[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)
[![GPLv3 License Badge](https://img.shields.io/badge/license-GPLv3-bd0000.png)](https://www.gnu.org/licenses/gpl-3.0)
<!-- badges: end -->

## Overview

This repository contains a [PKGBUILD](https://wiki.archlinux.org/title/PKGBUILD) script for building and installing the latest daily build of the [Positron IDE](https://github.com/posit-dev/positron). It is based on the [positron-ide-devel-bin](https://aur.archlinux.org/packages/positron-ide-devel-bin) package published on the Arch User Repository ([AUR](https://aur.archlinux.org/)) by [ponte-vecchio](https://github.com/ponte-vecchio), but it follows the daily builds instead of the monthly releases.

The package conflicts with `positron-bin` and `positron-ide-devel-bin`, since all of them install the same files. Pacman will ask to remove the other one when you install this package.

## Usage

To build and install the package, follow these steps:

1. **Clone the Repository**: Open your terminal and run the following command to clone this repository:

```bash
  git clone https://github.com/danielvartan/positron-ide-daily-bin
```

2. **Navigate to the Directory**: Change into the cloned repository's directory:

```bash
  cd positron-ide-daily-bin
```

3. **Build and Install the Package**: Use the `makepkg` command to build and install the package:

```bash
  makepkg -si
```

This command will download all the files, build the package, and install it on your system.

## Daily builds

The package follows the [daily builds](https://positron.posit.co/updating.html#daily-builds) of Positron, not the monthly releases. A GitHub Actions workflow checks the daily build feed every 6 hours and opens a pull request when a newer build is available.

Posit removes daily builds from its servers after 60 days. If `makepkg` fails with a 404 error while downloading, the pinned build has aged out. Run `git pull` to get the current one, or update `pkgver`, `pkgver_url`, and the checksums in the `PKGBUILD` by hand using the values in `https://cdn.posit.co/positron/dailies/deb/x86_64/releases.json`.

Daily builds get less testing than releases, so expect some rough edges.

## License

[![License: GPLv3](https://img.shields.io/badge/license-GPLv3-bd0000.svg)](https://www.gnu.org/licenses/gpl-3.0)

```text
Copyright (C) 2026 Daniel Vartanian

positron-ide-daily-bin is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by the Free
Software Foundation, either version 3 of the License, or (at your option) any
later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with
this program. If not, see <https://www.gnu.org/licenses/>.
```

plainlibs ![language](https://img.shields.io/badge/language-C99-blue) ![license](https://img.shields.io/badge/License-CC0%20(public%20domain)-blue)
=========
Lightweight single-file utilities for C99.

## Key Features
- Portable across Unix & Windows (including MSVC)
- Zero dependencies (besides C stdlib)
- Extremely lightweight

## Included Libraries
- argparse (header only) ([docs](./docs/argparse.md))
   - A lightweight argument parsing library.

## Structure
Most of these libraries are header only, although some require an additional source file (`.c`).

Sometimes this additional source filesis nessicary to either:
1. reduce binary size (and avoid duplicating large functions)
2. reduce compile times

After adding this to your include path, using a libary should then be as simple as writing `#include "plain/argparse.h"` (or whatever library you want) inside your source files (See below).

See below for more detailed instructoions on using this.

## Projects that use these libraries
| Name | Description | Used libraries | Build style |
|-----------------------------------------------------------------|-----------------------------|----------------------|--------|
| [Techcable/wrap-shell](https://github.com/Techcable/wrap-shell) | A wrapper for [xonsh](https://xon.sh/) shell with automatic fallback to zsh | argparse | Meson |

Consider looking at my projects for examples of good usage :)

## Using & Building
None of these utilities should require a seperate build step.

The recommended way to include this project is with a git submodule, however you can also copy source files directly.

Most only require a single header file, although some require an additional source file.

If the utility you're using requires a source file (`.c`) in addition to a header file, you can choose to either:

1. Make a symbolic link in your project, pointing to the necessary source file
   - Symbolic links are recommended over direct copies, since they will automatically updgrade with the sub-repo.
2. build a static lib containing all the sources, and rely on the linker to remove unsued sections.
   - Almost every linker does this by default (even in debug mode).
   - Plus even without this the optimization, the whole library is < 32kb ;)

Option (2) is extremely easy to do if you use meson, otherwise you probably want to stick with option 1.

### Simple usage
Add `<path to repo>/include` to your project.

From that point any header-only libraries can be used directly.

If you need to include a `.c` file, consider the options listed above.

### Copying directly
You may copy and paste the needed headers and sources into your library.

Except where otherwise noted, each utility in this library should be independent of each other.

Since the license is CC0, you don't need to worry about any attribution when copying/pasting.

However, consider using a system link pointing to a git submodule, if you want to get the benefit of simpler updates.

### Meson
This project can be used as a meson subproject. You would git clone and put it in the subprojects directory.

Since this project has a meson build file, it can be quite easily used as a dependency.

By defualt, the meson dependency only includes headers (and doesn't compile any sources).

You can disable this by setting the `stati`

See [Techcable/wrap-shell](https://github.com/Techcable/wrap-shell) for a simple example of how to use this with a meson project.

## Portablity
Except where otherwise noted, all of these utilities should be able to be compiled with a conformant C99 compiler.

They should support both Windows (MSVC) and Unix-like systems.

## License
![CC0 License](https://licensebuttons.net/p/zero/1.0/88x31.png)

Everything in this repository is dual-licensed under the [Creative Commons Zero v1.0](./LICENSE-CC0) and the [MIT LICENSE][./LICENSE-MIT].  You may use either at your option.

Using CC0 makes this effectively public domain. In particular, this means you do not need to provide any sort of license notice if you copy/paste these libraries directory into your own code. This is in contrast to the standard MIT license.

See [LICENSE.md](./LICENSE.md) for more details.


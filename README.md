# Frozen repository

This repository contains the `opam-lock` plugin, which is deprecated,since the
feature has been integrated in opam.

See [this opam PR](https://github.com/ocaml/opam/issues/3734) for details.

No new pull requests will be accepted; please see the [opam](https://github.com/ocaml/opam) tracker for any issues or feature requests.

# opam-lock: restrict opam file to describe a precise build environment

This small opam plugin can rewrite opam package definition files to emulate the
behaviour of so-called "lock files" present in many package managers.

It reads opam files, extracts the precise set of their dependencies that is
currently installed, as well as pins and non-installed optional dependencies,
and writes back a `<name>.opam.locked` file that enforces this set and has the
corresponding `pin-depends:`.

You can then use `opam install <name>.opam.locked` to get the package installed
with the precise dependencies, including transitive dependencies, that it had in
the original system.

Option `--direct-only` can be used to only lock direct dependency versions
rather than the whole tree.

Note that the locked opam file adds _conflicts_ to uninstalled optional
dependencies, but not recursively: it therefore guarantees the same dependencies
get installed, up to potentially some of their optional dependencies.

This project is currently in early beta.

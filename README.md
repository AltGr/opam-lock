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

This project is currently in early beta.

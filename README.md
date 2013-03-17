## ocamlbrew - A tool for managing OCaml installations in $HOME

ocamlbrew aims to be a simple tool for getting up and running with various
versions of [OCaml][].  The concept, along with some basic code, is borrowed
from [perlbrew][].

### Requirements

* bash
* OCaml's build requirements
* Any non-OCaml dependencies required by other software selected for
  installation.
  * To fetch all depedencies coming from a fresh Ubuntu 12.04 installation:
    * `sudo apt-get install curl m4`
      * `curl` is for fetching files
      * `m4` is required by [findlib][]

### Usage:

#### Getting started

Using ocamlbrew is very easy.  In its most basic form, ocamlbrew can run in a
completely automated fashion:

    curl -kL https://raw.github.com/hcarty/ocamlbrew/master/ocamlbrew-install | bash

See `RECIPES.md` for more installation options.

ocamlbrew will print the name of the log file where compilation output is being
directed.  This can be watched to track build progress and/or used for
troubleshooting in case one of the build steps fails.

#### Configurable environment variables

ocamlbrew can be configured with several environment variables.

* `$OCAMLBREW_BASE`
  The most important is `$OCAMLBREW_BASE` which defines the directory under
  which all software built and installed by ocamlbrew will reside.
  `$OCAMLBREW_BASE` defaults to `$HOME/ocamlbrew`.
* `$OCAMLBREW_LOGFILE`
  Output from the build process will be directed to this file.  This defaults
  to a randomly named file under `$TMPDIR` if defined or `/tmp` otherwise.
* `$OCAMLBREW_FLAGS`
  This is only for installations which do not involve downloading ocamlbrew
  locally.  This variable specifies which flags to pass to `ocamlbrew`.
  `$OCAMLBREW_FLAGS` defaults to `-a`.

#### Available command line flags
    -h              Display this message
    -b [path]       Use [path] as $OCAMLBREW_BASE
    -v [version]    Install the given version of OCaml (i.e. 4.00.1)
    -c "[flags]"    Flags to pass to OCaml's configure
    -p [patch]      Patch to apply to OCaml
    -a              Install everything with no prompts
    -o              Install OCaml, no prompts
    -f              Install OCaml and findlib, no prompts
    -r              Install OCaml and opam, no prompts
    -x              Install OCaml, opam, oasis (via opam), no prompts
    -s [path]       Install OCaml from Subversion [path]
    -t              Install OCaml from Subversion trunk
    -n [name]       Install under $OCAMLBREW_BASE/[name]

The build and installation will occur under `$OCAMLBREW_BASE`  
Subversion paths should be relative to `http://caml.inria.fr/svn/ocaml/`

#### After installation

ocamlbrew will provide instructions on how to setup the newly
installed OCaml environment once all build and installation steps are
complete.  After following those instructions, depending on the
options selected at ocamlbrew startup, the [OCaml][] toolchain,
[ocamlfind][findlib], [opam][], [oasis][], [utop][], and
[ocamlscript][] will be available from the shell environment.

### License

ocamlbrew is distributed under the MIT license.  See LICENSE for details.

[OCaml]: http://caml.inria.fr/ocaml/release.en.html
[findlib]: http://projects.camlcity.org/projects/findlib.html
[oasis]: http://oasis.forge.ocamlcore.org/
[opam]: http://opam.ocamlpro.com/
[Batteries]: http://batteries.forge.ocamlcore.org/
[React]: http://erratique.ch/software/react
[Lwt]: http://ocsigen.org/lwt/
[utop]: http://forge.ocamlcore.org/projects/utop/
[ocamlscript]: http://martin.jambon.free.fr/ocamlscript.html
[perlbrew]: http://search.cpan.org/~gugod/App-perlbrew/bin/perlbrew

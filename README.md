## ocamlbrew - A tool for managing OCaml installations in $HOME

ocamlbrew aims to be a simple tool for getting up and running with various
versions of [OCaml][].  The concept, along with some basic code, is borrowed
from [perlbrew][].

### Requirements

* bash
* OCaml's build requirements
* Any non-OCaml dependencies required by other software selected for
  installation.
  * For example, [oasis][] depends indirectly on [PCRE][] and [Lwt][] depends
    on [libev][].  These dependencies can be filled on Debian and Ubuntu
    with the `libev-dev` and `libpcre3-dev` packages.

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
    -c "[flags]"    Flags to pass to OCaml's configure
    -a              Install everything with no prompts
    -o              Install OCaml only, no prompts
    -f              Install OCaml and findlib only, no prompts
    -s [path]       Install OCaml from Subversion [path]
    -t              Install OCaml from Subversion trunk
    -n [name]       Install under $OCAMLBREW_BASE/[name]

The build and installation will occur under `$OCAMLBREW_BASE`  
Subversion path should be relative to `http://caml.inria.fr/svn/ocaml/`

#### After installation

ocamlbrew will provide instructions on how to setup the newly installed OCaml
environment once all build and installation steps are complete.  After
following those instructions, depending on the options selected at ocamlbrew
startup, the [OCaml][] toolchain, [ocamlfind][findlib], [odb.ml][odb],
[oasis][], [utop][], and [ocamlscript][] will be available from the shell
environment.

### License

ocamlbrew is distributed under the MIT license.  See LICENSE for details.

[OCaml]: http://caml.inria.fr/ocaml/release.en.html
[findlib]: http://projects.camlcity.org/projects/findlib.html
[odb]: https://github.com/thelema/odb
[oasis]: http://oasis.forge.ocamlcore.org/
[oasis-db]: http://oasis.ocamlcore.org/dev/home
[Batteries]: http://batteries.forge.ocamlcore.org/
[React]: http://erratique.ch/software/react
[Lwt]: http://ocsigen.org/lwt/
[utop]: http://forge.ocamlcore.org/projects/utop/
[ocamlscript]: http://martin.jambon.free.fr/ocamlscript.html
[perlbrew]: http://search.cpan.org/~gugod/App-perlbrew/bin/perlbrew
[PCRE]: http://www.pcre.org/
[libev]: http://software.schmorp.de/pkg/libev.html

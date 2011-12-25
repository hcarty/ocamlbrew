## ocamlbrew - A tool for managing OCaml installations in $HOME

ocamlbrew aims to be a simple tool for getting up and running with various
versions of [OCaml][].  The concept, along with some basic code, is borrowed
from [perlbrew][].  This script should be considered to be in an early alpha
state.

### Requirements

* Linux
* bash
* OCaml's build requirements
* Any non-OCaml dependencies required by other software selected for
  installation (for example, [oasis][] depends indirectly on [PCRE][]).

### Usage:

#### Getting started

Using ocamlbrew is very easy.  It can be run in a completely automated fashion:

    # Optionally setting $OCAMLBREW_BASE and/or $OCAMLBREW_LOGFILE first
    curl -kL https://raw.github.com/hcarty/ocamlbrew/master/ocamlbrew-install | bash

Or it can be run by hand:

    # Download...
    cd /tmp
    curl -O https://raw.github.com/hcarty/ocamlbrew/master/ocamlbrew
    # ... and run, again, optionally configuring the environment first
    ./ocamlbrew

You will be provided with several prompts asking which software to install.
[OCaml][] is always installed, with [findlib][], [oasis][], [Batteries][] and
[utop][] optionally included as well.  If they are requested, [oasis][],
[Batteries][], and [utop][] are all installed using [oasis-db][] via [odb][].

ocamlbrew will print the name of the log file where compilation output is being
directed.  This can be used for troubleshooting in case one of the build steps
fails.

#### Configuration options

ocamlbrew can be configured with several environment variables.

* `$OCAMLBREW_BASE`  
  The most important is `$OCAMLBREW_BASE` which defines the directory under which all
  software built and installed by ocamlbrew will reside.  `$OCAMLBREW_BASE`
  defaults to `$HOME/ocamlbrew`.
* `$OCAMLBREW_LOGFILE`  
  Output from the build process will be directed to this file.  This defaults
  to a randomly named file under `/tmp`.

#### After installation

ocamlbrew will provide instructions on how to setup the newly installed OCaml
environment once all build and installation steps are complete.  After following
those instructions, depending on the options selected at ocamlbrew startup, the
[OCaml][] toolchain, [ocamlfind][findlib], [odb.ml][odb], [oasis][], and
[utop][] will be available from the shell environment.

[OCaml]: http://caml.inria.fr/ocaml/release.en.html
[findlib]: http://projects.camlcity.org/projects/findlib.html
[odb]: https://github.com/thelema/odb
[oasis]: http://oasis.forge.ocamlcore.org/
[oasis-db]: http://oasis.ocamlcore.org/dev/home
[Batteries]: http://batteries.forge.ocamlcore.org/
[React]: http://erratique.ch/software/react
[Lwt]: http://ocsigen.org/lwt/
[utop]: http://forge.ocamlcore.org/projects/utop/
[perlbrew]: http://search.cpan.org/~gugod/App-perlbrew/bin/perlbrew

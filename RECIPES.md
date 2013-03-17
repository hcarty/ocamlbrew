## Recipes for your own OCaml brews

Most of these recipes do not require any manual downloads.  Each curl command
has an associated comment which shows how you would perform the equivalent task
with a local copy of ocamlbrew.

Unless otherwise noted, each of the recipes below will install under
`$HOME/ocamlbrew`.

### Latest stable OCaml with all available goodies

    # Equivalent to: ./ocamlbrew -a
    # This is the default when using ocamlbrew-install, so it's not
    # necessary to specify $OCAMLBREW_FLAGS.
    curl -kL https://raw.github.com/hcarty/ocamlbrew/master/ocamlbrew-install | bash

### Latest OCaml trunk, findlib (directly from source)

    # Equivalent to: ./ocamlbrew -t -f
    # Specify that we want to pull from Subversion trunk and we only want
    # OCaml and findlib
    curl -kL https://raw.github.com/hcarty/ocamlbrew/master/ocamlbrew-install | env OCAMLBREW_FLAGS="-t -f" bash

### OCaml 3.12.1 release version, no other tools

    # Equivalent to: ./ocamlbrew -s release/3.12.1 -o
    # Specify an explicit Subversion path to pull from and we want OCaml only
    curl -kL https://raw.github.com/hcarty/ocamlbrew/master/ocamlbrew-install | env OCAMLBREW_FLAGS="-s release/3.12.1 -o" bash

### Install to a custom brew root

    # Build and install under /opt/ocamlbrew
    # Equivalent to: ./ocamlbrew -a
    curl -kL https://raw.github.com/hcarty/ocamlbrew/master/ocamlbrew-install | env OCAMLBREW_BASE="/opt/ocamlbrew" bash

### Install OCaml trunk and findlib to a custom directory

    # Build and install under /opt/ocamlbrew/
    # Equivalent to: ./ocamlbrew -t -f -b /opt/ocamlbrew -n trunk
    curl -kL https://raw.github.com/hcarty/ocamlbrew/master/ocamlbrew-install | env OCAMLBREW_FLAGS="-t -f -b /opt/ocamlbrew -n trunk" bash

### Download ocamlbrew and run it locally

This method will prompt you before the brewing begins, asking if you want to
install each available package.

    # Download...
    cd /tmp
    curl -O https://raw.github.com/hcarty/ocamlbrew/master/ocamlbrew
    # ... and run, optionally configuring the environment first
    bash ocamlbrew

You will be provided with several prompts asking which software to
install.  [OCaml][] is always installed, with [findlib][], [oasis][],
[opam][], [Batteries][], [utop][], and [ocamlscript][] optionally
included as well.  If they are requested, [oasis][], [Batteries][],
[utop][], and [ocamlscript][] are all installed using [opam][].

[OCaml]: http://caml.inria.fr/ocaml/release.en.html
[findlib]: http://projects.camlcity.org/projects/findlib.html
[oasis]: http://oasis.forge.ocamlcore.org/
[opam]: http://opam.ocamlpro.com/
[Batteries]: http://batteries.forge.ocamlcore.org/
[utop]: http://forge.ocamlcore.org/projects/utop/
[ocamlscript]: http://martin.jambon.free.fr/ocamlscript.html

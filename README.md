# ![Logo](https://raw.githubusercontent.com/clarus/icons/master/shield-48.png) CUnit
Unit testing for Coq.

## Install
### With OPAM
Add the Coq repository (you may prefer the [unstable](https://github.com/coq/repo-unstable) repository to get the latest version):

    opam repo add coq-stable https://github.com/coq/repo-stable.git

and run:

    opam install coq:cunit

### From the sources
Run:

    ./configure.sh
    make
    make install

## Use
Add:

    Require Import CUnit.All.

at the beginning of your source files.

## Reference
### List
* `map_pair {A B C : Type} (f : A -> B -> C) (l : list (A * B)) : list C`
* `map_triple {A B C D : Type} (f : A -> B -> C -> D) (l : list (A * B * C)) : list D`
* `map_quad {A B C D E : Type} (f : A -> B -> C -> D -> E) (l : list (A * B * C * D)) : list E`

# ![Logo](https://raw.githubusercontent.com/clarus/icons/master/shield-48.png) CUnit
Unit testing in Coq, at compile time.

    Require Import Coq.Lists.List.
    Require Import CUnit.All.

    Import ListNotations.

    Definition test_plus : List.map_pair plus
      [(0, 0); (0, 3); (4, 0); (4, 3)] =
      [0; 3; 4; 7] :=
      eq_refl.

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

The idea is to consider tests as specifications, and to express them as types. For example:

    Definition test_pred : pred 12 = 11 := eq_refl.

will force the type checker of Coq to evaluate `pred 12` and make sure its value is `11`. Do run many tests we usually take a list:

    Definition test_pred : List.map pred [0; 1; 2; 12] = [0; 0; 1; 11] := eq_refl.

For functions with multiple arguments, CUnit provides generalized versions of `List.map`, like `List.map_pair`.

## Reference
### List
* `map_pair {A B C : Type} (f : A -> B -> C) (l : list (A * B)) : list C`
* `map_triple {A B C D : Type} (f : A -> B -> C -> D) (l : list (A * B * C)) : list D`
* `map_quad {A B C D E : Type} (f : A -> B -> C -> D -> E) (l : list (A * B * C * D)) : list E`

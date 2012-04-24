Inductive types in Homotopy Type Theory: Coq proofs
===================================================

This subdirectory contains Coq proofs formalizing the development of 
inductive types in the setting of Homotopy Type Theory. It relies on
Vladimir Voevodsky's Foundations repository.


The files in this subdirectory were created and are maintained by S.
Awodey, N. Gambino, and K. Sojakova (awodey@cmu.edu,
ngambino@math.unipa.it, kristinas@cmu.edu).

The Coq version used is 8.3pl3 (although note that you will need
Vladimir Voevodsky's patches to compile all of Foundations).

The main results formalized in the repository are the proofs of the following
statements:

  * weak 2-types arise as h-initial algebras
  * weak W-types arise as h-initial algebras
  * weak natural numbers reduce to weak W-types
  * second number class reduces to weak W-types
  
## How to compile

Starting in the `Foundations` directory:

    cd Generalities
    coqc uuu.v
    coqc uu0.v
    cd ../IT
    make

That should be it. Note that you need Coq 8.3pl3 or newer.


## The organization of files

1. We rely only on two files from Foundations, namely:

   * `Generalities/uuu.v`
   * `Generalities/uu0.v`

   The above files introduce the identity types, Sigma types, and the
   (simple) function extensionality axiom. Dependent function
   extensionality is derived as a consequence and a homotopy
   equivalence is established between the types of pointwise vs global
   function equalities.

   If you do not have a patcheed version of Coq, you can just compile
   `uuu.v` and `uu0.v` by hand with Coq 8.3pl3 or later:

       coqc uuu.v
       coqc uu0.v
   
2. The file `identity.v` in the folder `identity` introduces various
   lemmas concerning the basic homotopical properties of propositional
   equalities and the interaction of identity types with other type
   constructors.
   
3. The folder `inductive_types` contains the definitions of various
   weak inductive types, namely the types `Zero`, `One`, `Two`,
   `Three` with `0`, `1`, `2`,`3` constructors respectively; the type
   `Sum` of weak sums; weak natural numbers and lists; and weak
   W-types. The types are presented in the standard form by giving the
   formation, introduction, elimination, and computation rules (here
   called beta). The corresponding eta rules are derived.

4. The folder `two_is_hinitial` contains the proof that the type `Two`
   arises as an h-initial algebra. The proof is structured as follows:

    1.  First the analogous simple rules for Two are formulated; the corresponding
        eta rules are no longer derivable and are stated as axioms. This is done
        in the file `two_simp.v`.

    2.  We show that the dependent rules for Two imply the simple ones and
        vice versa. This is done in the files `simp_implies_dep.v` and
        `dep_implies_simp.v`.

    3.  The notions of algebra homomorphisms, algebra 2-cells, and homotopy-initial
        algebras are formulated for Two. It is furthermore shown that two algebra
        homomorphisms are propositionally equal if and only if there exists an
        algebra 2-cell between them. This is done in the file `two_algebras.v`.

    4.  We show that the simple rules for Two are equivalent to the assertion
        that there exists a homotopy-initial 2-algebra. This is done in the files
        `simp_implies_hinitial.v` and `hinitial_implies_simp.v`.
			  
5. The folder `w_is_hinitial` contains the proof that weak W-types arise as h-initial
   algebras for polynomial functors. The proof is structured as follows:

   1. First we introduce the notion of polynomial functors and prove a number
      of useful lemmas. This is done in the file `polynomial_functors.v`.

   2. We show the main result, i.e. that the dependent rules for W are
      equivalent to the assertion that there exists a homotopy-initial algebra
      for the associated polynomial functor. This is done in the files
      `w_implies_hinitial.v` and `hinitial_implies_w.v`.
			  
6. The file `nat_as_w_type.v` in the folder `nat_as_w_type` formalizes the proof that
   weak natural numbers are encodable as weak W-types in the presence of the types
   Zero, One, and (a type-level version of) Two.   
   
7. The file `o2_as_w_type.v` in the folder `nat_as_w_type` formalizes the proof that the
   second number class is encodable as a weak W-type in the presence of the types
   Zero, One, Two, and (a type-level version of) Three.

## How to compile

The order of compilation is as follows (although after you compiled
`uuu.v` and `uu0.v` you can just run `make` in the IT subdirectory):

1. in the top `Foundations` directory:
   * `Generalities/uuu.v`
   * `Generalities/uu0.v`
2. `identity/identity.v`
3. `inductive_types/*.v`
4. `two_is_hinitial`: 
    * `two_simp.v`, `two_algebras.v`
    * `dep_implies_simp.v`, `simp_implies_dep.v`, `simp_implies_hinitial.v`, `hinitial_implies_simp.v`
5. `w_is_hinitial`:
   * `polynomial_functors.v`
   * `hinitial_implies_w.v`, `w_implies_hinitial.v`
6) nat_as_w_type:
   * `nat_as_w_type.v`
   * `o2_as_w_type.v`

# hyperelliptic

This directory contains two [Magma](http://magma.maths.usyd.edu.au/magma/) program files that can be used to enumerate
hyperelliptic curves of genus 2 or 3 over finite fields of odd characteristic. The algorithms used are based on the
one described in the paper [&ldquo;Enumerating hyperelliptic curves over finite fields in quasilinear time,&rdquo;](https://doi.org/10.48550/arXiv.2401.15255)
by Everett W. Howe.

The two program files are

    Hyperelliptic2.magma
    Hyperelliptic3.magma

Each file has extensive comments, which the user should consult. Briefly: If you run Magma and load Hyperelliptic2.magma, you can enter

    L := sixpoints(GF(q));

for any odd prime power *q*, and *L* will then contain a list of triples <*f*,*n*,*S*>, where *f* is a polynomial of degree 5 and 6 over __F__<sub>*q*</sub>, 
where *n* is an integer, and where *S* is a list of elements of PGL<sub>2</sub>(__F__<sub>*q*</sub>). Every orbit of PGL<sub>2</sub>(__F__<sub>*q*</sub>) acting on
the monic separable polynomials of degree 5 and 6 over __F__<sub>*q*</sub> will have exactly one representative *f* on the list. The set *S* associated to *f* consists of
the stabilizer of *f* under the PGL<sub>2</sub>(__F__<sub>*q*</sub>) action, and the associated *n* is the cardinality of *S*.

If you then enter

    M := curves(L);

the variable *M* will contain a similar list, now with the property that the list of curves *y*<sup>2</sup> = *f* will contain every hyperelliptic curve of genus 2 
over __F__<sub>*q*</sub>  exactly once. The corrresponding set *S* will give the __F__<sub>*q*</sub>-rational automorphism group for the curve, and the corresponding *n* will be the order of this group.

Likewise, if you run Magma and load both Hyperelliptic2.magma *and* Hyperelliptic3.magma, you can enter

    L := eightpoints(GF(q));
    M := curves(L);

to get similar lists of polynomials of degree 7 and 8 and of hyperelliptic curves of genus 3. Both program files have to be loaded, because  Hyperelliptic3.magma uses
functions defined in Hyperelliptic2.magma.

# hyperelliptic

This directory contains two [Magma](http://magma.maths.usyd.edu.au/magma/) program files that can be used to enumerate
hyperelliptic curves of genus 2 or 3 over finite fields of odd characteristic. The algorithms used are based on the
one described in the paper [&ldquo;Enumerating hyperelliptic curves over finite fields in quasilinear time,&rdquo;](https://doi.org/10.48550/arXiv.2401.15255)
by Everett W. Howe.

The two program files are

    Hyperelliptic2.magma
    Hyperelliptic3.magma

Each file has extensive comments, which the user should consult. Briefly: If you run Magma and load Hyperelliptic2.magma, you can enter

    L := hyperelliptic2(GF(q));

for any odd prime power *q*, and *L* will then contain a list of triples <*f*,*n*,*S*>, where *f* is a polynomial of degree 5 and 6 over __F__<sub>*q*</sub>, 
where *n* is an integer, and where *S* is a list of elements of PGL<sub>2</sub>(__F__<sub>*q*</sub>). The equation *y<sup>2</sup> = f* defines a hyperelliptic curve of genus 2, and every genus-2 hyperelliptic curve over __F__<sub>*q*</sub> will have exactly one representative in the list. 
The set *S* associated to *f* consists of elements of PGL<sub>2</sub>(__F__<sub>*q*</sub>) that define automorphisms of the curve, and every automorphism
arises from an element of *S*. The value *n* is twice the size of *S*, which equals the size of the automorphism group of the curve.

Likewise, if you run Magma and load both Hyperelliptic2.magma *and* Hyperelliptic3.magma, you can enter

    L := hyperelliptic3(GF(q));

to get a similar list of hyperelliptic curves of genus 3. Both program files have to be loaded, because  Hyperelliptic3.magma uses
functions defined in Hyperelliptic2.magma.

There are many flags and optional variables that are explained in the comments at the beginning of the files. The most important thing to know is that you can prevent the functions from returning values, and instead have them print the values they calculate to standard out or to a file. When this is done, the memory requirements of the program are *O*(*q*) for Hyperelliptic2.magma and *O*(*q*<sup>2</sup>) for Hyperelliptic3.magma. Both programs run in time quasilinear in the size of their (printed or returned) output.

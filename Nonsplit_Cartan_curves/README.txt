The code in files in this directory is based on the paper:
> "Modular forms invariant under non-split Cartan subgroups", Mercuri Pietro, Schoof René, Mathematics of Computation, Vol. 89, no. 324, 2020, pp. 1969–1991, MR4081925, DOI 10.1090/mcom/3503; free online version at https://arxiv.org/pdf/1805.06873.pdf.

In the following is explained the structure and the main output of the file "Nonsplit_Cartan.txt".


/////////////////////////////////////////////////////////////////////////////////////////


The first part is just a setup for parameters and general structures used.


/////////////////////////////////////////////////////////////////////////////////////////


The second part computes the irreducible representation associated to a cusp form of weight 2 associated to Gamma0(p^2).

For the cuspidal case, the check is numerical. If the precision is not sufficient to detect the right character of cuspidal representations, must be raised the parameter "repprec".

The elements of "representations" are different depending on whether the irreducible representation is cuspidal or not.


Cuspidal case:

<#cuspform,#conjugate,type,gen,exp>

where:
1) #cuspform is the number of the cusp form with order given by Newforms(CuspidalSubspace(ModularForms(Gamma0(p^2),2)));
2) #conjugate is the number of Galois conjugate with order given by Newforms(CuspidalSubspace(ModularForms(Gamma0(p^2),2)))[#cuspform];
3) type is the string "Cuspidal";
4) gen is the generator describing the character theta parametrizing the representation;
5) exp is the logarithm of gen with base a fixed generator u of GF(p,2).


Non-cuspidal case:

<#cuspform,#conjugate,type,char,#embedding,#twistedform,#twistedconjugate>

where:
1) #cuspform is the number of the cusp form with order given by Newforms(CuspidalSubspace(ModularForms(Gamma0(p^2),2)));
2) #conjugate is the number of Galois conjugate with order given by Newforms(CuspidalSubspace(ModularForms(Gamma0(p^2),2)))[#cuspform];
3) type is one of the strings "Steinberg", "Twisted Steinberg", "Principal Series";
4) char is the character mu parametrising the representation;
5) #embedding is the embedding in the complex field of the number field over which is defined mu;
6) #twistedform is the number of the cusp form that twisted by mu gives #cuspform, the order is the one given by Newforms(CuspidalSubspace(ModularForms(Gamma1(p),2)));
7) #twistedconjugate is the number of Galois conjugate with order given by Newforms(CuspidalSubspace(ModularForms(Gamma1(p),2)))[#twistedform];


/////////////////////////////////////////////////////////////////////////////////////////


The third part computes the relevant number fields containing characters' images and Fourier coefficients of the cusp forms involved.


/////////////////////////////////////////////////////////////////////////////////////////


The fourth part computes the q-expansions of the (normalizer of a) non-split Cartan invariant cusp forms.

The sequence fns contains the q-expansions up to the order given in coefprec.


/////////////////////////////////////////////////////////////////////////////////////////


The fifth part makes some linear transformations of the basis of cusp forms: eliminates linear dependenecies modulo every prime l (this avoids bad reduction of canonical model for most primes) and apply LLL (this reduces the size of the coefficients of the equations describing canonical model).

The sequence fnspretty contains the q-expansions of the prettified basis up to the order given in coefprec.

The matrix Mprettifying represents the linear transformation from the starting basis to the prettified one (multiplicating by left the g x coefprec matrix of the cusp forms, where g is the genus).


/////////////////////////////////////////////////////////////////////////////////////////


The sixth part computes equations for the canonical model of the associated modular curve using the canonical embedding. This works only if the genus g is at least 3 and:
- g=3 and the canonical model can be described as a plane quartic;
- g=4 and the canonical model can be described by 1 quadric and 1 cubic;
- g>4 and the canonical model can be described by (g-2)(g-3)/2 quadrics.

To further reduce coefficient's size one can use LLL on quadrics' coefficients.


/////////////////////////////////////////////////////////////////////////////////////////


Issues:

1) The computation of the representations is made by brute force trying all the oldforms and all the characters, this may be made faster with some insight.

2) The computation of the number fields involved is quite heavy, I think that it is a question of well coding with MAGMA, maybe it can be made faster.

3) I just tested Xns(11), Xns+(13), Xns(13), Xns+(17), Xns+(19); in other cases could emerge problems, in particular in the third part. If you find any problem you can write me: mercuri.ptr@gmail.com




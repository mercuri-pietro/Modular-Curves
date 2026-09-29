The code in files in this directory is based on the paper:
> "Automorphisms of general modular curves", Valerio Dose, Lido Guido, Mercuri Pietro, preprint.

The code in the file "find_modular_automorphisms.txt" computes the group G of modular automorphisms of the modular curve X_H for H a subgroup of GL_2(Z/nZ). More in detail, it finds a sequence of matrices representing all elements in G and gives a subgroup of the symmetric group on #G elements isomorphic to G.
More details are given inside the file.

The file "find_modular_automorphisms_examples.txt" contains some examples of use of the code contained in "find_modular_automorphisms.txt".

The file "MAut_results_up_to_level_39.txt" contains the results of the main function in "find_modular_automorphisms.txt" applied to the modular curves of level up to 39 and genus at least 2 considered in the paper. For each modular curve, the file records its LMFDB label, the order of its group of modular automorphisms, a Magma description of the abstract group, and matrices representing generators of modular automorphism group.

The file "results70.ods" contains the results, for the modular curves considered up to level 70, of the criterion developed in the paper for determining whether all automorphisms of a modular curve are modular.

# Design of candidate SARS-CoV-2 "cocktail" vaccines

This repo aims to design "cocktail" vaccines of several SARS-CoV-2 spikes that include both a current leading variant (XBB.1.16) and some designed sequences with possible "future" variants.
The design here was done by Jesse Bloom for a project with Drew Weissman.

The future variants are designed by picking mutations that:
 
 - are expected to cause a lot of antigenic escape using the [escape calculator](https://jbloomlab.github.io/SARS2-RBD-escape-calc/)
 - have relatively favorable affects on ACE2 affinity and RBD expression as measured using [deep mutational scanning](https://journals.plos.org/plospathogens/article?id=10.1371/journal.ppat.1010951)
 - are estimated to have favorable effects on viral fitness based on [analysis of natural sequences](https://www.biorxiv.org/content/10.1101/2023.01.30.526314v1)

The configuration for the design is in [config.yaml](config.yaml).
To make the designs, build the `conda` environment in [environment.yml](environment.yml), and then run the Jupyter notebook [design_vax.ipynb](design_vax.ipynb), which does the design.

The results designs are in the following files:

 - [vax_designs/parent-vax.fa](vax_designs/parent-vax.fa): the *parent* cocktail that just includes the XBB.1.16 sequence.

 - [vax_designs/cocktail-vax.fa](vax_designs/cocktail-vax.fa): the *cocktail* that contains XBB.1.16 parent and four designed mutants. If just one cocktail is tested, this is the recommended one.

 - [vax_designs/aggressive-cocktail-vax.fa](vax_designs/aggressive-cocktail-vax.fa): a more *aggressive cocktail* that contains XBB.1.16 and four designed mutants with a larger (more aggressive) number of mutations. If multiple cocktails are tested, this could be a useful comparator to *cocktail*.

 - [vax_designs/conservative-cocktail-vax.fa](vax_designs/conservative-cocktail-vax.fa): a more *conservative cocktail* that contains XBB.1.16 and four designed mutants with a smaller (more conservative) number of mutations compared to *cocktail*. If multiple cocktails are tested, this could be a useful comparator to *cocktail*.

The following points should be taken into consideration before starting any experiments:

 - The designed sequences in the aforementioned files are spikes that do **not** contain any stabilizing mutations. For actual vaccine constructs, the 2P or (preferably) 6P mutations should be added to stabilize the pre-fusion spike.
 - The spikes have not been validated for proper folding or expression, which should be done prior to beginning any expensive / time-consuming experiments.
 - It may be desirable to add an additional control which represents the existing standard for vaccine composition in order to have better metrics on how well the cocktail performs.


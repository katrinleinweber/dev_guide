--- 
title: "rOpenSci Packages: Development, Maintenance, and Peer Review"
author: "rOpenSci onboarding editorial team: Scott Chamberlain, Anna Krystalli, Lincoln Mullen, Karthik Ram, Noam Ross, Maëlle Salmon"
date: "2018-06-27"
site: bookdown::bookdown_site
documentclass: book
bibliography: [book.bib]
biblio-style: apalike
link-citations: yes
github-repo: ropenscilabs/dev_guide
url: 'http\://ropensci.github.io/dev_guide/'
description: "Extended version of the onboarding packaging guide."
---

# Preface {-}

This book has the ambition to become a guide for maintainers of rOpenSci packages, in particular volunteers who submit a package to onboarding. 

The [first section of the book](#building) presents our guidelines for building and testing your package. 

The [second section](#onboardingintro) is dedicated to onboarding: what it is, our policies, and specific guides for authors, editors and reviewers.

The [third and last section](#collaboration) features our best practice for nurturing your package once it has been onboarded: how to collaborate with other developers, how to document releases, how to promote your package and how to leverage GitHub as a development platform.

We hope that you'll find the guide useful and clear, and welcome your suggestions in the [issue tracker of the book](https://github.com/ropenscilabs/dev_guide/issues). Happy R packaging!

The rOpenSci editorial team.

_If you want to contribute to this book (suggestions, corrections) please refer to [its GitHub repository](https://github.com/ropensci/dev_guide) in particular [the contributing guidelines](https://github.com/ropensci/dev_guide#contributing). Thanks!_

_We are thankful for all authors, reviewers and guest editors for helping us improve the system and this guide over the years. Thanks also to the following persons who made direct edits to this guide here or in its former home at ropensci/onboarding or ropensci/packaging_guide: [Katrin Leinweber](https://github.com/katrinleinweber), [John Baumgartner](https://github.com/johnbaums), [François Michonneau](https://github.com/fmichonneau), [Christophe Dervieux](https://github.com/cderv), [Lorenzo Busetto](https://github.com/lbusett), [Ben Marwick](https://github.com/benmarwick), [Nicholas Horton](https://github.com/nicholasjhorton), [Chris Kennedy](https://github.com/ck37), [Mark Padgham](https://github.com/mpadge), [Jeroen Ooms](https://github.com/jeroen), [Sean Hughes](https://github.com/seaaan), [Jan Gorecki](https://github.com/jangorecki), [Joseph Stachelek](https://github.com/jsta), [Dean Attali](https://github.com/daattali), [Julia Gustavsen](https://github.com/jooolia), [Nicholas Tierney](https://github.com/njtierney), [Rich FitzJohn](https://github.com/richfitz), [Tiffany Timbers](https://github.com/ttimbers), [Hilmar Lapp](https://github.com/hlapp), [Miles McBain](https://github.com/milesmcbain), [Bryce Mecum](https://github.com/amoeba), [Jonathan Carroll](https://github.com/jonocarroll/), [Carl Boettiger](https://github.com/cboettig/). Please tell us if we forgot to acknowledge your contribution!_

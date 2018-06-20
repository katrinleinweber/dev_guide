#  (PART) Maintaining Packages {-}

# Collaboration Guide {#collaboration}

<div class="summaryblock">
<p>Having contributors will improve your package, and if you onboard some of them as package authors with <a href="https://help.github.com/articles/repository-permission-levels-for-an-organization/">write permissions to the repo</a>, your package will be more sustainably developed.</p>
<p>This chapter contains our guidance for collaboration, in a <a href="#friendlyfiles">section about making your repo contribution- and collaboration- friendly</a> by infrastructure (code of conduct, contribution guidelines, issue labels); and <a href="#workingcollaborators">a section about how to collaborate with new contributors</a>, in particular in the context of the rOpenSci organization.</p>
</div>

## Make your repo contribution- and collaboration- friendly {#friendlyfiles}

### Code of conduct

We require that you use a code of conduct such as the [Contributor Covenant](http://contributor-covenant.org/) in developing your package.  You can document your code of conduct in a `CODE_OF_CONDUCT.md` or `CONDUCT.md` file in the package root directory, and linking to this file from the `README.md` file.  `devtools::use_code_of_conduct()` will add the Contributor Covenant template to your package.

### Contributing guide

Please include contribution guidelines in the README or a CONTRIBUTING.md. These guidelines can indicate:

* How to open issues (e.g. do you want bug reports to use [`reprex`](https://github.com/tidyverse/reprex)?)

* How your package is built (`roxygen2`, `pkgdown` so that people know which files to edit to correct a typo for instance)

* The coding style (see [the very brief style guide in `osmdata` README](https://github.com/ropensci/osmdata#style-guide)).

* Whether potential contributors should open an issue proposing a substrantial change before opening a PR implementing it, to make sure you agree.

You can have a look at the [tidyverse contributing.md template](https://github.com/r-lib/usethis/blob/8483d1edbec15e36ba72bf1f4fb5ab5dad44acf7/.github/CONTRIBUTING.md) for inspiration. It can be added to a package (and then modified) by using `usethis::use_tidy_contributing()`. Also see [this contributing.md template by rOpenSci's Scott Chamberlain](https://github.com/ropensci/dotgithubfiles/blob/80ba808ed035069cbb073e04c697368072fafaad/CONTRIBUTING.md).

### Issue labelling

You can use labels such as "help wanted" and "good first issue" to help potential collaborators, including newbies, find your repo. [Cf GitHub article](https://help.github.com/articles/helping-new-contributors-find-your-project-with-labels/)

## Working with collaborators {#workingcollaborators}

### Onboarding collaborators

There's no general rOpenSci rule as to how you should onboard collaborators. You should increase their rights to the repo as you gain trust, and you should definitely ackonwledge contributions (see[this section](#attributions)).

You can ask a new collaborator to make PRs (see following section for assessing a PR locally, i.e. beyond CI checks) to dev/master and assess them before merging, and after a while let them push to master, although you might want to keep a system of PR reviews... even for yourself once you have team mates!

A possible model for onboarding collaborators is provided by Jim Hester in [his `lintr` repo](https://github.com/jimhester/lintr/issues/318). 

If your problem is _recruiting_ collaborators, you can post an open call like Jim Hester's [on Twitter](https://twitter.com/jimhester_/status/997109466674819074), [GitHub]((https://github.com/jimhester/lintr/issues/318)), and as an rOpenSci package author, you can ask for help in rOpenSci slack and ask rOpenSci team for ideas for recruiting new collaborators.

### Working with collaborators (including yourself)

You could implement the [gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)" philosophy as explained by Amanda Dobbyn in [this blog post](https://ropensci.org/blog/2018/04/20/monkeydo/).

To asses PR cf ["Explore and extend a pull request" in happygitwithr.com](http://happygitwithr.com/pr-extend.html)

### Be generous with attributions {#attributions}

If someone contributes to your repository consider adding them in DESCRIPTION, as contributor ("ctb") for small contributions, author ("aut") for bigger contributions. Also consider adding their name near the feature/bug fix line in [NEWS.md](#news) We recommend your being generous with such acknowledgements.

As a reminder from [our packaging guidelines](#building) if your package was reviewed and you feel that your reviewers have made a substantial contribution to the development of your package, you may list them in the `Authors@R` field with a Reviewer contributor type (`"rev"`), like so:

```
    person("Bea", "Hernández", role = "rev",
    comment = "Bea reviewed the package for ropensci, see <https://github.com/ropensci/onboarding/issues/116>"),
```
Only include reviewers after asking for their consent.  Note that 'rev' will raise a CRAN NOTE unless the package is built using R v3.5 (r-devel as of 2017-09-21). Please do not list editors as contributors. Your participation in and contribution to rOpenSci is thanks enough!

### Welcoming collaborators to rOpenSci

If you give someone write permissions to the repository, please contact one of [the editors](#associateditors) or [Stefanie Butland](github.com/stefaniebutland) so that this new contributor might

* get invited to ropensci GitHub organization (instead of being [outside collaborators](https://help.github.com/articles/repository-permission-levels-for-an-organization/#outside-collaborators))

* get invited to rOpenSci slack workspace.

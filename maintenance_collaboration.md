#  (PART) Maintaining Packages {-}

# Collaboration Guide {#collaboration}

<div class="summaryblock">
<p>Having contributors will improve your package, and if you onboard some of them as package authors with <a href="https://help.github.com/articles/repository-permission-levels-for-an-organization/">write permissions to the repo</a>, your package will be more sustainably developed.</p>
<p>This chapter contains our guidance for collaboration, in a <a href="#friendlyfiles">section about making your repo contribution- and collaboration- friendly</a> by infrastructure (code of conduct, contribution guidelines, issue labels); and in<a href="#workingcollaborators">a section about how to collaborate with new contributors</a>, in particular in the context of the rOpenSci organization.</p>
</div>

## Make your repo contribution- and collaboration- friendly {#friendlyfiles}

### Code of conduct

We require that you use a code of conduct such as the [Contributor Covenant](http://contributor-covenant.org/) in developing your package.  You can document your code of conduct in a `CODE_OF_CONDUCT.md` or `CONDUCT.md` file in the package root directory, and linking to this file from the `README.md` file.  `devtools::use_code_of_conduct()` will add the Contributor Covenant template to your package.

### Contributing guide

Please include contribution guidelines in the README or CONTRIBUTING.

### Issue labelling

You can use labels such as "help wanted" and "good first issue" to help potential collaborators, including newbies, find your repo. [Cf GitHub article](https://help.github.com/articles/helping-new-contributors-find-your-project-with-labels/)

## Working with collaborators {#workingcollaborators}

### Assessing a PR

Cf ["Explore and extend a pull request" in happygitwithr.com](http://happygitwithr.com/pr-extend.html)

### Be generous with attributions

If someone contributes to your repository consider adding them in DESCRIPTION, as contributor ("ctb") for small contributions, author ("aut") for bigger contributions. Also consider adding their name near the feature/bug fix line in [NEWS.md](#news) We recommend your being generous with such acknowledgements.

As a reminder from [our packaging guidelines](#building) if your package was reviewed and you feel that your reviewers have made a substantial contribution to the development of your package, you may list them in the `Authors@R` field with a Reviewer contributor type (`"rev"`), like so:

```
    person("Bea", "Hernández", role = "rev",
    comment = "Bea reviewed the package for ropensci, see <https://github.com/ropensci/onboarding/issues/116>"),
```
Only include reviewers after asking for their consent.  Note that 'rev' will raise a CRAN NOTE unless the package is built using R v3.5 (r-devel as of 2017-09-21). Please do not list editors as contributors. Your participation in and contribution to rOpenSci is thanks enough!

### Onboarding collaborators

If you give someone write permissions to the repository, please contact one of [the editors](#associateditors) or [Stefanie Butland](github.com/stefaniebutland) so that this new contributor might

* get invited to ropensci GitHub organization (instead of being [outside collaborators](https://help.github.com/articles/repository-permission-levels-for-an-organization/#outside-collaborators))

* get invited to rOpenSci slack workspace.
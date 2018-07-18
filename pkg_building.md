#  (PART) Building Your Package {-}

# Packaging Guide {#building}

<div class="summaryblock">
<p>rOpenSci accepts packages that meet our guidelines via a streamlined <a href="#whatisonboarding">onboarding process</a>. To ensure a consistent style across all of our tools we have written this chapter highlighting our guidelines for package development. Please also read and apply our <a href="#ci">chapter about continuous integration (CI)</a>. Further guidance for after onboarding is provided in the third section of this book starting with <a href="#collaboration">a chapter about collaboration</a>.</p>
<p>We strongly recommend that package developers read Hadley Wickham’s concise but thorough book on package development which is available for <a href="http://r-pkgs.had.co.nz/">free online</a> (and <a href="http://amzn.com/1491910593?tag=r-pkgs-20">print</a>). Our guide is partially redundant with other resources but highlights rOpenSci’s guidelines.</p>
<p>To read why submitting a package to rOpenSci is worth the effort to meet guidelines, have a look at <a href="#whysubmit">reasons to submit</a>.</p>
</div>

## Package name and metadata

### Naming your package

* We strongly recommend short, descriptive names in lower case. If your package deals with one or more commercial services, please make sure the name does not violate branding guidelines. You can check if your package name is available, informative and not offensive by using the [`available` package](https://github.com/ropenscilabs/available).

* A more unique package name might be easier to track (for you and us to assess package use) and search (for users to find it and to google their questions). Obviously a _too_ unique package name might make the package less discoverable (e.g. it might be an argument for naming your package [geojson](https://github.com/ropensci/geojson)).

* Find other interesting aspects of naming your package [in this blog post by Nick Tierney](http://www.njtierney.com/post/2018/06/20/naming-things/), and in case you change your mind, find out [how to rename your package in this other blog post of Nick's](http://www.njtierney.com/post/2017/10/27/change-pkg-name/).

### Creating metadata for your package

We recommend you to use the [`codemetar` package](https://github.com/ropensci/codemetar) for creating and updating a JSON [CodeMeta](https://codemeta.github.io/) metadata file for your package via `codemetar::write_codemeta()`. It will automatically include all useful information, including [GitHub rep keywords](#grooming). CodeMeta uses [Schema.org terms](https://schema.org/) so as it gains popularity the JSON metadata of your package might be used by third-party services, maybe even search engines. 

## Function/variable naming & general syntax

* We strongly recommend `snake_case` over all other styles unless you are porting over a package that is already in wide use.

* Avoid function name conflicts with base packages or other popular ones (e.g. `ggplot2`, `dplyr`, `magrittr`, `data.table`)

* Functions and arguments naming should be chosen to work together to form a common, logical programming API that is easy to read, and auto-complete. 

    * Consider an `object_verb()` naming scheme for functions in your package that take a common data type or interact with a common API. `object` refers to the data/API and `verb` the primary action.  This scheme helps avoid namespace conflicts with packages that may have similar verbs, and makes code readable and easy to auto-complete.  For instance, in **stringi**, functions starting with `stri_` manipulate strings (`stri_join()`, `stri_sort()`, and in **googlesheets** functions starting with `gs_` are calls to the Google Sheets API (`gs_auth()`, `gs_user()`, `gs_download()`).
    
    * Argument naming and order should be consistent across functions that use similar inputs.

    * For functions that manipulate an object/data and return an object/data of the same type, make the object/data the first argument of the function so as to enhance compatibility with the pipe operator (`%>%`)

* Package functions importing data should not import data to the global environment, but instead must return objects. Assignments to the global environment are to be avoided in general.

* For more information on how to style your code, name functions, and R scripts inside the `R/` folder, we recommend reading the [code chapter in Hadley's book](http://r-pkgs.had.co.nz/r.html). We recommend the [`styler` package](https://github.com/r-lib/styler) for automating part of the code styling.

## README

* All packages should have a README file, named `README.md`, in the root of the repository. The README should include, from top to bottom:

    * The package name
    * Badges for continuous integration and test coverage, the badge for rOpenSci peer-review once it has started (see below), a repostatus.org badge, and any other badges
    * Short description of goals of package, with descriptive links to all vignettes (rendered, i.e. readable, cf [the documentation website section](#website)) unless the package is small and there's only one vignette repeating the README.
    * Installation instructions
    * Any additional setup required (authentication tokens, etc)
    * Brief demonstration usage
    * If applicable, how the package compares to other similar packages and/or how it relates to other packages
    * Citation information


If you use another repo status badge such as a [lifecycle](https://www.tidyverse.org/lifecycle/) badge, please also add a [repostatus.org](http://www.repostatus.org/) badge. [Example of a repo README with two repo status badges](https://github.com/ropensci/ijtiff#ijtiff-).

* Once you have submitted a package and it has passed editor checks, add a peer-review badge via

```
[![](https://badges.ropensci.org/<issue_id>_status.svg)](https://github.com/ropensci/onboarding/issues/<issue_id>)
```

where issue_id is the number of the issue in the onboarding repository. For instance, the badge for [`rtimicropem`](https://github.com/ropensci/rtimicropem) review uses the number 126 since it's the [review issue number](https://github.com/ropensci/onboarding/issues/126). The badge will first indicated "under review" and then "peer-reviewed" once your package has been onboarded (issue labelled "approved" and closed), and will link to the review issue.

* If your README has many badges consider ordering them in an html table to make it easier for newcomers to gather information at a glance. See examples in [`drake repo`](https://github.com/ropensci/drake) and in [`qualtRics` repo](https://github.com/ropensci/qualtRics/). Possible sections are 
    * Development (CI statuses cf [CI chapter](#ci), Slack channel for discussion, repostatus)
    * Release/Published ([CRAN version and release date badges from METACRAN](https://www.r-pkg.org/services#badges), [CRAN checks API badge ](https://github.com/ropensci/cchecksapi#badges), Zenodo badge)
    * Stats/Usage (downloads e.g. [download badges from METACRAN](https://www.r-pkg.org/services#badges))
  The table should be more wide than it is long in order to mask the rest of the README.

* If your package connects to a data source or online service, or wraps other software, consider that your package README may be the first point of entry for users.  It should provide enough information for users to understand the nature of the data, service, or software, and provide links to other relevant data and documentation.  For instance,
a README should not merely read, "Provides access to GooberDB," but also include,
"..., an online repository of Goober sightings in South America.  More
information about GooberDB, and documentation of database structure and metadata
can be found at *link*".

* We recommend not creating `README.md` directly, but from a `README.Rmd` file (an R Markdown file) if you have any demonstration code. The advantage of the `.Rmd` file is you can combine text with code that can be easily updated whenever your package is updated.

* Extensive examples should be kept for a vignette. If you want to make the vignettes more accessible before installing the package, we suggest [creating a website for your package](#website)

* Consider using `usethis::use_readme_rmd()` to get a template for a `README.Rmd` file and to automatically set up a pre-commit hook to ensure that `README.md` is always newer than `README.Rmd`.

* _After_ a package is accepted but before transfer, the rOpenSci footer should be added to the bottom of the README file with the following markdown line:

```
[![ropensci_footer](http://ropensci.org/public_images/github_footer.png)](https://ropensci.org)
```

* Add a code of conduct and contribution guidelines, cf [this section of the book](#friendlyfiles).

* See the [`gistr` README](https://github.com/ropensci/gistr#gistr) for a good example README to follow for a small package, and [`bowerbird` README](https://github.com/ropensci/bowerbird) for a good example README for a larger package.

## Documentation

* All exported package functions should be fully documented with examples.

* All functions should document the type of object returned under the `@return` heading.

* We recommend using the `@family` tag in the documentation of functions to allow their grouping in the documentation of the installed package and potentially in the package's website, see [this section of Hadley Wickham's book](http://r-pkgs.had.co.nz/man.html) and [this section of the present chapter](#function-grouping) for more details.

* The package should contain top-level documentation for `?foobar`, (or `?foobar-package` if there is a naming conflict). Optionally, you can use	both `?foobar` and `?foobar-package` for the package level manual file, using `@aliases` roxygen tag. `usethis::use_package_doc()` adds the template for the top-level documentation.

* The package should contain at least one vignette providing a substantial coverage of package functions, illustrating realistic use cases and how functions are intended to interact. If the package is small, the vignette and the README can have the same content. 

* As is the case for a README, top-level documentation or vignettes may be the first point of entry for users. If your package connects to a data source or online service, or wraps other software, it should provide enough information for users to understand the nature of the data, service, or software, and provide links to other relevant data and documentation.  For instance, a the vignette intro or documentation should not merely read, "Provides access to GooberDB," but also include, "..., an online repository of Goober sightings in South America.  More information about GooberDB, and documentation of database structure and metadata can be found at *link*". Any vignette should outline prerequisite knowledge to be able to understand vignette upfront.

 The general vignette should present a series of examples progressing in complexity from basic to advanced usage.

* Functionality likely to be used by only more advanced users or developers might be better put in a separate vignette (i.e. programming/NSE with dplyr).

* The vignette(s) should include citations to software and papers where appropriate.

* We request all submissions to use `roxygen2` for documentation.  `roxygen2` is [an R package](http://cran.r-project.org/web/packages/roxygen2/index.html) that automatically compiles `.Rd` files to your `man` folder in your package from simple tags written above each function.

* More information on using roxygen2 [documentation](http://r-pkgs.had.co.nz/man.html) is available in the R packages book.

* One key advantage of using `roxygen2` is that your `NAMESPACE` will always be automatically generated and up to date.

* When using `roxygen2`, add `#' @noRd` to internal functions.

* Only use package startup messages when necessary (function masking for instance). Avoid package startup messages like "This is foobar 2.4-0" or citation guidance because they can be annoying to the user. Rely on documentation for such guidance. 

* You can choose to have a README section about use cases of your package (other packages, blog posts, etc), [example](https://github.com/ropensci/vcr#example-packages-using-vcr).

## Documentation website {#website}

We recommend creating a documentation website for your package using [`pkgdown`](https://github.com/hadley/pkgdown). [Here](http://enpiar.com/2017/11/21/getting-down-with-pkgdown/) is a good tutorial to get started with `pkgdown`, and unsurprisingly `pkgdown` has a [its own documentation website](http://pkgdown.r-lib.org/).

There are a few tips we'd like to underline here.

### Grouping functions in the reference {#function-grouping}

 When your package has many functions, use grouping in the reference, which you can do more or less automatically.
 
 If you use `roxygen` above version 6.0.1.9000 (as of July 2018, development version to be installed via `remotes::install_github("klutometis/roxygen")`) you should use the family tag in your functions documentation to indicate grouping. This will give you links between functions in the local documentation of the installed package ("See also" section) _and_ allow you to use the `pkgdown` `has_concept` function in the config file of your website. Non-rOpenSci example courtesy of [`optiRum`](https://github.com/lockedata/optiRum): [family tag](https://github.com/lockedata/optiRum/blob/master/R/APR.R#L17), [`pkgdown` config file](https://github.com/lockedata/optiRum/blob/master/_pkgdown.yml) and [resulting reference section](https://itsalocke.com/optirum/reference/).
 
 Less automatically, see the example of [`drake` website](https://ropensci.github.io/drake/reference/index.html) and [associated config file
](https://github.com/ropensci/drake/blob/master/_pkgdown.yml).

### Automatic deployment of the documentation website

You could use the [`tic` package](https://github.com/ropenscilabs/tic) for automatic deployment of the package's website, see [this example repo](https://github.com/krlmlr/tic.package). This would save you the hassle of running (and remembering to run) `pkgdown::build_site()` yourself every time the site needs to be updated. First refer to our [chapter on continuous integration](#ci) if you're not familiar with continuous integration/Travis.

### Branding of authors

You can make the names of (some) authors clickable by adding their URL, and you can even replace their names with a logo (think rOpenSci... or your organisation/company!). See [`pkgdown` documentation](http://pkgdown.r-lib.org/reference/build_home.html?q=authors#yaml-config-authors) and this example in the wild: [`pkgdown` config file](https://github.com/ropenscilabs/rodev/blob/f07fdead39762b332bc1df63e470cdc271d696e0/_pkgdown.yml#L1), [resulting website](https://ropenscilabs.github.io/rodev/).

## Authorship

The `DESCRIPTION` file of a package should list package authors and contributors to a package, using the `Authors@R` syntax to indicate their roles (author/creator/contributor etc.) if there is more than one author. See [this section of "Writing R Extensions"](https://cran.rstudio.com/doc/manuals/r-release/R-exts.html#The-DESCRIPTION-file) for details.  If you feel that your reviewers have made a substantial contribution to the development of your package, you may list them in the `Authors@R` field with a Reviewer contributor type (`"rev"`), like so:

```
    person("Bea", "Hernández", role = "rev",
    comment = "Bea reviewed the package for ropensci, see <https://github.com/ropensci/onboarding/issues/116>"),
```

Only include reviewers after asking for their consent. Read more in [this blog post "Thanking Your Reviewers: Gratitude through Semantic Metadata"](https://ropensci.org/blog/2018/03/16/thanking-reviewers-in-metadata/).  Note that 'rev' will raise a CRAN NOTE unless the package is built using R v3.5. As of June 2018 you need to use [`roxygen2` dev version](https://github.com/klutometis/roxygen#installation) for the list of authors in the package-level documentation to be compiled properly with the "rev" role (because this is a MARC role not included yet in [`royxgen2` CRAN version from February 2017](https://cran.r-project.org/web/packages/roxygen2/index.html)).

Please do not list editors as contributors. Your participation in and contribution to rOpenSci is thanks enough!

## Testing

* All packages should pass `R CMD check`/`devtools::check()` on all major platforms.

* All packages should have a test suite that covers major functionality of the package. The tests should also cover the behavior of the package in case of errors.

* We recommend using `testthat` for writing tests. Strive to write tests as you write each new function. This serves the obvious need to have proper testing for the package, but allows you to think about various ways in which a function can fail, and to _defensively_ code against those. [More information](http://r-pkgs.had.co.nz/tests.html).

* Once you've set up CI, use your package's code coverage report (cf [this section of our book](#coverage)) to identify untested lines, and to add further tests.

* `testthat` has a function `skip_on_cran()` that you can use to not run tests on CRAN. We recommend using this on all functions that are API calls since they are quite likely to fail on CRAN. These tests will still run on Travis.

* Even if you use [continuous integration](#ci), we recommend that you run tests locally prior to submitting your package, as some tests are often skipped (you may need to set `Sys.setenv(NOT_CRAN="true")` in order to ensure all tests are run). In addition, we recommend that prior to submitting your package, you use MangoTheCat's [**goodpractice**](https://github.com/MangoTheCat/goodpractice/) package to check your package for likely sources of errors, and run `spelling::spell_check_package()` to find spelling errors in documentation.

## Examples

* Include extensive examples in the documentation. In addition to demonstrating how to use the package, these can act as an easy way to test package functionality before there are proper tests. However, keep in mind we require tests in contributed packages. If you prefer not to clutter up code with extensive documentation, place further documentation/examples in files in a `man-roxygen` folder in the root of your package, and those will be combined into the manual file by the use of `@template <file name>`, for example. You can run examples with `devtools::run_examples()`.


## Package dependencies

* Use `Imports` instead of `Depends` for packages providing functions from other packages. Make sure to list packages used for testing (`testthat`), and documentation (`knitr`, `roxygen2`) in your `Suggests` section of package dependencies. If you use any package in the examples or tests of your package, make sure to list it in `Suggests`, if not already listed in `Imports`.

* For most cases where you must expose functions from dependencies to the user, you should import and re-export those individual functions rather than listing them in the `Depends` fields.  For instance, if functions in your package produce `raster` objects, you might re-export only printing and plotting functions from the **raster** package.

* If your package uses a system dependency, you should 
    * indicate it in DESCRIPTION
    * and check for it in the configure script and give a helpful error message if it cannot be found. [Example of a line indicating a system dependency in DESCRIPTION](https://github.com/ropensci/magick/blob/c116b2b8505f491db72a139b61cd543b7a2ce873/DESCRIPTION#L19), [example of a configure script that checks for the dependency](https://github.com/cran/webp/blob/master/configure). You can have a look at [more configure scripts](https://github.com/search?q=org%3Acran+anticonf&type=Code). Your configure script might need to do some hacky things since the config script is where you put all the hacks needed to make a particular library work. Use examples as a starting point but make sure you understand what you are doing because small bugs in the configure script can lead to bad things and can even get your package kicked from CRAN. Do not hesitate to [ask for help](https://discuss.ropensci.org/).
    * You should also check the dependency is listed by [`sysreqsdb`](https://github.com/r-hub/sysreqsdb#sysreqs) in order to ensure automatic tools building packages don't have a hard time with your package. See [`sysreqsdb` contributing guidelines](https://github.com/r-hub/sysreqsdb#contributing).

## Recommended scaffolding

* For http requests we strongly recommend using `httr` over `RCurl`.

* For parsing JSON, use `jsonlite` instead of `rjson` or `RJSONIO`.

* For parsing, creating, and manipulating XML, we strongly recommend `xml2` for most cases.

## Console messages

* Use `message()` and `warning()` to communicate with the user in your functions. Please do not use `print()` or `cat()` unless it's for a `print.*()` method, as these methods of printing messages are harder for the user to suppress.

##  Miscellaneous CRAN gotchas {#crangotchas}

This is a collection of CRAN gotchas that are worth avoiding at the outset.

* Make sure your package title is in Title Case.
* Do not put a period on the end of your title.
* Avoid starting the description with the package name or "This package ...".
* Make sure you include links to websites if you wrap a web API, scrape data from a site, etc. in the `Description` field of your `DESCRIPTION` file.
* Avoid long running tests and examples.  Consider `testthat::skip_on_cran` in tests to skip things that take a long time but still test them locally and on Travis.
* Include top-level files such as `paper.md`, `.travis.yml` in your `.Rbuildignore` file.

## Further guidance

* Hadley Wickham's _R Packages_ is an excellent, readable resource on package development which is available for [free online](http://r-pkgs.had.co.nz/) (and [print](http://amzn.com/1491910593?tag=r-pkgs-20)).

* [Writing R Extensions](https://cran.r-project.org/doc/manuals/r-release/R-exts.html) is the canonical, usually most up-to-date, reference for creating R packages.

* If you are submitting a package to rOpenSci via the [onboarding repo](https://github.com/ropensci/onboarding), you can direct further questions to the rOpenSci team in the issue tracker, or in our [discussion forum](https://discuss.ropensci.org/).

* Before submitting a package use the [**goodpractice**](https://github.com/MangoTheCat/goodpractice) package (`goodpractice::gp()`) as a guide to improve your package, since most exceptions to it will need to be justified. E.g. the use of `foo` might be generally bad and therefore flagged by `goodpractice` but you had a good reason to use it in your package.

# Continuous Integration Best Practices {#ci}

<div class="summaryblock">
<p>This chapter summarizes our guidelines about continuous integration after explaining what continuous integration.</p>
<p>Along with <a href="#building">last chapter</a>, it forms our guidelines for onboarding reviews.</p>
</div>

## Why use continuous integration?

All rOpenSci packages must use one form of continuous integration. This ensures that all commits, pull requests, and new branches are run through `R CMD check`. rOpenSci packages continuous integration must also be linked to a code coverage service, indicating how many lines are covered by unit tests.

Both test status and code coverage should be reported via badges in your package README.

## How to use continuous integration?

The `usethis` package offers a few functions for continuous integration setup, see [the docs](http://usethis.r-lib.org/reference/ci.html).

Details will be provided below for different services.

## Which continuous integration service(s)?

Different continuous integration services will support builds on different operating system.

R packages should have CI for all platforms when they contain:

* Compiled code

* Java dependencies

* Dependencies on other languages

* Packages with system calls

* Text munging e.g. getting people's names (in order to find encoding issues).

* Anything with file system / path calls

### Travis CI (Linux and Mac OSX)

Travis offers continuous integration for Linux and Mac OSX.

R is now a [natively supported language on Travis-CI](http://blog.travis-ci.com/2015-02-26-test-your-r-applications-on-travis-ci/), making it easier than ever to do continuous integration. See [R Packages](http://marker.to/NEr8Bd) and Julia Silge's [Beginner's Guide to Travis-CI for R](http://juliasilge.com/blog/Beginners-Guide-to-Travis/) for more help.

### Appveyor CI (Windows)

For continuous integration on Windows, see [R + Appveyor](https://github.com/krlmlr/r-appveyor).

### Circle CI

[Circle CI](https://circleci.com/) is e.g. used by rOpenSci package [`bomrang`](https://github.com/ropensci/bomrang) as an alternative to Travis CI.

## Test coverage

Continuous integration should also include reporting of test coverage via a testing service such as [CodeCov](https://codecov.io/) or [Coveralls](https://coveralls.io/).  See the [README for the **covr** package](https://github.com/jimhester/covr) for instructions, as well
as `usethis::use_coverage()`. 

If you run coverage on several CI services [the results will be merged](https://docs.codecov.io/docs/merging-reports).

## Even more CI: OpenCPU

After transfer to the ropensci organization, each push to the repo will be built on OpenCPU and the person committing will receive a notification email. This allows an additional CI service for package authors that that allows for R functions in packages to be called remotely via https://ropensci.ocpu.io/ using the [opencpu api](https://www.opencpu.org/api.html#api-json). For more details about this service consult the OpenCPU [help page](https://www.opencpu.org/help.html) that also indicates where to ask questions.

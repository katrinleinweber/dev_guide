# Contributing Guide {#contributingguide}

<div class="summaryblock">
<p>This chapter outlines how you can contribute to the rOpenSci project as a user or developer.</p>
</div>

So you want to contribute to rOpenSci? Fantastic! First of all, maybe contributing code or documentation to a package is not the (only) way you’ll want to get involved. Check out our [community page](https://ropensci.org/community/) to find out all the ways to participate in the project, from reading about our packages to volunteering to review them.

We strive to make contributing to our suite a constructive and positive experience and we welcome participation that adheres to [our code of conduct](https://ropensci.org/coc/). 

If you wish to contribute to this guide itself, please report any suggestions via [this GitHub repository](https://github.com/ropensci/dev_guide).

## Reporting use cases

It’s valuable to both users and developers of a package to see how it has been used “in the wild”. If you see a use case of one of our packages, please post the link to our [discussion forum in the Use Cases category](https://discuss.ropensci.org/c/usecases) and tag Scott Chamberlain (@sckott) for inclusion in the [rOpenSci biweekly newsletter](https://news.ropensci.org/). Let the package author know by opening an issue in the GitHub repository for that package, perhaps suggesting they create a “use cases in the wild” section in the README, and maybe even tag them in a tweet about the use case. This goes a long way to encouraging people to keep up development knowing there are others who appreciate and build on their work.

See examples of README’s listing use cases in the wild [here](https://github.com/ropenscilabs/ghrecipes/blob/master/README.md#use-cases-in-the-wild) and [here](https://github.com/ropensci/riem/blob/master/README.md#use-cases-in-the-wild).

## Reporting issues or feature requests

If you already have a package in mind, head to its issue tracker to report a bug or a feature request you might have. E.g. if you have a feature request for `magick`, the place to fill it is https://github.com/ropensci/magick/issues

When reporting a bug try to include a reproducible example - a “[reprex](https://www.tidyverse.org/help/#reprex)” - to help the package author help you.

## Prerequisites for package development

Before contributing to one of our packages, you might want to read a bit more about package development in general and our guidelines.

### Learning about package development

#### Tutorials

* [Hilary Parker's famous blog post *Writing an R package from scratch*](https://hilaryparker.com/2014/04/29/writing-an-r-package-from-scratch/)

* [This pictorial by Matthew J Denny](http://www.mjdenny.com/R_Package_Pictorial.html)

#### Books

* [Hadley Wickham's *R packages* book](http://r-pkgs.had.co.nz/)

* [*Writing R extensions*, the official CRAN guide](http://cran.r-project.org/doc/manuals/r-release/R-exts.html)

* [*Mastering Software Development in R* by Roger D. Peng, Sean Kross, and Brooke Anderson](https://bookdown.org/rdpeng/RProgDA/)

* [*Advanced R* by Hadley Wickham](http://adv-r.had.co.nz/)

* [*Testing R code* by Richard Cotton](https://www.crcpress.com/Testing-R-Code/Cotton/p/book/9781498763653)

##### MOOCs

There is a [Coursera specialization corresponding to the book by Roger Peng, Sean Kross and Brooke Anderson](https://fr.coursera.org/specializations/r), with a course specifically about R packages.

### Reading about our guidelines

See the whole first section of this book: [Building Your Package](#building)

## Finding where to contribute code or documentation

Our packages are developed on GitHub. We have two organizations:

* https://github.com/ropensci for more mature packages, , including some developed by rOpenSci staff and some developed by community members where the package has gone through [review and onboarding](#onboardingintro)

* https://github.com/ropenscilabs for experiments and packages that are not ready for release yet.

If you already know what package you’d like to contribute to, have a look at its issue tracker and comment in one of the issues to ask the maintainer whether they'd be interested in your help. E.g. if you like `taxize`, the place to look is https://github.com/ropensci/taxize/issues

If you’re not sure which package you’d like to contribute to, you can start by browsing [our packages page](https://ropensci.org/packages/). To browse issues targeted at beginners you could try [the `contributr` Shiny app by Lucy D'Agostino McGowan](https://ropensci.shinyapps.io/contributr/) or use an advanced GitHub search such as [this one](https://github.com/search?q=user%3Aropensci+user%3Aropenscilabs+label%3ABeginner+state%3Aopen&type=Issues) that gets all issues from "ropensci" or "ropenscilabs" organizations that are open and labelled "beginner".

 Still not sure how you can contribute? Tell us about your expertise and interests and we’ll try to match you with a package that could use your help.
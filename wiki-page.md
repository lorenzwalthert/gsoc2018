Advancing styler - A flexible source code formatter for R
================
Lorenz Walthert

2/23/2018

# Background

styler started out as a small project developed by Kirill Müller and it
evolved throughout [Google Summer of
Code 2017](https://summerofcode.withgoogle.com/archive/2017/projects/5410482240356352/)
from a proof of concept into a ready-to-use source code formatter for
the R language, implemented in R. One of its distinguishing features is
its flexibility and the separation of a style guide that contains
formatting rules from the actual transformation of code according to it,
which allows users to create their own style guide and apply it with
styler. Although many goals of Google Summer of Code were achieved,
there remains a lot of work to do to make styler a reliable, flexible
and comprehensive source code formatter for R.

# Related work

There are a couple of other packages with similar functionality and we
repeat (and extend) what we stated about them last year.

  - [formatR](https://yihui.name/formatr/): Currently powers
    pretty-printing in knitr. Parses code and uses R’s deparsing
    mechanism to emit formatted source code. Applies base R’s notion of
    source code formatting. Has problems with certain edge cases, and
    cannot reliably restrict the width of the formatted output, removes
    comments in some edge cases. Not really customizable.
  - Google’s [R formatter](https://github.com/google/rfmt): Aims at
    producing “aesthetically appealing” formatting by using an
    optimization approach ([technical
    report](https://research.google.com/pubs/pub44667.html%5D)),
    requires Python.
  - “Reformat code” command in RStudio: Cannot be easily automated,
    implemented in Java. Applied style is just slightly different from
    the tidyverse style guide.
  - [lintr](https://github.com/jimhester/lintr): Only detects style
    violations, cannot currently fix them.

All of the above solutions operate with a hard-coded notion of style
which cannot be changed easily. The code is edited too heavily, or (in
the case of lintr) not at all.

styler was designed with flexibility in mind and hence offers an
infrastructure that allows for a wide range of customization. In
particular it can: 

* style according to an arbitrary, user-defined style guide. 
* handle tidy eval syntax properly (\!\!\! is not turned
into \!(\!(\!…)).
* handle the pipe `%>%` properly (does not remove line breaks after it).
* handle non-R files (currently only .Rmd).

Given that styler already has a lot of benefits, it seems to make sense
to further improve styler to become a comprehensive source code
formatter.

# Details of your coding project

First, it seems crucial that the student can become familiar with the
project. In particular, he / she should understand how the source code
is organized, what conventions and design principles are followed, how
code is tested. As styler is a project with currently more than 6
thousand lines of source code (in the R/ directory only, not including
any tests, vignettes etc.), this will take a bit of time. Code
contributed by the student should be indistinguishable from existing
source code and frictions should be avoided to the extend possible.

As far as actual contributions to styler go, there are two main
categories the student can contribute to: Postponed issues and further
ideas:

## Postponed issues

There are a number of [issues](https://github.com/r-lib/styler/issues)
in the GitHub repository of styler that were closed and labeled with
“Status: Postponed” and are to be resolved at some point, better
sooner than later. They can be grouped into the following categories:

- Infrastructure.
- Edge cases and cases not yet covered in the tidyverse style guide
  (need to adapt tidyverse style guide in sync with these changes):
- New rules styling rules.
- New functionality in terms of UI.

Solving a few, easy-to-tackle postponed issuses (can be found via 
label:"Complexity: Low" and label:"Status: Postponed") could help the student
to get familar with the code base while starting to make some contributions to 
the project.

## Further ideas

There is quite a few ideas how styler could be improved or extended. Here
are a few, sorted according to priority. However, we want the student to 
have a say as well on what he wants to work on.

- A mechanism to enforce a maximum width (e.g. 80 characters).
- Implementing other style guides, in particular the base R style
  guide and the Google Style Guide as well as the style guides
  suggested in #340.
- A Domain Specific Language (e.g. YAML-based) to store styling specification
  of a project.
- Implementing a more sophisticated Add-in in which styling rules
  can be checked unchecked individually, allowing for a very custom styling.
- Implementing an algorithm that can detect style given a code base (and 
  potentially style guides to match it against).


# Expected impact

styler is a package that already benefits people today, both package developer
and end user. A consistent style is important, especially in collaborative 
settings. The initial release of styler on CRAN had about 800 direct downloads 
within the first 30 days and it will become a second-level dependency of 
devtools (via usethis) with the next devtools release. 
reprex (a tidyverse core package) allows the user to optionally style the code 
it processes and exampletestr uses styler to prettify code.

# Mentors

The mentors for this project are:

  - Lorenz Walthert (<lorenz.walthert@icloud.com>, principal mentor) is
    the maintainer of styler, former student of the styler Google Summer
    of Code Project 2017 and student of statistics, living in Zurich.
  - Kirill Müller (<krmlr@gmail.com>, secondary mentor) is the creator
    of styler, last year’s mentor of the styler Google Summer of Code
    Project and active contributor to the tidyverse and r-lib, living in
    Zurich.

# Tests

## Workflow

Students, please do one or more of the following tests before contacting
the mentors above. As far as the workflow goes:

  - fork the upstream repo (r-lib/styler).
  - create a branch dedicated to the test named "[your
    name]-[difficulty]" using dash separators and all lowercase
    letters, e.g. if you are Jack Ben and you want to solve the easy
    task, name your branch *jack-ben-easy*.
  - Then, submit a Pull Request (PR) to **your** own master branch of
    the fork and make sure all continuous integration tests pass
    (codecov can be ignored). Please add explanations to what you did
    when submitting the PR.
  - Then, add a link to your solution under **Solutions of tests**
    below.

## Actual tests

  - Easy: Read the vignettes of the styler 
    [pkgdown page](http://styler.r-lib.org/index.html). In your own words, 
    examplain why an approach with a nested parse data structure was preferred 
    over an approach with a flat parse structure.
  - Medium: Get familiar with the testing infrastructure used in styler.
    The workhorse functions are defined in R/serialized\_tests.R and
    pretty much every test uses it. The message sent to the console if
    the *-in.R and *-out.R are different ends with some Boolean value
    that does not belong to the message. Can you fix this and explain
    what the problem was? Hint: To see the message displayed, you must
    make the test fail.
  - Hard: Resolve one of the issues labeled “Status: Postponed” and
    “Complexity: Low”, e.g. #199.

# Solutions of tests

Students, please post a link to your test results here.

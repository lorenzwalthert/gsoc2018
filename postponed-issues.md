## Postponed issues

There are a number of [issues](https://github.com/r-lib/styler/issues)
in the GitHub repository of styler that were closed and labeled with
“Status: Postponed” and are to be resolved at some point, better
sooner than later. They can be grouped into the following categories:

  - Infrastructure: Consistent naming (#16), verification of styling
    (\#140), removing NSE calls (\#199), tab conversion (#213),
    parallel styling (#277), caching unchanged files for repeated
    styling (#320), use styler to cache code (#343).
  - Edge cases and cases not yet covered in the tidyverse style guide
    (need to adapt tidyverse style guide in sync with these changes):
    line breaks and curly braces / function declaration (#124, #125,
    #254), infix operators and indention (#255), ensure new lines at
    EOF (#314).
  - New rules styling rules: maximal character width (#247), alignment
    detection (#258, #317), adding curly braces to other than if
    statements (#286), remove comments (#334), remove blank lines
    (#335).
  - New functionality in terms of UI: corrupt code, unstyle code (#22,
    #220), style from clipboard (#122), use styler as a CI step
    (#302), store styler config in yml file (#319), styling of roxygen
    example code (#332), support styling of unsaved .Rmd (#339) ,
    style syntactically invalid files (#346).

In terms of workload, the maximal character width, alignment detection
and config integration are probably the most complex and time consuming.
However, before diving into that, we prefer to close a significant
amount of the infrastructure and edge case issues listed under bullet
one and two.

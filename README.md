= Git Immersion Labs =

These are the labs for the Git Immersion training, a series of
self-paced exercises that take you through the basics of using git.

== Online ==

You can find the labs online at
"http://edgecase.github.com/git_immersion":http://edgecase.github.com/git_immersion.

== Building the Lab ==

The labs are generated from a single source file that describes
each of the labs.  The generation is done in two steps.

First, the "rake run" method runs through each of the labs and
executes the listed commands and captures the output.  The auto
directory is used for the automatic running and the output is captured
in the +samples+ directory.

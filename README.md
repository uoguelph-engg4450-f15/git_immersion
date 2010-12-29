# Git Immersion Labs

These are the labs for the Git Immersion training, a series of
self-paced exercises that take you through the basics of using git.

## Online

You can find the labs online at
[http://edgecase.github.com/git_immersion](http://edgecase.github.com/git_immersion).

## Building the Labs

The labs are generated from a single source file that describes
each of the labs.  The generation is done in two steps.

First, the `rake run` command runs through each of the labs and
executes the listed commands and captures the output.  The `auto`
directory is used for the automatic running and the output is captured
in the `samples` directory.

Second, the `rake labs` command generates the HTML labs using the text
from the `src/labs.txt` file and the captured live output from the
`samples` directory.  Template files for the main index, the lab
pages, and the navigation divs can be found in the `templates`
directory.

The HTML output is put into `git_tutorial/html`.  Browsing the
`git_tutorial/html/index.html` file will bring up the git tutorial in
your browser.

## Publising the Labs

To publish the labs on the web-site, run the `rake publish` command.
This will copy the `git_tutorial/html` directory to the `gh-pages`
branch. The `gh-pages` branch is then pushed, which auto-publishes it
from github.

Manually modifying the files in the `gh-pages` branch is probably the
wrong thing to do.  Modify the appropriate template or css file on the
master branch, then run `rake publish`.








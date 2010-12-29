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

## Lab Format Directives

The `labs.txt` file contains all the lab text, formatted as a textile
file with additional directives interpreted for both run time
(generating the sample output) and format time (generating the HTML).

The Format Directives are:

### h1. _\<lab name\>_

Starts a new lab with the name _\<lab name\>_.  Each lab 

### pre(_\<class name\>_).

A section of predefined code, using the HTML class of _\<class
name\>_.  The predefined code block runs until a blank line.

### p. _\<text...\>_

A paragraph of text.  The text for the paragraph will continue on
following lines until a blank line.

### Execute:

Execute the following shell command until a blank line is encountered.
Commands are executed as they appear with the following exceptions.

* +_\<command line\>_

  Run this _\<command\>_ line silently, do not include it on the lab
  output.

* -command line

  Do not run this _\<command line\>_, but include it in the lab
  output.

### File: _\<filename\>_

Format the following lines (until an "EOF" string is encountered) as
the contents of a file name _\<filename\>_.

### Output:

Format the following line.  (until an "EOF" string is encountered) as
the output of commands.

Output lines starting with = are used to grab the sample files
generated during the run phase.

### Set: _\<keyword\>_=_\<ruby expression\>_

Evaluate the _\<ruby expression\>_ and set the _\<keyword\>_ to that
value.  Often used to grab dynamic data from the run phase for use in
later commands.

For example, the following will grab the git hash value for the commit
labelled "First Commit", and store it in _\<hash\>_.  When the `git
checkout` command is executed, it uses the value of _\<hash\>_ in the
command.

    Set: hash=hash_for("First Commit")
    Execute:
    git checkout \<hash\>


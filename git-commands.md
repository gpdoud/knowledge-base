# Git Commands

## Show the commits in branch1 missing from branch2

    git log branch1 --not branch2 {--oneline}

## Show at most n abbrev. commits and message

    git log {-n} {--oneline}

## Rename current branch or any existing branch 

    git branch -m { <oldname> } <newname>

## Remove files from repository but not from disk

    git rm -r --cache {files...|folders...}
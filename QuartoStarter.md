My notes on Quarto
================

# Creating a quarto project

You can start a new quarto project from scratch, but you can also
convert an existing project (markdown) to quarto.

**Note:** Make sure to have the most updated RStudio version, which will
contain full Quarto embedded.

## Creating new project

-   **On Github**

    -   Create your repository

    -   Go on code, copy the http repository path

-   **On RStudio**

    -   To clone your repository in your computer and edit on RStudio

        -   File, New Project, Version Control

            ![](figures/gitrepo.png)

        -   Include the http URL (or ssh if http does not work, see
            notes)

        -   Chose the path to include the project

            ![](figures/getfromgit.png)

        -   Done, your github repository is clone and you can edit on
            RStudio

    -   To create a new file in your repo

        -   File, New File, Quarto Document (or Quarto Presentation)

            -   Chose the file type (Pdf, WordDoc, html, PowerPoint,
                etc)

                ![](figures/newfile.png)

            -   Edit your file on Visual or source mode on RStudio

    -   Files to edit

        -   Readme - it is the file that will be shown in your github
            repository

            -   can be a front page linking to other pages within your
                repo

        -   .gitignore

            -   add files that you do not want to be tracked by git
                (either temporary files, or system files, etc)

            -   Files and directories in my standard gitignore

                    # Mac files 
                    .DS_Store

                    #Quarto files 
                    /.quarto/

                    # R files
                    .Rproj.user 
                    .Rproj.user/ 
                    .Rhistory
                    *.RData
                    *.Ruserdata

                    # conversion files (from qmd to pdf) 
                    *.tex
                    *.aux 
                    *.log

<!-- -->

-   see note at end on how to fix your gitignore if you want to stop
    tracking files after they were already pushed to your repo.

## Converting Markdown to Quarto:

-   **In the terminal**

    -   Go to local repo director, on terminal, type:

                  quarto create-project

-   Edit your \_quarto.yml file with configurations

# Updating existing files

-   **On RStudio**

    -   Update the files, save changes

    -   Mark each file to stage (add, modified, deleted)

    -   Commit changes (with message)

    -   Pull

-   **On terminal:**

    -   If you want to convert files to different formats than
        specified, inside the local repo type the following command to
        convert qmd (= quarto extension) files

            render quarto --to <format>

    -   format options include GitHub flavored markdown (gfm), docx, pdf
        (see more in the [Quarto
        userguide)](https://quarto.org/docs/computations/r.html#rendering)

# Notes of issues encountered

-   For cloning a repo: http option might not work for some setups
    (while it works for my desktop, it doesn’t for my laptop), which
    will require the ssh option.

-   This also requires the creation of a ssh key - [see github page help
    for
    that.](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

## To fix gitignore (to stop tracking files already in your repo)

From
[stackexchange](https://stackoverflow.com/questions/1139762/ignore-files-that-have-already-been-committed-to-a-git-repository)

-   To untrack a single file that has already been added/initialized to
    your repository

    `git rm --cached filename`

-   To untrack all files/directories in your .gitignore

    -   First, **commit any outstanding code changes**

    -   Then, on the terminal, run this command to remove changed files
        from the index (staging area):

        `git rm -r --cached`

    -   Add all changes to the staged area

        `git add .`

    -   Then commit it:

        `git commit -m ".gitignore is now working"`

To undo `git rm --cached filename`, use `git add filename`.

Notes from the original answer:

-   Make sure to **commit changes** before running git add.

-   Please be careful, when you push this to a repository and pull from
    somewhere else into a state where those files are still tracked, the
    files will be DELETED.

    -   Note from Ana - I got into this, and could return my files, but
        I went through a stressful half an hour around midnight there.

Another note - from another answer, it is funny to look at how many
people have done this by looking for the `".gitignore is now working"`
commit message:

[github.com/search?q=.gitignore+is+now+working&type=Commits](https://github.com/search?q=.gitignore+is+now+working&type=Commits) 

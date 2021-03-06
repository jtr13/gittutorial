The No-Shell\* Git/GitHub Tutorial for R users using RStudio
================
Joyce Robbins
2017-11-14

\*Not exactly, but we'll keep shell commands to an absolute minimum.

This is a simple barebones tutorial designed to help you first become familiar with GitHub.com, and then get started using a combination of GitHub and Git for code version control, sharing, and collaboration -- three distinct but related enterprises.

If you are not familiar with one or more of the concepts just mentioned, or are asking yourself why you should bother with any of this, I recommend that you first watch this webinar by Hadley Wickham, in which he explains the benefits of creating systems for version control, sharing, and collaboration, which he presents in terms of the larger goals of *safety* and *community*:

[Collaboration and time travel: version control with git, github and RStudio](https://www.rstudio.com/resources/webinars/collaboration-and-time-travel-version-control-with-git-github-and-rstudio/)

### TO DO \#1: Create a repository on GitHub.com

1.  If you have an account, sign in to [GitHub](https://github.com/login);

    if you don't have an account, [create a GitHub account](https://github.com/join?source=login).

2.  Click "Start a project" or click "+" in the upper right corner and then "New repository"

3.  Give it the name "goldfish" (or any other name you wish)

4.  Check ☑️**Initialize this repository with a README**

5.  Click "Create repository"

### TO DO \#2: Upload a file to the repository on GitHub.com

1.  Find the home page of your new repo

2.  Click "Upload files"

3.  Upload a photo of a goldfish (or any other file) to your repo

### TO DO \#3: Submit an issue on GitHub.com

1.  Go to <https://github.com/jtr13/goldfish>

2.  Click the Issues tab

3.  Click New issue

4.  Make up a title and comment and click "Submit new issue"

**NOW LET'S LEAVE GITHUB.COM AND SET THINGS UP TO USE VERSION CONTROL FROM WITHIN RSTUDIO**

### TO DO \#4: Configure Git

1.  Follow these instructions to configure Git: <http://happygitwithr.com/hello-git.html>

2.  The first time you use `git push` you will be asked for your GitHub username and password. Depending on how things are set up on your computer, these credentials may be saved automatically and you won't be asked again. Or you may be asked if you want the credentials to be saved. If not, if it gets tedious to repeatedly type in your username and password, follow these instructions to cache your credentials (that is, save your username and password):

<https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage>

Please [submit an issue](https://github.com/jtr13/gittutorial/issues) and describe your experience caching credentials. Add the label "caching credentials."

### TO DO \#5: Clone the repo you created on GitHub.com

1.  Go to the repo on GitHub, click "Clone or download" and then the "Copy to clipboard" button:

The URL will has three parts: 1) the GitHub address, 2) your username, 3) the name of the repository followed by ".git", for example:

<https://github.com/jtr13/goldfish.git>

1.  In **RStudio**, click "File New Project..."

2.  Choose "Version Control"

3.  Choose "Git"

4.  Paste the repository URL into the first box.

5.  Give the project directory a name (it can be the same name as the repository)

6.  Choose where to create the project (best to keep it out of other version control systems such as Dropbox).

7.  Click "Create Project"

### TO DO \#6: Add a file to the repository from within RStudio

1.  Create any file as you normally would in RStudio and save it.

2.  Notice that it appears on the Git tab on the upper right corner of the screen.

3.  Check the box to "stage" the file (this is equivalent to `git add`) -- the status changes to a green "A".

4.  Click "Commit". A new screen opens up.

5.  Write a commit message, such as "first commit". You must do this!

6.  Click "Commit". ( = `git commit`) You will get a popup with info about the commit. Close it.

7.  Click "Push" (green up arrow on top right of screen) ( = `git push`)

8.  You should get another info message that ends with 'master -&gt; master\`. You can close it.

9.  Go back to **Github.com** If all went well, your new file will be there.

### TO DO \#7: Change a file in the repo from within RStudio

1.  Make a change to your new file. Save it. (Note that nothing happens in the Git window until you save the file.)

2.  A blue "M" should appear in the Git window since the file has been **M**odified.

3.  Click the "stage" button and the "M" will jump to the left.

4.  Click "Commit". Now you will see the changes you've made since your last commit. This is useful!

5.  Repeat steps 5.- 9. from "Adding a file"

### TO DO \#8: Change multiple files in RStudio in one commit

1.  Add several files and make changes to them.

2.  Stage (add), commit, and push them all at once. You can commit multiple files with one commit message.

### TO DO \#9: Change a file on GitHub.com and pull it to local

A key principle of working with version control is not to make changes similtaneously in two places. Since cloning the repository, we have been making local changes and pushing them to remote (GitHub.com). Now we'll try making a change remotely (on GitHub.com) and then retrieve (`git fetch`) the changes and combine (`git merge`) them with what we have locally. These two tasks are often combined into one (`git pull`), which we will accomplish in RStudio by clicking the down arrow ![](pull.png) button in the Git pane. (More info from GitHub Help on fetching a remote can be found [here](https://help.github.com/articles/fetching-a-remote/).

1.  Go to **GitHub.com** and make an edit to the README.md file in your repository. (Click the file name, click the Edit this file icon ![](edit.png), make some changes, then click the green "Commit changes" button.)

2.  Go back to **RStudio** and click the `git pull` ![](pull.png) button. You should get a message indicating that README.md was changed.

**Make it a habit to start your work session with a "pull" and end it with a "push" to prevent getting out of sync with the remote version of your repository.**

### TO DO \#10: Let's make a mess :smiling\_imp:

Ok, we know we're supposed to pull first before we begin working, but let's suppose we forget to do that... let's simulate that scenario.

1.  Making another change to the README.md on GitHub.com

2.  Jump back to **RStudio** and make a change to a *different* local file *without pulling the remote change first*.

    Let's see what happens when we try to push:

3.  Commit the local changes and click push.

What happened? There's a problem! If you change remote and local simultaneously your push will be rejected, and you'll get a message that looks like this:

    To https://github.com/jtr13/gittutorial.git
     ! [rejected]        master -> master (fetch first)
    error: failed to push some refs to 'https://github.com/jtr13/gittutorial.git'
    hint: Updates were rejected because the remote contains work that you do
    hint: not have locally. This is usually caused by another repository pushing
    hint: to the same ref. You may want to first integrate the remote changes
    hint: (e.g., 'git pull ...') before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.

Since the changes are in different files, we can fix this by *pulling* ![](pull.png) first and then *pushing* ![](push.png) again.

### TO DO \#11: Let's make a bigger mess. :smiling\_imp: :smiling\_imp:

This time we're going to make simultaneous changes to the *same file* remotely and locally and see what happens.

1.  Make a change to the README.md file on **GitHub.com** and click Commit changes.

2.  In **RStudio**, make a change to the README.md file and save it.

3.  Commit the changes in **RStudio** and click push ![](push.png).

A problem... we get a similar error message as before. Let's try to solve it as we did in the previous section but clicking pull ![](pull.png) before pushing.

But this time it's not so easy to fix the problem. If you try to pull changes from remote with edits to the same file, you'll be informed there's a conflict when you try to pull. It will look something like this:

    From https://github.com/jtr13/gittutorial
       b4c21a1..28b94b4  master     -> origin/master
    Auto-merging README.md
    CONFLICT (content): Merge conflict in README.md
    Automatic merge failed; fix conflicts and then commit the result.

Now what?

1.  Open README.md in **RStudio** and you'll see that it combines changes make remotely and locally along with conflict markers "&lt;&lt;&lt;&lt;&lt;&lt;&lt;", "&gt;&gt;&gt;&gt;&gt;&gt;&gt;" and other stuff.

2.  Delete all the added stuff and just fix the file as you want it to be. *Do not worry if you are keeping the local or the remote changes; for our purposes, it doesn't matter.*

3.  Save the file. Commit and push the changes. *You just resolved a merge conflict!* :muscle:

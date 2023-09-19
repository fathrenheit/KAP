[English]
GIT is a version control program.

**GLOSSARY**
**GitHub**: GitHub is a code hosting platform for version control and collaboration.

**Snapshot**: A checkpoint of a virtual machine at a point in time. Meaning Git basically takes a picture of what all your files look like at that moment and stores a reference to that snapshot.
Repository:  A repository contains all of the project files (including documentation), and stores each file's revision history. Repositories can have multiple collaborators and can be either public or private.

**Push**: To push means to send your committed changes to a remote repository on GitHub.com. For instance, if you change something locally, you can push those changes so that others may access them.

**Pull**: Pull refers to when you are fetching in changes and merging them. For instance, if someone has edited the remote file you're both working on, you'll want to pull in those changes to your local copy so that it's up to date.
Branch: A branch is a parallel version of a repository. It is contained within the repository, but does not affect the primary or main branch allowing you to work freely without disrupting the "live" version. When you've made the changes you want to make, you can merge your branch back into the main branch to publish your changes.

**Merge**: Merging takes the changes from one branch (in the same repository or from a fork), and applies them into another. This often happens as a "pull request" (which can be thought of as a request to merge), or via the command line. A merge can be done through a pull request via the GitHub.com web interface if there are no conflicting changes, or can always be done via the command line.

**Commit**: A commit, or "revision", is an individual change to a file (or set of files). When you make a commit to save your work, Git creates a unique ID (a.k.a. the "SHA" or "hash") that allows you to keep record of the specific changes committed along with who made them and when. Commits usually contain a commit message which is a brief description of what changes were made.

INSTALLING GIT
- First thing first we need to install GIT. Further notes on this topic can be found at: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

CREATING A NEW REPOSITORY
- Secondly we need a repository. If we do *NOT* already have one we need to make a new repository on GitHub. To do that we use:
	1. Go to https://www.github.com/new
	2. Create a new repository.

CLONING A REPOSITORY:
- There are couple of ways to download <`clone`> a repository. 
	1. Using HTTPS: It will required a username and password.
	2. Using SSH key: This option will also provide a authentication on GitHub.
We will mainly stick with URL address (HTTPS option). 

- Opening Windows/Linux/Mac Terminal:
	- Change the directory we want to clone the repository using `cd` and/or make a new directory `mkdir` if necessary.
	- `git clone URL`:  Using this command will clone everything within the URL into the directory we are already in.

 - Creating a new file (0 byte sized):
	- In Mac or Linux terminal type: `touch file_name.file_extension`
	- In Windows PowerShell type: `New-Item file_name.file_extension` or shortly `ni file_name.file_extension` (`ni` stands for `New-Item`)
	- Or alternatively if we have VS Code installed, we can simply type in terminal: 
		- `code .` to create an empty file without an extension
		- `code hello.py` to create a script named `hello` with python `py` extension.

KEEP TRACK OF CHANGES
Creating a new file (or multiple files) or editing existing files results changing. After that point we can let Git to keep track of those changes that have been made. If we are working on multiple files and only want to save for example 3 of them, with the `add` execution, we simply say keep track of this and that or these files to later to be committed. This step is the last step before committing changes.
- Run `git add new_file_name.with_extension>` to track of a specific file or
- Run `git add .` to track all files within that directory.

COMMITING CHANGES -> değişiklikleri onaylamak/kaydetmek
This step takes snapshot of the current state of the repository, keeping track of any of the changes that have been made to files that we `add`ed.
- `git commit -m "message"`; typing this command in Terminal, now we can save the very last current state of the files that added. `-m` flag stands for "message" and `"message"` must contain one-line description of the changes we are committing to a Git repository. Using a descriptive message is important since we can refer back to that commit simply by looking the description message.
- If we only changed existing files and not created new ones, instead of using `git add .` and then `git commit`, we can condense (belli bir ölçüde sadeleştirmek) these commands into one command: `git commit -am "some message"`.

*Until* this time all the actions we take actually happened in our *local* version of the repository. We actually keep working in our local repository offline, so internet is not a necessity. Following comment was asked to ChatGPT:
"Git keeps track of changes locally by creating snapshots of your project's files and directories at each commit. It does not save complete copies of the entire project for each commit; instead, it uses a highly efficient mechanism that stores the changes (deltas) between commits. This approach is what makes Git very space-efficient and fast.

Here's a simplified explanation of how Git tracks changes:

1. **Snapshots**: When you make a commit, Git takes a snapshot of the entire state of your project at that point in time. This snapshot includes all the files and directories in your project, but it doesn't duplicate the unchanged files from the previous commit. Instead, it records pointers to the previously committed, unchanged files, which saves space.
    
2. **Deltas**: Git calculates the differences (deltas) between the current snapshot and the previous one. It stores these differences in a compressed format. This is what makes Git's storage mechanism efficient because it doesn't save the entire file for each change; it only records what has changed.
    
3. **Commit Objects**: Git creates a commit object that contains metadata, such as the commit message, author information, timestamps, and pointers to the parent commit(s). It also includes the reference to the root tree object that represents the current state of your project.
    
4. **Commit Chain**: Each commit points to its parent commit(s), forming a chain of commits that represents the history of your project. This is how Git reconstructs the entire history by following the commit chain backward in time.
    

By using this method, Git can quickly navigate through the history and reconstruct the state of your project at any point in time. It also minimizes the storage requirements because it stores only the changes and can reuse unchanged files from previous snapshots.
This mechanism of snapshots and deltas is what allows Git to efficiently manage the complete history of your project while using a minimal amount of disk space. It's one of the key reasons Git is so popular for version control"

TO REFLECT COMMITING CHANGES TO ONLINE
Previously we highlighted that `clone, add, commit` commands happens in our local repository in other words in our computer. If we want to push those changes up to GitHub, then we need to use additional commands.
- `git status`: This command provides information about the current state of our local Git repository. When we execute this command in Terminal, Git will display; (1) branch information, (2) changes to be committed, (3) changes not staged for commit, (4) un-tracked files
- `git push`: This command is used to take the files have been changed in the repository and `push` them up to some remote server on GitHub. 

DOWNLOADING THE MOST RECENT VERSION
Sometimes the version on GitHub is the most recent version of  that repository (compared to the version on our computer). In these cases we must use `pull` command.
- `git pull`:  This command is used to download the latest version of the repository to our local repository.

MERGE CONFLICTS
In GitHub glossary page, merge conflict defined as this:
*A difference that occurs between merged branches. Merge conflicts happen when people make different changes to the same line of the same file, or when one person edits a file and another person deletes the same file. The merge conflict must be resolved before you can merge the branches.*
It is simply when two or more people  attempt to change a file in ways that conflict each other. This will occur typically when we either `git push` or `git pull`. GIT automatically outlines (ana hatlarıyla belirtmek, özetlemek) what the conflict is. Here is an example:
```
a = 1
<<<<< HEAD
b = 2
=====
b = 3
>>>>> 56782736387980937883
c = 3
d = 4
e = 5
```
- `56782736387980937883` is the hash that represents the commit that conflicts.
- Between `<<< HEAD` and `====` is our change on the file
- Between `====` and `>>>> hash` it the other change on the file
- Many modern editors provides highlighting and simple options like accept current, accept incoming, accept both etc.

- `git log`: This command is useful that gives us a history of all of our commits on that repository.
- `git reset --hard <commit>`:  Reverts our code to exactly how it was after the specified commit. To specify the commit, use the commit *hash* associated with a commit which can be found using `git log`.
- `git reset --hard origin/master`: Reverts our code to the version currently stored online on GitHub.

BRANCHING
Branching is GIT's wat of working on different parts of the repository at the same time.  Branching is quite powerful, because it provides working on features or bugs independently. Each branch represents a separate path of development, allowing us to make changes, add new features, or fix bugs without affecting the main or other branches.
- `git branch`: This commands shows list of branches in our repository and highlights the branch we are currently on using an asterisk; `* master`.
- `git branch branch_name`: This command creates a new branch from the master branch. It is typically used when you want to create a new branch but continue working on your current branch without switching immediately.
- `git checkout -b branch_name`: This command creates a new branch from the master branch *and* switch to it. It is used when you want to create a new branch and start working on it without remaining on your current branch.
- `git checkout branch_name`: This command switches to `branch_name` and updates the working directory.

When we switch any other branch then main/master, what we do in this branch does *not* affect the main branch. Until we merge them. 
- `git merge branch_name`: This command combines the specified branch's (`branch_name` in this case) history into the current branch. 

OTHER CONCEPTS
- `forking`: Process of creating a copy of a repository.  Then we can clone, push and pulls etc. The reason we do that is even if a repository is *public*, it does not mean anyone can just push to it. That would be probably unsafe if anyone in the world could just update the repository/master code. Instead, we can copy the code using `forking`, make changes to our very own copy of it, push and pull to it. And then when we feel like we have made a contribution, we would like to send back to that specific repository by what's called `pull request` which is basically requesting our code to be pulled in to the repository. And the people maintain the repository can review those pull requests, provide feedback, ask for additional changes and then when everyone is satisfied they can merge those changes into the actual repository.

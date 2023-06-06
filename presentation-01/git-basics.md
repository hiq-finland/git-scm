---
marp: true
paginate: true
---

# Git why, what, how?

---

## What is this series about?
- Introduction to git 
- Brief history of source control management systems
- Managing version history 
- Troubleshooting issues with git
- Structure of git repository
- Git processes
- Continuous integration and delivery

---
## We want you to participate!
You can contact [Jesse](mailto:jesse.taina@hiq.fi) or [Miro](mailto:miro.lehteva@hiq.fi) if you want to be part of
- Bringing up topics to cover
- Be part of making these presentations by making a pull request to this [repo](https://github.com/hiq-finland/git-scm)
- Become a presenter yourself!
---
## What kind of experiences do you have with git or other version control systems

The good?
The bad?
The ugly?

---
## Why would you use SCM like Git?

- Log of changes to the source code
  - Who made the changes?
  - When were the changes made?
  - What changed and why?
- Allow multiple people to edit the same source files
  - Everyone has their own local copy of the source files
  - Changes can be reviewed before merging to main
- Bookmark specific points in the history as releases
  - For example "v1.2.3" or "production"

---
## What are versions?

---

## Different ways of versioning and why does it matter?

### What kind of changes do you think happened between these versions
- Focal Fossa and Jammy Jellyfish 
- 61404 and 61405
- 2.0.0 and 2.1.0

---
## Introduction <br>to Git CLI

![bg contain](./xkcd_1597_git.png)

---
## Why use Git CLI

Benefits to using Git CLI comprared with a Git client with a GUI:

- Efficiency: Using Git CLI can be faster (when you have enough experience)
- Flexibility: More flexibility with all the command-line arguments and options; Git GUIs, however, often offer limited options
- Automation: You can write scripts to perform tasks or complex Git operations automatically
- Portability: Git CLI is available on almost all platforms

---

### Git resources

- See [Git Book](https://git-scm.com/book/en/v2) for good information and tutorials
- See [Git Docs](https://git-scm.com/docs) for reference

---

### Configuring git

#### [git config](https://git-scm.com/docs/git-config)

Username and email need to be set for logging changes. They are added to commit messages along with everything else.

```bash
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

Run the command without the --global option if you need to override the global config in a particular project.


---

### Working with a local repository

#### [git init](https://git-scm.com/docs/git-init)

Initializes a new Git repository in the current directory.

```bash
mkdir project1
cd project1
git init
```

---

#### [git status](https://git-scm.com/docs/git-status)

Shows the current status of the repository.

```bash
$ echo "<h1>Hello from project1</h1>" > index.html
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        index.html

nothing added to commit but untracked files present (use "git add" to track)
```

---

#### [git add](https://git-scm.com/docs/git-add)

git add: Adds changes to the staging area.

```bash
$ git add index.html
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   index.html
```

The staging area lets you control what changes will be included in the next commit.

---

#### [git commit](https://git-scm.com/docs/git-commit)

Commits changes to (the local copy of) the repository.

```bash
$ git commit -m "feat: create index.html"
[master (root-commit) 1b02118] feat: create index.html
 1 file changed, 1 insertion(+)
 create mode 100644 index.html
```

The flag `-m` lets you write a commit message directly in the terminal.

[Conventional commits](https://www.conventionalcommits.org) provides a good set of rules for creating explicit commit messages. These rules are followed in this series.

---
#### Commit - what and why?

- A commit is a snapshot of the current state of a project at the time in which that commit is made.
- Git does not track differences but instead records the entire contents of each file in every commit.
  - Changes between commits can be compared with `git diff`. The command takes two input data sets and outputs the changes between them.
- Commits let us keep track not only of what was changed but when, by whom and why that change was made.
- See also [Recording Changes to the Repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)

---

#### [git log](https://git-scm.com/docs/git-log)

Displays the commit history.

```bash
$ git log
commit 1b0211871bf0d01d750b809612bc456f153d62b5 (HEAD -> master)
Author: Taina Jesse <jesse.taina@hiq.fi>
Date:   Wed May 17 12:14:21 2023 +0300

    feat: create index.html
```

---

#### [git branch](https://git-scm.com/docs/git-branch)

Lists all branches in the repository.

```bash
$ git branch
* master
```

---

#### [git switch](https://git-scm.com/docs/git-switch)

Switches between branches. Creates new ones with the flag `-c`.

```bash
$ git switch -c feature1
Switched to a new branch 'feature1'

$ git branch
* feature1
  master
```

---

#### [git merge](https://git-scm.com/docs/git-merge) (pt. 1)

Merge the commits of one branch into another branch

```bash
$ git branch
* feature1
  master

$ git commit -a
[feature1 8c8c631] feat: add some content to index.html
 1 file changed, 1 insertion(+)

$ git switch master
Switched to branch 'master'
 ```

---

#### [git merge](https://git-scm.com/docs/git-merge) (pt. 2)

```bash
$ git merge feature1
Updating 1b02118..8c8c631
Fast-forward
 index.html | 1 +
 1 file changed, 1 insertion(+)

$ git log
commit 8c8c63191ec311f2709b839efbd1d564b1644f92 (HEAD -> master, feature1)
Author: Taina Jesse <jesse.taina@hiq.fi>
Date:   Mon May 29 14:16:08 2023 +0300

    feat: add some content to index.html

commit 1b0211871bf0d01d750b809612bc456f153d62b5
Author: Taina Jesse <jesse.taina@hiq.fi>
Date:   Wed May 17 12:14:21 2023 +0300

    feat: create index.html
```

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
  - When the changes were made?
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
- Automation: You can write scripts to perform tasks or complex Git operations automatically;
- Portability: Git CLI is available on almost all platforms

---

## Git CLI introduction

#### git init

Initializes a new Git repository in the current directory.

```bash
$ mkdir project1
$ cd project1
$ git init
```

---

#### git status

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

#### git add

git add: Adds changes to the staging area.

```
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
#### git commit

Commits changes to the repository.

```
$ git commit -m "feat: create index.html"
[master (root-commit) 1b02118] feat: create index.html
 1 file changed, 1 insertion(+)
 create mode 100644 index.html
```

The flag `-m` lets you write a commit message in the terminal.

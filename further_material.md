<!--

author:   Central Research Data Management of Kiel University
email:    fdm@rz.uni-kiel.de
version:  0.0.1
language: en
narrator: UK English Female

icon:     assets/images/cau-norm-en-lilagrey-rgb.png

logo:     https://git-scm.com/images/branching-illustration@2x.png

comment:  Online course for getting started with the version control system Git
          and the open source software development platform GitLab. Further material.

script:   https://cdn.jsdelivr.net/npm/mermaid@9.1.1/dist/mermaid.min.js

@mermaid
<script run-once="true" modify="false">
mermaid.initialize({});

var svg = mermaid.render('io9wuwzxt',`@0`.replace(/\\n/g, "\n"),
function(g) {
    return true;
})

"HTML: " + svg
</script>
@end
-->

# Getting started with Git and GitLab

**Thorge Petersen, Britta Petersen, Thilo Paul-Stüve**

Central Research Data Management of Kiel University

> To see this document as an interactive LiaScript rendered version, click on the
> following link/badge:
>
> [![LiaScript](https://raw.githubusercontent.com/LiaScript/LiaScript/master/badges/course.svg)](https://liascript.github.io/course/?https://cau-git.rz.uni-kiel.de/fdm/schulungen/git-einfuehrung/-/raw/main/course.md)
>
> This course assumes a basic knowledge of command line interfaces.
>
> If you need help, feel free to ask us any questions:
>
> [fdm@rz.uni-kiel.de](mailto:fdm@rz.uni-kiel.de)

## Further Topics: Git Client Software

Git is a free software for distributed version management:

- Git is a distributed versioning control system (DVCS), mainly used by programmers to issue changes to applications and keep track of the revisions.
- Git is a actively maintained open source project originally developed in 2005 by Linus Torvalds.
- Git is de facto standard: it is the most widely used modern version control system in the world today.
- Many (software) projects rely on Git for version control, including commercial and open source projects alike.

### Installation

Before you can use Git, you must install it on your computer. Even if you already
have Git installed, you should update it to the latest version.

More information can be found in the [official documentation](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

#### Mac OSX

There are several ways to install Git on a Mac.

If you have Xcode (or its command-line
tools) installed on your system, Git may already be installed. You can check this
by opening a terminal and typing `git --version`.

```console
$ git --version
git version 2.7.0 (Apple Git-66)
```

Installing Git with Homebrew
================

If you use Homebrew for package management on OS X, you can install Git using the
following instructions:

1. Open your terminal and install Git using Homebrew:

    `brew install git`

2. Check with `git --version` if the installation was successful:

    `git --version`

#### Windows

1. Download the latest version of the [Git for Windows installer](https://git-for-windows.github.io/).
2. Once the installer starts, you should see the Git Setup wizard. Follow the on-screen instructions to complete the installation. The default options are a good choice for most users.

#### Linux

Debian/Ubuntu
================

1. Install Git from the shell using `apt-get`:

    `sudo apt-get update && sudo apt-get install git`

2. Check with `git --version` if the installation was successful:

    `git --version`

Fedora
================

1. Install Git from the shell using `dnf`:

    `sudo dnf install git`

    On older Fedora versions, you might need to use `yum` instead:

    `sudo yum install git`

2. Check with `git --version` if the installation was successful:

    `git --version`

#### Configuration

No matter what operating system you have Git installed on, you should now configure
your username and email. These two pieces of information will be associated with
every commit you create in the future.

Open a command prompt and run the commands below to configure your Git username
and Git email address:

```console
git config --global user.name "Jane Doe"
```

```console
git config --global user.email "janedoe@example.com"
```

### More information on Repositories

> A Git repository is a virtual storage of your project. It allows you to store versions of your code and access them when needed.

To interact with a repository locally on your system, you have two options:

1. [Create a new Git repository](#create-new-repository)
2. [Clone existing Git repository](#clone-existing-Git-repository)

{{1}}
********************************************************************************

**Local and remote repositories:**

> A Git repository can be local to your system, but it can also be located elsewhere.
>
> - Your local repository has exactly the same features and functions as any other Git repository.
> - A Git repository on a server (remote) is basically the same as a Git repository of a Git service (e.g. [Gitlab RZ CAU](https://cau-git.rz.uni-kiel.de/)), which in turn is the same as your colleague's local repository.

If you created a new repository using `git init`, you don't have a remote repository
to move your changes to. Typically, when you create a new repository, you use a
Git service (e.g. [Gitlab RZ CAU](https://cau-git.rz.uni-kiel.de/)) and create a repository
there. The Git service provides a Git URL that you add to your local Git repository.
After that you are ready to push to the hosted repository using the `git push` command.

**Note:**

- Your *working directory* is the directory with your source files under git control.
- Git is tracking the difference between your *working directory* and your *local repository*.
- Git is also tracking the difference your *local repository* and (one of) the *remote repositories*.

********************************************************************************

{{2}}
********************************************************************************

**Command overview:**

An overview on which level the different commands operate.

```text @mermaid
sequenceDiagram
    Working Directory->>Staging Area: git add
    Staging Area->>Local Repository: git commit
    Local Repository-->>Remote Repository: git push
    Remote Repository-->>Local Repository: git fetch
    Local Repository->>Working Directory: git checkout
    Local Repository->>Working Directory: git merge
    Remote Repository-->>Working Directory: git pull
    Working Directory->Staging Area: git diff
    Working Directory->Local Repository: git diff HEAD
```

********************************************************************************

### Set up a repository

The following is an overview of how to set up a repository (repo) using Git version
control:

1. [Create a new Git repository](#create-new-repository)
2. [Clone existing Git repository](#clone-existing-Git-repository)

#### Create new repository

The `git init` command creates a new Git repository. It can be used to convert an
existing, unversioned project into a Git repository or to initialize a new, empty
repository.

Most other Git commands are not available outside of an initialized repository,
so git init is usually the first command executed in a new project.

We assume that you already have a project directory where you want to create the
repository. Let's assume the path to the root of your working directory is `/your/project`.
To init your new repository, you first need to navigate to the directory using the
command line and then run the `git init` command:

```console
cd /your/project
git init
```

> **Note:**
>
> - You only have to init a repository once during the initial setup of a new repository.
> - Running this command creates a new `.git` subdirectory in your current working directory.
> - The `.git` directory will contain all of the configuration and metadata necessary for Git to keep track of your files and the changes that you make to them.

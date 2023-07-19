# EPMC-Serverconfig
## EmpirePowers Minecraft Server-Specific  Server Configuration


---

### How to use Git

Install a suitable version of Git for your operating system.

Can I suggest, for Windows: [GitforWindows](https://gitforwindows.org/).

#### Make a Git Hub Account.

Yes, you need one.

#### Cloning the Repository

There are two ways to clone to Repository. I will explain both and why to use each one.

##### Cloning into a new Directory

This is useful for when you want to work on config files without necessarily editing your minecraft installation's files.

Navigate to a directory that you wish to contain this project. Cloning this project will create a new directory of the project's name, within the directory that you run the following command:|

```
git clone https://github.com/LordNotix/epmc-serverconfig.git
```

This may ask you to authenticate your git credentials, do so.

##### Cloning into an existing Directory

This is far more useful for setting the various folders (directories) of your minecraft installation to track this repository.

For full transparency this section is adapted from the answers given [Here on StackOverflow](https://stackoverflow.com/questions/5377960/git-whats-the-best-practice-to-git-clone-into-an-existing-folder).

Navigate to the correct directory. This can be in a file-explorer, or via the command line in the Git Bash window. (`cd` is your friend here for `c`hanging `d`irectory. \[`cd ..` to go up\]).

From within the folder you want to turn into the git project.
```
git init
git remote add origin https://github.com/LordNotix/epmc-serverconfig.git
git fetch origin
git checkout -b main --track origin/main # origin/main is clone's default
```

This may ask you to authenticate your git credentials, do so.

Then you can reset the tree to get the commit you want:

```
git reset origin/main
```

#### Making a new Branch

Once you have your local repostiory, you should see that it is one the `main` branch. This will correspond with the remote branch referred to as `origin/main`. (That is because the remote by default is called `origin` and the default branch of the project is `main`.)

You will need to create a new local branch to save your changes against, as the remove branch is protected. (More on this later).

To do so, I recommend running the following commands from the Git Bash terminal whilst within the directory:

```
git status
git pull
git checkout -b feat/<branch_name>
```

Where you want to replace the entire `<branch_name>` with a suitable name for your changes. We prefact this with `feat/` for ease of sorting later.

Running `git status` again, should show you on this branch.
Running `git pull` in the above commands will ensure that your local `main` is up-to-date with the `origin/main`. (This minimises the chances of you having to do unpleasant merges when rebasing.)

#### Making commits

When you make changes to the files in the local repository (and save them 😉), they will show up in `git status` as having been modified (or added).

You can "add" these files to a staging-commit through the following command:

```
git add </path/to/file.txt>
```

Where `</path/to/file.txt>` represents the path to the file itself. This can be shorter to add multiple files with the same path root, or even simply `.` to add all files within the directory.

Running `git status` again should show these files in Green.

After this, you will need to finalise, and "make" your commit for these changes. You can do so with the following command:

```
git commit -m "<Commit Message>"
```

Where `<Commit Message>` is a note about your changes made. Ideally this would be conforming to the [Conventional Commits Standard](https://www.conventionalcommits.org/en/v1.0.0-beta.2/).

#### Pushing your commits

Once you have made one or more commits and want to either access them from another branch, you will need to "push" your commits to remote. This is why you work on a branch, so that your changes can be pushed to the remote repository and checked out by others, before being finalised back into the `main` branch. If everyone committed directly to `main`, you would spend a lot of time dealing with merge conflicts and not be able to review changes.

Instead to get our changes into `origin/main` we make a merge request, from our remote branch. So we need to get your branch into a remote branch.

The easiest way to do this, is to run the following command.

```
git push
```

And to read the response. You will likely have to run `git branch --set-upstream-to origin/<branch-name>` (where `<branch-name>` is your current local branch name).

For advanced users, you can run `git config --add push.default current` to instead automatically create those remote branches.

#### Merging into origin/main

Navigate to Github and follow the lovely helpful green buttons.

#### Checking out a remote branch

```
git fetch
git branch
git switch <branch-name>
```

Where you should see the branch you want listed to replace the `<branch-name>` with as the results of git branch.

Any questions, google it, or ask me.

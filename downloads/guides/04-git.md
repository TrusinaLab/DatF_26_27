---
layout: default
title: Git
permalink: /guides/git/
---

[Guides home]({{ '/guides/' | relative_url }}) ·
[VS Code]({{ '/guides/vscode/' | relative_url }}) ·
[Terminal]({{ '/guides/terminal/' | relative_url }}) ·
[Anaconda]({{ '/guides/anaconda/' | relative_url }}) ·
[Git]({{ '/guides/git/' | relative_url }})

# Git — installation & everyday commands

**Git** records your project's history on your computer. **GitHub** hosts a copy online for sharing. A *repository* is a project folder with Git history; a *commit* is a saved snapshot. You can always use Git locally without a GitHub account.

## 1. Install once

### For Windows: 

1. Download the installer from [Git for Windows](https://git-scm.com/install/windows).
   *Check if your machine uses x64 or ARM64 in 'System Information'*
2. We will mainly use default installation settings, but make sure to:
	- Choose VS Code as the default editor
	- Continue with **"Git from the command line and also from 3rd-party software"** on the PATH page. This makes `git` available in PowerShell and VS Code. 
	- Keep the **Git Credential Manager** enabled.
3. Close and restart VS Code after installation.

### For macOS:

Open **Terminal** and try `git --version`. If Git is available, continue below. Otherwise, install Apple's Command Line Tools:

```zsh
xcode-select --install
```

Finish the installer, then reopen Terminal. For reference, see the [official macOS installation options](https://git-scm.com/install/mac).

### Check on either system

Run the following command in a new VS Code terminal:

```text
git --version
```

You should see the Git version you installed.

## 2. Set your commit identity - once

Run these commands in a VS Code terminal, replacing the name and email with your own:

```text
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

These settings label your commits; **they do not sign you in to GitHub**. [Official setup reference](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

## 3. Start tracking a project

You make a project folder into a git repository by navigating to the folder and running the `git init` command:

```zsh
cd Exercises1
git init
```

## 4. Everyday workflow - no GitHub

At the start of a session, run `git status` to check if there are any untracked changes. Then edit and save your files. For example, after changing `analysis.py`:

```zsh
git status # are there untracked changes?
git add analysis.py # stage changes for commit

# commit all staged changes and make a snapshot with a message describing what you did
git commit -m "Add uncertainty calculation"
git log --oneline # review the commit history
```

Replace `analysis.py` with the actual file(s) you changed. `add` stages the current contents for the next commit; run it again if you make further edits. `commit` records staged changes **locally**

| Recall                               | Command                         |
| ------------------------------------ | ------------------------------- |
| Changed, staged, and untracked files | `git status`                    |
| Stage selected files                 | `git add analysis.py README.md` |
| Commit added changes                 | `git commit -m "some message"`  |
| Recent commits                       | `git log --oneline`             |
Press **q** to leave the `git log` interface.

### Keep generated files out of Git

Create a file named `.gitignore` in the project folder:
Then indicate what files should not be tracked by `git`, for instance:

```gitignore
**/__pycache__/
**/*.egg-info
.vscode/
.venv/
```

`**/__pycache__/` means "any folder named `__pycache__` present anywhere in the repository."
`*.egg-info` means "any file that has the `.egg-info` filetype, regardless of its name."

Commit the `.gitignore` itself to git. Keep source code, notebooks and environment specifications in Git. `.gitignore` does not remove files already tracked by Git. [Tracking and ignoring files](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)

#### A typical Exercises folder
```zsh
Assignment1/
	data/
		some_data_used_in_exercises.txt
		...			
	some_notebook.ipynb
	some_file.py
	.git/
	.gitignore
```
*When you .zip the folder and hand it in, your TA can read your Git commit history. Make sure to commit often and describe what you conceptually changed/added to your repository in the commit messages.*

## 5. Everyday workflow - with GitHub (Relevant for assignments 3 + 4)

### Publish a new local project to GitHub - once

Go to [GitHub](https://github.com/) and make an account. 

1. Create a GitHub repository. Leave **README, license and .gitignore initialization unchecked** so the remote starts empty.
2. Click the **`<> Code`** menu in the top right and copy the HTTPS URL string.
3. In your local project folder, run the following command in the VS Code terminal and replace `REPOSITORY_URL` below with the HTTPS URL from your GitHub:

```zsh
git remote add origin REPOSITORY_URL
git push -u origin main
```

GitHub may open a browser and ask you to sign into your account.
Verify that the remote is set up by running:

```zsh
git remote -v
# origin https://github.com/username/repository.git (fetch)
# origin https://github.com/username/repository.git (push)
```

### Synchronizing the local and remote repositories

Now that your project has a copy in the cloud you need to update the changes you commit locally. This doesn't have to happen after every single commit. To make your locally committed changes appear on GitHub use the `push` command:

```zsh
git push
```

If you have multiple people or machines pushing to the same GitHub account and want the online changes to appear on your local machine, use the `pull` command: 

```zsh
git pull
```

This is also handy if you cloned someone else's work and want to have the latest update on your local machine.
### Cloning an existing GitHub repository

If you want to make a copy of a repository from GitHub on your local machine, simply navigate to the desired location in the VS Code terminal and run:

```zsh
git clone REPOSITORY_URL 
```

## Common fixes

| Problem                                    | Check                                                                                          |
| ------------------------------------------ | ---------------------------------------------------------------------------------------------- |
| `git` is not recognized / not found        | Restart the terminal and VS Code. On Windows, make sure to check the installer's PATH option.  |
| `not a git repository`                     | Use `pwd` and `cd` to enter the project folder.                                                |
| `nothing to commit` after editing          | Save the file, then check `git status` and stage the intended changes.                         |
| Push denied                                | Check `git remote -v`, your signed-in account, and write permission.                           |

 [Pull reference](https://git-scm.com/docs/git-pull) · [Git command reference](https://git-scm.com/docs) · [GitHub learning exercises](https://skills.github.com/)


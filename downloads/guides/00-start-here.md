# DatF — installation guide and setup checklist

As a part of the course you will create a fully functional programming setup that implements the core tools of best-practice python development - all in one place. No more Jupyter notebooks in the browser, no more separate applications or terminals for managing files, using Anaconda, or executing code.

This guide is intended to be followed from start to finish and we recommend re-installing tools like Anaconda or VS Code if you already have them.

## What each tool does

| Tool | Purpose | Cheat sheet |
| --- | --- | --- |
| Visual Studio Code - your editor | Manage files, edit code, run scripts and notebooks. A proper editor offers lots of helpful features that means way less switching back and forth between Jupyter, google, or LLMs | [VS Code](vscode/) |
| Terminal | Run commands and navigate folders. Lets you use Git and Anaconda without leaving your editor | [Terminal](terminal/) |
| Anaconda / Conda | Install Python libraries and manage environments | [Anaconda](anaconda/) |
| Git | Record changes, restore earlier versions of your work, collaborate, and share code. | [Git](git/) |

While the tools are the same, the exact setup differs slightly between operating systems - for instance **Windows users will use the _PowerShell_ terminal**, while **macOS users will use the _zsh_ terminal.** Follow the parts of the installation guide that matches your system.


## First-time setup — follow this order

1. **Install and configure [VS Code]({{ '/guides/vscode/' | relative_url }}).** Add Python and Jupyter notebook extensions and choose the terminal profile. **Using VS Code is mandatory for this course** even if you normally use a different editor. This ensures that you get the best help and feedback while teaching you a new skill.
2. **Review the [terminal page]({{ '/guides/terminal/' | relative_url }}).** Learn how to navigate your file-system using commands like `cd`, `ls`, `mkdir`, and get ready for interacting with Git and Anaconda.
3. **Install [Anaconda]({{ '/guides/anaconda/' | relative_url }}).** We recommend un- and re-installing Anaconda even if you already have it since its `base` environment have most likely been contaminated if you have ever installed packages like `numpy` or `matplotlib` using `pip install`. Confirm that you can create and activate different environments in the VS Code terminal window.
4. **Install [Git]({{ '/guides/git/' | relative_url }})** and confirm that it works in the VS Code terminal window.
5. **Run the checks below inside the VS Code terminal:**

## A normal working session

1. Open the relevant project folder in VS Code.
2. Open a terminal; run `conda activate datf`.
3. Check `git status`
4. Edit and save your work.
5. Review your changes, add the intended files to git and commit. (*Push when the project has a remote you can write to. See the [git workflow]({{ '/guides/git/' | relative_url }}).*)

## If something fails

Use the **Common fixes** table in the relevant sheet. 

Official resources: [Git](https://git-scm.com/doc) · [Anaconda overview](https://www.anaconda.com/docs/getting-started/main) · [VS Code Python tutorial](https://code.visualstudio.com/docs/python/python-tutorial) · [VS Code terminal](https://code.visualstudio.com/docs/terminal/basics)


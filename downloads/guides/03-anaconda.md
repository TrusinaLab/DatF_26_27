---
layout: default
title: Anaconda & Conda
permalink: /guides/anaconda/
---

[Guides home]({{ '/guides/' | relative_url }}) ·
[VS Code]({{ '/guides/vscode/' | relative_url }}) ·
[Terminal]({{ '/guides/terminal/' | relative_url }}) ·
[Anaconda]({{ '/guides/anaconda/' | relative_url }}) ·
[Git]({{ '/guides/git/' | relative_url }})

# Anaconda & Conda — setup and quick use

**Purpose:** install Python and packages, and keep each project's software in its own environment. **Anaconda Distribution** is the installer; **Conda** is the command you use in the terminal to manage environments. 

## What is an environment?

The output of your python scripts depends on two things:
1. The actual code you wrote
2. The libraries and packages your code depends on

When you for instance write `import numpy`, the exact version of numpy you get to use is the one present in your active environment. 

By now, you have probably installed libraries way back when you started doing lab work using something like `pip install numpy`. This is fine for small projects and lab work, but can cause issues once projects depend on more than a few standard libraries, or if you want scientific collaborators to be able to run and reproduce your work on their computers.

The fundamental problem that can arise, is that libraries change across versions. Suppose for instance that `scipy` uses `numpy` code but wrote it back when `numpy` was at version `2.1`. Now you want to use both in your script, but if you install the newest `numpy=2.4`, your `scipy` library could break. 

Conda solves this problem for you: you declare what packages you want and conda figures out what versions everything needs to have to be compatible. It also allows you to freeze versions such that programs you write now still run in 5 years when both python and library syntax will have changed. You can even share your environment with others so they can recreate the conditions as they were on your machine.

## 1. Install and connect your terminal — once

### For Windows: Windows PowerShell

1. Download the Windows installer from [Anaconda Distribution](https://www.anaconda.com/download/success?reg=skipped) and follow the installation wizard. 
   We will use default settings but be aware to:
	- Choose **Just Me**
	- keep **Create shortcuts** selected
	- leave **Add Anaconda3 to my PATH** unchecked.
2. We will not use the **Anaconda Navigator**
3. Open **Anaconda Prompt** from the Start menu - this is a new kind of terminal that we will use only this once. Run:

   ```text
   conda --version
   conda init powershell
   ```

4. Close Anaconda Prompt and open a **Windows PowerShell** in VS Code. Check:

   ```powershell
   conda --version
   ```

**IF PowerShell reports “running scripts is disabled”:** 
This is because Windows by default prohibits foreign scripts from running and thereby blocks Anaconda. To allow it, run this one-time command in your Windows PowerShell:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

Confirm the change if prompted, then close and reopen PowerShell. `conda --version` should now print your installed version.

### For macOS: zsh

1. Open **Apple menu → About This Mac** to identify your processor.
2. For **Apple Silicon**, download the **Apple silicon graphical installer** from [Anaconda Distribution](https://www.anaconda.com/download). For an **Intel Mac**, select a `MacOSX-x86_64.pkg` installer compatible with your macOS from the [official archive](https://repo.anaconda.com/archive/). Follow the [macOS installation guide](https://www.anaconda.com/docs/getting-started/anaconda/install/mac-gui-install); the graphical installer normally uses `/opt/anaconda3` as the target folder.
3. We will not use the **Anaconda Navigator**
4. Open **Terminal** and initialize zsh:

   ```zsh
   conda init zsh
   ```

**Trouble shooting:**
If `conda` is not found, use the actual installation path. Example for the graphical installer's default location:

   ```zsh
   /opt/anaconda3/bin/conda init zsh
   ```

If you instead used the terminal installer with its default home-folder location, use:

```zsh
~/anaconda3/bin/conda init zsh`.
```

**Intel Mac note:** Anaconda stopped producing new Intel Mac packages on 15 August 2025. Use an archived installer and check the course environment below. Optionally, see the [support announcement](https://www.anaconda.com/blog/intel-mac-package-support-deprecation).

## 2. Disable automatic `base` activation

Anaconda comes with an environment named `base` which is used as a starting point for any new environment. This is activated by default but you should **never** install packages into `base` - rather create new environments for specific purposes. To prevent accidental installation into `base` run the following commands once:

```shell
conda config --set auto_activate false
```

In order to run install new packages you know purposefully have to activate the environment you want to install into.

## 3. Create the course environment — once

Open a terminal in VS Code and run:

```text
conda create --name datf python=3.12 numpy scipy matplotlib ipykernel
conda activate datf
```

Review Conda's proposed installation and confirm when prompted. If Conda presents repository terms, read and respond to that prompt. Creation may take several minutes.

Check the result in your terminal by running the following commands one at a time:

```text
conda env list
python --version
python -c "import sys; print(sys.executable)"
python -c "import numpy, scipy, matplotlib; print('Packages OK')"
```

`datf` should have the active-environment marker `*`; the Python path should point into that environment. Its folder may be under Anaconda's installation or your user environment directory.

Your active conda environment is usually indicated in parentheses in front of your terminal input line. For instance:

```zsh
# no python environment is active
PS C:\Users\username> 

# base is activate - BAD! Installing packages now will polute base
(base) PS C:\Users\username>

# the datf environment is active
(datf) PS C:\Users\username>
```

Running python files in the terminal will use the active environment and the specific versions of packages like `numpy` and `scipy` that it contains.

## 4. Everyday commands

These commands work in both PowerShell and zsh.

| Task                                                  | Command                |
| ----------------------------------------------------- | ---------------------- |
| Activate the course environment                       | `conda activate datf`  |
| List environments; `*` marks the active one           | `conda env list`       |
| List all installed packages in the active environment | `conda list`           |
| Add a package, for example sympy                      | `conda install sympy`  |
| Run a saved .py script                                | `python analysis.py`   |
| Leave the active environment                          | `conda deactivate`     |
| Read command help                                     | `conda install --help` |

Activate `datf` before installing packages or running Python. An environment contains software; your scripts stay in your project folder. Changing folders with `cd` does not switch environments.

## 5. Common fixes

| Symptom | First thing to check |
| --- | --- |
| `conda` is not recognized                  | Repeat the shell initialization above; open a fresh terminal. On Windows, start from Anaconda Prompt. |
| `Run 'conda init' before 'conda activate'` | Initialize the terminal you are actually using, then reopen it.                                  |
| Works outside VS Code only                 | Check VS Code's shell profile, quit/reopen VS Code, and create a new terminal.                        |
| `ModuleNotFoundError`                      | Activate `datf`, check `sys.executable`, and select the same interpreter/kernel in VS Code.       |
| `EnvironmentNameNotFound`                  | Run `conda env list`; create the environment if it is absent.                              |

## Official references

- [Conda getting started](https://docs.conda.io/projects/conda/en/stable/user-guide/getting-started.html)
- [Managing environments](https://docs.conda.io/projects/conda/en/stable/user-guide/tasks/manage-environments.html)
- [Managing packages](https://docs.conda.io/projects/conda/en/stable/user-guide/tasks/manage-pkgs.html)
- [Shell initialization: `conda init`](https://docs.conda.io/projects/conda/en/stable/commands/init.html)

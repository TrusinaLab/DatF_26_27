# Terminal — setup and everyday commands

## 1. Open the right place to type

A **terminal** is the window in which you type commands. A **shell** interprets those commands: this course uses **Windows PowerShell** on Windows and **zsh** on macOS. Python is just another program that the shell can start.

You can start a new terminal in VS Code using **Terminal → New Terminal** in the top panel, or with the Command Palette using **Terminal: Create New Terminal.** *Optionally make it and other things you do often a keyboard shortcut.*

## 2. Find your way around

Commands act relative to the terminal's **current folder**, which can differ from the file open in the editor. The current folder is indicated by the path displayed on your terminal input line.

Here is a list of commands that reflect the common actions you now from navigating a file explorer with your cursor. Folder and filenames are just examples.

| Action                                                                                         | Windows PowerShell                            | macOS zsh                              |
| ---------------------------------------------------------------------------------------------- | --------------------------------------------- | -------------------------------------- |
| Show current folder                                                                            | `pwd`                                         | `pwd`                                  |
| List files and folders                                                                         | `ls`                                          | `ls`                                   |
| Include hidden items                                                                           | `Get-ChildItem -Force`                        | `ls -a`                                |
| Enter a folder inside your current colder                                                      | `cd Datf`                                     | `cd Datf`                              |
| Go up one folder                                                                               | `cd ..`                                       | `cd ..`                                |
| Go to your home folder                                                                         | `cd ~`                                        | `cd ~`                                 |
| Enter a folder with spaces in its name - we recommend avoiding spaces in folder and filenames. | `cd "Week 1"`                                 | `cd "Week 1"`                          |
| Create a folder inside your current folder                                                     | `mkdir assignment1`                           | `mkdir assignment1`                    |
| Clear the visible screen                                                                       | `clear`                                       | `clear`                                |
| Print the contents of a file                                                                   | `Get-Content analysis.py`                     | `cat analysis.py`                      |
| Copy a file                                                                                    | `Copy-Item analysis.py new_analysis.py`       | `cp analysis.py new_analysis.py`       |
| Rename or move a file                                                                          | `Move-Item exercises1.ipynb exercises2.ipynb` | `mv exercises1.ipynb exercises2.ipynb` |
| Remove a file                                                                                  | `Remove-Item analysis.py`                     | `rm analysis.py`                       |
| Create an empty file                                                                           | `New-Item analysis.py`                        | `touch analysis.py`                    |

`.` means “this folder”, `..` means “one folder up”, and `~` means your home folder. Quote paths containing spaces. A relative file path might be `.\results\plot.png` on Windows or `./results/plot.png` on macOS.

In Windows PowerShell, `pwd`, `ls`, and `cd` are short names for PowerShell commands. Their options are not necessarily the same as zsh options: for example, use `Get-ChildItem -Force`, not `ls -a`.

## 5. Small habits that save time

- **Tab:** complete a partially typed path; Use up and down arrows **↑ / ↓** to recall previous commands.
- **Ctrl+C:** interrupt a running program. On Mac, use **Control**, not Command.
- **Copy/paste:** On Windows **Ctrl+Shift+C / Ctrl+Shift+V**; on Mac, **Cmd+C / Cmd+V** works.
- **“File not found”:** check `pwd`, then `ls`, then the filename.
- **“Command not found” / “not recognized”:** reopen VS Code after installation and check the relevant setup sheet.

## Official references

- [VS Code terminal basics](https://code.visualstudio.com/docs/terminal/basics)
- [PowerShell: files and folders](https://learn.microsoft.com/en-us/powershell/scripting/samples/working-with-files-and-folders)
- [PowerShell aliases](https://learn.microsoft.com/en-us/powershell/scripting/learn/shell/using-aliases) · [New-Item](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/new-item?view=powershell-5.1) · [Get-Command](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.core/get-command?view=powershell-5.1)
- [Apple: terminal shells](https://support.apple.com/guide/terminal/change-the-default-shell-trml113/mac) · [Terminal keyboard shortcuts](https://support.apple.com/guide/terminal/trmlshtcts/mac)

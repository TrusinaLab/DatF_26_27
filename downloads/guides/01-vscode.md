# Visual Studio Code — setup and quick use

[All sheets](00-start-here.md) · [Git](04-git.md) · [Anaconda / Conda](03-anaconda.md) · [Terminal](02-terminal.md)

**Purpose:** edit your project, run Python and notebooks, and use Git and Conda - all in one application. Install Git and Anaconda using their sheets after the basic VS Code setup.

## 1. Install once

Download the **desktop application** from [Visual Studio Code](https://code.visualstudio.com/download).

| Windows                                                                                                                                                                                                                                                                                                                | macOS                                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Choose the **User Installer** (check if your system uses x64 or ARM64 in *'System Information'*). <br><br>Keep default settings in the installation setup but be sure to:<br><br>- **Keep** *Add to PATH* **enabled**<br><br>- When prompted for **GitHub Copilot CLI**, choose: *'Don't add the copilot command'*<br> | Choose the build for your Mac, open the download, and move **Visual Studio Code.app** into **Applications**. |
More info at: [Windows installation](https://code.visualstudio.com/docs/setup/windows) · [macOS installation](https://code.visualstudio.com/docs/setup/mac)

## 2. Add extensions

VS Code is a general purpose editor and comes installed as a blank canvas. Since we need support for Python and Jupyter Notebook files, we must install the following **Extensions**:

- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) — Python editing and execution.
- [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) — support for `.ipynb` notebooks.

In VS Code, open the **Command Palette**: **Ctrl+Shift+P** on Windows, **Cmd+Shift+P** on Mac. 

Then run the command: **Extensions: Install Extensions** to open the Extensions Marketplace - alternatively click the icon with four square boxes in the left panel. 

Search for and install the Python and Jupyter extensions published by **Microsoft**.

## 3. Disable AI code generation

For this course, we want to practice programming and develop a solid foundation for your future scientific work. We will therefore disable VS Code's built-in AI integrations for tools such as GitHub Copilot or OpenAI's Codex. 

**These can be powerful additions later on** that we encourage you to get familiar with along the road. 

However, to really benefit from these in a scientifically solid way, **it is essential that you learn to read, write, test, and understand code yourselves.** 

To disable the tools:
1. Open the Command Palette and enter **Preferences: Open User Settings**. (not JSON)
2. Search for **Disable AI Features** in the settings menu
3. Check the **Chat: Disable AI Features** box
4. Restart VS Code.

## 4. Choose the course terminal — once

### For Windows: Windows PowerShell

In the Command Palette, run: **Terminal: Select Default Profile** and choose **Windows PowerShell**, the built-in Windows version. If plain **PowerShell** is also listed, use **Windows PowerShell** specifically.
### For macOS: zsh

Nothing to configure - VS Code detects zsh as the macOS default.

### Both Windows and macOS: restart and terminal usage

Fully quit and reopen VS Code. Make a fresh terminal following: **Terminal → New Terminal**, either using the top panel menu or the Command Palette.

**Go through the [terminal sheet](02-terminal.md)** to learn basic terminal commands and then come back here.

### Exercise: set up folders for the course using the terminal

1. Navigate to your `home` directory
2. Print the content and compare the output with your usual file explorer
3. Create a new folder and name it - e.g. `DatF`. We recommend not using spaces in filenames
4. Change directory to your created folder
5. Print the content - it should be empty
6. Create a new folder inside `DatF` called `MandatoryProject`
7. Also create four additional folders; one for each assignment's exercises
8. Print the contents of `DatF` to verify that the folders were created:
```zsh
DatF/
	MandatoryProject/
	Exercises1/
	Exercises2/
	Exercises3/
	Exercises4/
```

The contents of `MandatoryProject` will evolve over the entire course while `ExercisesX` folders will contain your solutions to point-based exercises for each assignment. You hand in by *zipping* both `MandatoryProject` and `ExercistsX` separately and upload them to Absalon for your TA to review.

## 5. OPTIONAL: make VS Code your own

You can customize almost anything about how VS Code looks and behaves - either using extensions from the **Extensions Marketplace** or writing them yourself.

For instance, you can change the color theme by opening the Command Palette and typing **Preferences: Color Theme.** If you don't like the default options - search for and install new ones in the Marketplace; try for instance `Neon Shimmer` or `GitHub Theme`. You can similarly change the icons used for different filetypes, all the keyboard shortcuts, install better commentary helpers, and much more. 

Try it out!

## 6. Using Python environments

**Go through the [Anaconda sheet](03-anaconda.md),** then come back here to test out how it integrates with VS Code.

Open your `DatF` folder in VS Code using the Command Palette or **File > Open Folder...** Create two files: `test.py` and `test.ipynb` and paste the following little program into each of them:

```python
import sys
print(sys.executable)
```
#### Python files
Open `test.py`. 

VS Code uses environments in two ways for python files:
1. As an **Interpreter** that reads your code, checks for errors, wring syntax, etc.
2. For **Executing** a file.
These are separate functions that can use different environments. To select `datf` as the interpreter, go to the Command Palette and type **Python: Select Interpreter**. To run `test.py` in the `datf` environment, make sure that it is activated in the terminal, then run:

```zsh
# activate environment
conda activate datf

# run a python file
python test.py # or the path from your current folder to test.py
```

Our little program prints where the python environment we used to execute the code lives. You should see that it comes from the datf location: `...anaconda3/envs/datf/python.exe`; not `...anaconda3/python.exe` which is the base environment.
#### Jupyter Notebooks

Open `test.ipynb`

A Jupter Notebook also uses an environment to execute cells you write. Here, the role of the **Interpreter** and **Execution** is shared in the **Notebook Kernel**. It is indicated in the top right corner of your notebook where you can change it, or use the Command Palette: **Notebook: Select Notebook Kernel**.

Verify that the code runs and indeed uses `datf`.

## 7. Using Git

**Go through the [Git sheet](04-git.md),** to install the tool and learn basic commands.

## 8. Useful VS Code controls

| Action                                                                                                 | Windows                 | macOS                   |
| ------------------------------------------------------------------------------------------------------ | ----------------------- | ----------------------- |
| Command Palette; then search for actions (select interpreter, kernel, new terminal, color theme, etc.) | Ctrl+Shift+P            | Cmd+Shift+P             |
| Save file                                                                                              | Ctrl+S                  | Cmd+S                   |
| Comment/uncomment selected lines                                                                       | Ctrl+'                  | Cmd+'                   |
| Open terminal                                                                                          | Terminal → New Terminal | Terminal → New Terminal |
| Open a folder                                                                                          | File → Open Folder...   | File → Open Folder...   |
*(Every action is also searchable in the Command Palette)*

## Common fixes

| Symptom                                         | Fix                                                                                                  |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `conda` or `git` not found                      | Check the selected terminal profile and the corresponding installation sheet; fully restart VS Code. |
| Import works in terminal but fails in notebook  | Select the `datf` environment as the notebook kernel; restart that kernel.                           |
| Python command missing from the Command Palette | Check that Microsoft's Python extension is installed and enabled.                                    |
| PowerShell says scripts are disabled            | Use the conditional fix in the [Anaconda sheet](03-anaconda.md).                                     |


[Python tutorial](https://code.visualstudio.com/docs/python/python-tutorial) · [Terminal basics](https://code.visualstudio.com/docs/terminal/basics) · [Keyboard shortcuts](https://code.visualstudio.com/docs/configure/keybindings)

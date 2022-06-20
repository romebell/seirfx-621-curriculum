# VS Code

# Contents

# What is VS Code?

*VS Code* is a popular open-source text-editor maintained by Microsoft. It's very customizable and capable. VS Code's functionality can be extended using *extensions*, however, most useful features are built-in. To try it out, let's use VS Code to open and edit a file!

# Edit a File in VS Code

To edit a specific file in VS Code, we can simply type the filename after `code`.

Let's add an *alias* (shortcut) command that will change to your code directory by simply typing `repo`. We can do this by editing the hidden `.zshrc` file.

```bash
code ~/.zshrc
```

Add this line (preferably near the example aliases).

```
alias fx1026="cd ~/seirfx1026"
```

# Extensions

One of the most powerful features of VS Code is extensions. They allow us to add on additional features to VS Code that will increase our productivity. Here's some of the ones we recommend using:

- [Azure Databases](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-cosmosdb) - Browse and query your Azure databases both locally and in the cloud.
- [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments) - helps you create more human-friendly comments in your code.
- [Bracket Pair Colorizer 2](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer-2) - allows matching brackets to be identified with colors.
- [Color Info](https://marketplace.visualstudio.com/items?itemName=bierner.color-info) - provides quick information about CSS colors.
- [Debugger for Firefox](https://marketplace.visualstudio.com/items?itemName=firefox-devtools.vscode-firefox-debug) and [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome) - Debug web applications in the browser!
- [EJS Language Support](https://marketplace.visualstudio.com/items?itemName=DigitalBrainstem.javascript-ejs-support) - Syntax highlighting for EJS, JavaScript, and HTML tags. Includes JavaScript autocompletion.
- [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) - Integrates ESLint JavaScript into VS Code. See the documentation for more.
- [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) - Launch a development local Server with live reload feature for static & dynamic pages.
- [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare) - Enables you to collaboratively edit and debug with others in real time.
- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) - All you need for Markdown (keyboard shortcuts, table of contents, auto preview and more).
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) - Linting, Debugging (multi-threaded, remote), Intellisense, Jupyter Notebooks, code formatting, refactoring, unit tests, snippets, and more.
- [vscode-icons](https://marketplace.visualstudio.com/items?itemName=vscode-icons-team.vscode-icons) - A file and folder icon library. Supports thousands of different file and folder types.

## Themes

Developers love making their workspace their own - one way to do this is through VS Code themes. Here's a few from the marketplace that come highly recommended:

- [One Dark Pro](https://marketplace.visualstudio.com/items?itemName=zhuangtongfa.Material-theme)
- [One Dark Monokai](https://marketplace.visualstudio.com/items?itemName=azemoh.one-monokai)
- [Dracula](https://marketplace.visualstudio.com/items?itemName=dracula-theme.theme-dracula)
- [Material Theme](https://marketplace.visualstudio.com/items?itemName=Equinusocio.vsc-material-theme)
- [SynthWave '84](https://marketplace.visualstudio.com/items?itemName=RobbOwen.synthwave-vscode)

You can change your theme by pressing `Command ⌘` + `Shift` + `P` in macOS or `Ctrl` + `Shift` + `P` on Linux and Windows to open the command palette. With the control palette open type `theme` and select the **Preferences: Color Theme** option. From here select the theme you want to apply. Many themes come with VS Code by default, one of the best of which is the **High Contrast Theme**.

# Accessing the Command Line Interface in VS Code

We are able to start a terminal session from within VS Code! This is incredibly useful because it means we can stay in one application and do all our work instead of switching back and forth between VS Code and the Terminal applications. To do this use `Ctrl` + ``` (that is a backtick - this key is above your `Tab` key).

# Test Your Alias

Before we wrap up we should test the alias we made earlier! Close VS Code and the Terminal window. Then re-launch Terminal and type `fx1026` to check that it works!

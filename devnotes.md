# devnotes

## 2024-02-12 - Testing Textual apps

I started work on testing a [Textual](doc/python-textual.md) app as described on their [Testing](https://textual.textualize.io/guide/testing/) page.

It was necessary to install [pytest-asyncio](https://pypi.org/project/pytest-asyncio/) because the [run_test](https://textual.textualize.io/api/app/#textual.app.App.run_test) method is an async context manager. I also installed the [pytest-textual-snapshot](https://pypi.org/project/pytest-textual-snapshot/) plugin for pytest which provides [snapshot testing](https://textual.textualize.io/guide/testing/#snapshot-testing).


## 2024-02-07 - Toggle Copilot

**UPDATE 2025-04-23:** The command `github.copilot.toggleCopilot` was replaced by `github.copilot.completions.toggle`.

---

GitHub Copilot's suggestions can be helpful or distracting depending on the context. Sometimes it saves me a lot of time, other times it slows me down having to evaluate every suggestion (and I get tired of hitting `Esc`). I went looking to see if there was a way to quickly toggle it.

I found a post by Rach Smith, [quickly-toggle-copilot](https://rachsmith.com/quickly-toggle-copilot/), that described a solution using a vscode extension and a keybinding. In the comments on that post, Simon Boehm gave a simpler solution that does not require an extension. The command referenced in the comment was not available when the original post was written.

In Visual Studio Code, select `File` -> `Preferences` -> `Keyboard Shortcuts` (or `[Ctrl+K Ctrl+S]`).

Near the top-right of the *Keyboard Shortcuts* page there is a small button to *Open Keyboard Shortcuts (JSON)*.

That opens `keybindings.json` (user settings). I entered the following to use `[Ctrl+Shift+x]` as the toggle.

```json
  {
    "command": "github.copilot.completions.toggle",
    "key": "ctrl+shift+x"
  },
```

## 2024-01-31 - pipenv - pruning python_version

When getting started with a new tool, it's easy to miss important aspects of using the tool when the first steps down the happy path are fairly easy. I have been switching to using [pipenv](https://github.com/pypa/pipenv) for managing dependencies and virtual environments for Python projects.

If a project previously had a `requirements-dev.txt` like this:

```
pytest
ruff
```

And a `requirements.txt` (or `requirements.in`) like this:

```
pillow
```

The `pipenv install` command will create a `Pipfile` listing those dependencies, create a `Pipfile.lock` that holds the version details for the dependencies (and sub-dependencies), creates a virtual environment for the project, and installs the dependencies.

```bash
pipenv install pytest ruff --dev
pipenv install pillow
```

What I was not aware of is that, by default, `pipenv install` also adds a **required Python version** to the `Pipfile` when it creates a new one.

```toml
[requires]
python_version = "3.12"
```

The `python_version` is set based on the current version on the system, and is set to one specific version (not a minimum or range). If the repository is cloned onto another system, and `pipenv sync` is used to set up the environment and dependencies, it will fail if that specific Python version is not installed. That is not what I want.

It is okay to remove the `[requires] \ python_version` section.

After removing `python_version` run `pipenv lock` to update the `Pipfile.lock` file.

Reference:

- Pipfile - [general-notes-and-recommendations](https://pipenv.pypa.io/en/latest/pipfile.html#general-notes-and-recommendations)
- pipenv - [specifying-versions-of-python](https://pipenv.pypa.io/en/latest/specifiers.html?highlight=python_version#specifying-versions-of-python)

## 2024-01-29 - pipenv and just

Lately I have been switching to using `pipenv` to manage dependencies and virtual environments for Python projects. It pairs nicely with using `just` to run the commands in a per-project `Justfile`.

- [pipenv](https://pypi.org/project/pipenv/)

- [casey/just](https://github.com/casey/just) - Just a command runner

- Introduction - [Just Programmer Manual](https://just.systems/man/en/chapter_1.html)

I learned about **Just** from reading posts (and code) by [Simon Willison](https://github.com/simonw), such as this post on [Using just with Django](https://til.simonwillison.net/django/just-with-django).


## 2024-01-26 - pipx on Windows

I run Linux on my main PC where I do my Python projects. I had not yet tried running my [scapr](https://github.com/wmelvin/scapr) screen capture tool on Windows. I have been using `pipx` to install Python applications on Linux. The docs have instructions for installing [pipx on Windows](https://github.com/pypa/pipx#on-windows). One method is to use [scoop](https://scoop.sh/), which is new to me. 

I do have a PC with Windows 10, so I gave this a try:

Install scoop, per their instructions, in a *Windows PowerShell* (5.1) terminal:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

irm get.scoop.sh | iex
```

Use scoop to install pipx.

```powershell
scoop install pipx
pipx ensurepath
```

Use pipx to install scapr (it's on [PyPI](https://pypi.org/project/scapr/))

```powershell
pipx install scapr
```

After reopening the PowerShell terminal, I ran `scapr` and it captured screenshots with no problems. It works on Windows, but unfortunately it does not work well on Ubuntu with *Wayland* (but that's another story).

---

# devnotes

## 2024-01-31

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

## 2024-01-29

Lately I have been switching to using `pipenv` to manage dependencies and virtual environments for Python projects. It pairs nicely with using `just` to run the commands in a per-project `Justfile`.

- [pipenv](https://pypi.org/project/pipenv/)

- [casey/just](https://github.com/casey/just) - Just a command runner

- Introduction - [Just Programmer Manual](https://just.systems/man/en/chapter_1.html)

I learned about **Just** from reading posts (and code) by [Simon Willison](https://github.com/simonw), such as this post on [Using just with Django](https://til.simonwillison.net/django/just-with-django).


## 2024-01-26

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

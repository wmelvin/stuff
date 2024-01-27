# devnotes

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

After reopening the PowerShell terminal, I ran `scapr` and it captured screenshots with no problems. It works on windows, but unfortunately it does not work well on Ubuntu with *Wayland* (but that's another story).

---

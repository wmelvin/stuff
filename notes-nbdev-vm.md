# Try nbdev on a VM

Using a virtual machine, host name `xude`, running Xubuntu 20.04, and configured for doing temporary experiments. The VM is restored to a previous snapshot after an experiment is finished and any materials to keep have been moved elsewhere.

<sub>(2022-10-13)</sub>

Try using *pipx* to install packages (*pipx* is already installed on the VM).

    pipx upgrade-all

> Versions did not change after running 'pipx upgrade' for each package.

Start by installing *Jupyter notebook*.

    pipx install notebook

>   installed package notebook 6.4.12, installed using Python 3.8.10
    These apps are now globally available
    - jupyter-bundlerextension
    - jupyter-nbextension
    - jupyter-notebook
    - jupyter-serverextension
    done!

Try running Jupyter notebook server.

    jupyter-notebook

It worked.

Install nbdev.

    pipx install nbdev

>   pipx install nbdev
    installed package nbdev 2.3.7, installed using Python 3.8.10
    These apps are now globally available
    - nbdev_bump_version
    - nbdev_changelog
    - nbdev_clean
    - nbdev_conda
    - nbdev_create_config
    - nbdev_docs
    - nbdev_export
    - nbdev_filter
    - nbdev_fix
    - nbdev_help
    - nbdev_install
    - nbdev_install_hooks
    - nbdev_install_quarto
    - nbdev_merge
    - nbdev_migrate
    - nbdev_new
    - nbdev_prepare
    - nbdev_preview
    - nbdev_proc_nbs
    - nbdev_pypi
    - nbdev_readme
    - nbdev_release_both
    - nbdev_release_gh
    - nbdev_release_git
    - nbdev_sidebar
    - nbdev_test
    - nbdev_trust
    - nbdev_update
    done!

---

Create a SSH key on the VM.

[Generating a new SSH key and adding it to the ssh-agent - GitHub Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

    ssh-keygen -t ed25519 -C "<email_address>"

File: `/home/bill/.ssh/xude_ed25519`

Passphrase is stored in a password manager.

Add key to *ssh-agent*.

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/xude_ed25519
```

Add key to GitHub account.

[Adding a new SSH key to your GitHub account - GitHub Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)

[ ] Remove the key from GitHub after this experiment is done.

---

Create a new repository on GitHub named 'try-nbdev'. Clone the repository.

```bash
mkdir ~/git
cd ~/git
git clone git@github.com:wmelvin/try-nbdev.git
cd try-nbdev
```

    nbdev_new

>   /home/bill/.local/pipx/venvs/nbdev/lib/python3.8/site-packages/ghapi/core.py:101: UserWarning: Neither GITHUB_TOKEN nor GITHUB_JWT_TOKEN found: running as unauthenticated
    else: warn('Neither GITHUB_TOKEN nor GITHUB_JWT_TOKEN found: running as unauthenticated')
    repo = try-nbdev # Automatically inferred from git
    branch = main # Automatically inferred from git
    user = wmelvin # Automatically inferred from git
    ...
    description = Exploring nbdev by fast.ai. # Automatically inferred from git
    settings.ini created.
    /bin/sh: 1: quarto: not found"

See what was generated.

    tree

>   .
    ├── `LICENSE`
    ├── `MANIFEST.in`
    ├── `nbs`
    │   ├── `00_core.ipynb`
    │   ├── `index.ipynb`
    │   ├── `nbdev.yml`
    │   ├── `_quarto.yml`
    │   └── `styles.css`
    ├── `_proc`
    │   ├── `00_core.ipynb`
    │   ├── `index.ipynb`
    │   ├── `nbdev.yml`
    │   ├── `_quarto.yml`
    │   └── `styles.css`
    ├── `README.md`
    ├── `settings.ini`
    ├── `setup.py`
    └── `try_nbdev`
        ├── `core.py`
        ├── `__init__.py`
        └── `_modidx.py`

---

Install Quarto.

    nbdev_install_quarto

(Maybe this should have been done before `nbdev_new`.)

---

Configure name and email in git.

    git config --global user.email ".."
    git config --global user.name ".."

Push to GitHub (from `~/git/try-nbdev`).

    git add .
    git commit -m "Initial commit."
    git push

GitHub Action to *Deploy to GitHub Pages* failed.
Enable GitHub Pages for the repo: [nbdev - End-To-End Walkthrough](https://nbdev.fast.ai/tutorials/tutorial.html#enabling-github-pages).

---

    nbdev_install_hooks

    nbdev_export

    pip install -e '.[dev]'

    nbdev_preview

---

Renamed `00_core.ipynb` to `00_hello.ipynb`.
When running the code in the notebook there is an error:

>   ModuleNotFoundError                       Traceback (most recent call last)
Cell In [2], line 2
1 #| hide
----> 2 from nbdev.showdoc import *
ModuleNotFoundError: No module named 'nbdev'

This might be due to using *pipx* to install.
Try creating a `venv` and installing into that.

    python3 -m venv venv

    . venv/bin/activate

    pip install --upgrade pip setuptools

    echo "notebook" >> requirements.txt
    echo "nbdev" >> requirements.txt

    pip install -r requirements.txt

Open the notebook server.

    jupyter notebook

Open `00_hello.ipynb` and re-run the notebook.
No error.

Edit notebook content.

    nbdev_prepare

>   Success.
>   pandoc -o README.md
>     to: gfm+footnotes+tex_math_dollars-yaml_metadata_block
>     output-file: index.html
>     standalone: true
>     default-image-extension: png
>
>   metadata
>     description: Exploring nbdev by fast.ai.
>     title: try-nbdev
>
>   Output created: _docs/README.md


    pip install -e '.[dev]'

>   Obtaining file:///home/bill/git/try-nbdev
    Preparing metadata (setup.py) ... done
    Installing collected packages: try-nbdev
    Running setup.py develop for try-nbdev
    Successfully installed try-nbdev-0.0.1

Make more edits and push to GitHub.

    nbdev_prepare
    git status
    commit -am "Ran nbdev_prepare to update README."
    git push

View results on GitHub.

Repository: [wmelvin/try-nbdev: Exploring nbdev by fast.ai.](https://github.com/wmelvin/try-nbdev)

GitHub Pages: [try-nbdev](https://wmelvin.github.io/try-nbdev/)

Also check status of GitHub Actions in the *Actions* tab.

---

<sub>(2022-10-14)</sub>

Using **restored VM**, before installing nbdev.

Try cloning the repo from GitHub and running some parts of nbdev.

```bash
mkdir ~/git
cd ~/git
git clone https://github.com/wmelvin/try-nbdev.git
cd try-nbdev/
```
    
Create the Python virtual environment and install requirements,
which include nbdev and notebook (jupyter).

```bash
python3 -m venv venv
. venv/bin/activate
pip install --upgrade pip setuptools
pip install -r requirements.txt

git status
```
    
Git status shows nothing changed at this point (venv is in .gitignore).    

Try opening and modifying a notebook. 

    jupyter notebook

Run nbdev tools.

    nbdev_prepare
    nbdev_preview
    
Running `nbdev_preview` installed Quarto.

Ran `nbdev_install_hooks` in case those may not be set up locally by just cloning the repo. Did not read the docs to find out if that is necessary.

Not setting up SSH keys on this VM, and registering them, to push back to GitHub from this VM. I need to wrap up this experiment.

That's all for now.

---

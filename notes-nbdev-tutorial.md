# notes-nbdev-tutorial

## Notes from watching nbdev tutorial

[nbdev tutorial](https://www.youtube.com/watch?v=l7zS8Ld4_iA): zero to published project in 90 minutes (YouTube)

<sub>(Started watching 2022-10-10)</sub>

Start by creating a Git repository. GitHub was used in the tutorial.
The *Apache 2.0* license was selected.

Clone the repository to local work directory.

Install nbdev (was already installed in tutorial).
Can use *pip* to install: `pip install nbdev`

`nbdev_help` to list commands.

Commands take `-h` argument to list help for the command.

Run `nbdev_new` in repo dir.

Infers initial configuration from git.
Creates `settings.ini`.

Each notebook produces one module.

Comment in code cell defines how the cell is treated.
`#| hide` - hide this cell (not in docs).
`#| export` - export this cell.


`nbdev_export`

`pip install -e .`


`nbdev_preview` fires up Quarto web server.

`nbdev_test` runs local tests in notebook.

Jupyter: `%debug` in code cell runs interactive debugger.

"Golden rule" - Put *imports* in separate cells from other code.

Use back-ticks around a `module` name in a Markdown cell to generate a link to the module on GitHub.

Use `show_doc()` to put the documentation at a specific location.
[nbdev - showdoc](https://nbdev.fast.ai/api/showdoc.html#show_doc)

Before pushing to GitHub, use `nbdev_clean` to remove unnecessary metadata.

There are also *git hooks* available to do this automatically.

You can also use `nbdev_prepare` which runs `nbdev_export`, `nbdev_clean`, and `nbdev_test`.

In GitHub repo, **Settings** / **Pages**: Set **Branch** to `gh-pages`.

GitHub **Actions** tab: **pages-build-deployment** action / **deploy**
will show the **URL** for the deployed documentation.

Copy the URL to the **Website** field in the repository settings
("Edit repository details") dialog.

Also in that dialog, under **Include in the home page**, only the *Releases* box was checked.

`nbdev_docs` updates README.md to contain content from generated home (index) page. Run this before pushing to GitHub to update README.

Use `nbdev_pypi` to publish to PyPI.

> Think of nbdev as a *dialect* of Python.

The [fastai coding style](https://docs.fast.ai/dev/style.html) does not follow all of [PEP 8](https://peps.python.org/pep-0008/).


### Links

[nbdev](https://nbdev.fast.ai/): *Create delightful software with Jupyter Notebooks*

[nbdev - End-To-End Walkthrough](https://nbdev.fast.ai/tutorials/tutorial.html)

nbdev uses [Quarto](https://quarto.org/); [Quarto - Using Python](https://quarto.org/docs/computations/python.html)

The *cards* module created in the demo was based on examples in the book [Think Python 2e](https://greenteapress.com/wp/think-python-2e/) (Green Tea Press). Also here: [Think Python, 2nd Edition](https://learning.oreilly.com/library/view/think-python-2nd/9781491939406/) (learning.oreilly.com)

[fast.ai](https://github.com/fastai/)

[fastai/execnb](https://github.com/fastai/execnb): *Execute a jupyter notebook, fast, without needing jupyter*

[fastcore - Test](https://fastcore.fast.ai/test.html) (`test_eq`, `test_ne`, etc.)

Tutorial mentioned use of `__all__` in Python [Modules](https://docs.python.org/3/tutorial/modules.html#importing-from-a-package).

`@patch` - [fastcore - patch](https://fastcore.fast.ai/basics.html#patch)

Python [configparser](https://docs.python.org/3/library/configparser.html#configparser.BasicInterpolation) used for processing `settings.ini`.

[nbdev - config](https://nbdev.fast.ai/api/config.html)

#### Related

[nbdev - Blogging](https://nbdev.fast.ai/tutorials/blogging.html)

[Nbdev: A literate programming environment that democratizes software engineering best practices | The GitHub Blog](https://github.blog/2020-11-20-nbdev-a-literate-programming-environment-that-democratizes-software-engineering-best-practices/)

[How nbdev helps us structure our data science workflow in Jupyter Notebooks | by David de Meij | Overstory | Medium](https://medium.com/overstoryai/how-nbdev-helps-us-structure-our-data-science-workflow-in-jupyter-notebooks-9cf6081b051f)

[NBDev Minimum Library | Isaac’s Blog](https://isaac-flath.github.io/fastblog/nbdev/personalutils/2021/03/30/NbdevMinimum.html)

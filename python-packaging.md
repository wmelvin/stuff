# Python Packaging

## Tools

### setuptools

Project Summaries: [setuptools](https://packaging.python.org/en/latest/key_projects/#setuptools)

### Poetry

Project Summaries: [poetry](https://packaging.python.org/en/latest/key_projects/#poetry)

[Poetry - Python dependency management and packaging made easy](https://python-poetry.org/)

[Introduction | Documentation | Poetry - Python dependency management and packaging made easy](https://python-poetry.org/docs/)

### Flit

Project Summaries: [flit](https://packaging.python.org/en/latest/key_projects/#flit)

[pypa/flit: Simplified packaging of Python modules](https://github.com/pypa/flit)

[Flit 3.9.0 — Flit 3.9.0 documentation](https://flit.pypa.io/en/stable/)

### Hatch - Hatchling

Project Summaries: [hatch](https://packaging.python.org/en/latest/key_projects/#hatch)

[Hatch](https://hatch.pypa.io/latest/)

[hatchling](https://pypi.org/project/hatchling/)

### PDM

Project Summaries: [pdm](https://packaging.python.org/en/latest/key_projects/#pdm)

### Rye

[mitsuhiko/rye](https://github.com/mitsuhiko/rye) - An Experimental Package Management Solution for Python

Python Bytes Podcast - [Episode #334 Packaging Organizations](https://pythonbytes.fm/episodes/show/334/packaging-organizations)

Rye - [334: Packaging Organizations - YouTube](https://www.youtube.com/watch?v=kake2wOH6RM&amp;t=125s)

[A few notes on Rye | Simon Willison’s TILs](https://til.simonwillison.net/python/rye)

InfoWorld - Serdar Yegulalp ([Dev with Serdar](https://www.youtube.com/playlist?list=PLYaGSokOr0MNgQlbnq_qY7BJs9-TOAxHA)) - [How to use Rye, an experimental all-in-one Python project management tool - YouTube](https://www.youtube.com/watch?v=DhMTblDwtOM)

---

## Posts

[Switching to Hatch – Oliver Andrich](https://andrich.me/2023/08/switching-to-hatch/)

---

2023-11-04

Talk Python To Me Podcast: [Episode #436 - An Unbiased Evaluation of Environment and Packaging Tools](https://talkpython.fm/episodes/show/436/an-unbiased-evaluation-of-environment-and-packaging-tools) with [Anna-Lena Popkes](https://alpopkes.com/)

Her post: [An unbiased evaluation of environment management and packaging tools](https://alpopkes.com/posts/python/packaging_tools/)

Referred to:
- [pandas/pyproject.toml at main · pandas-dev/pandas](https://github.com/pandas-dev/pandas/blob/main/pyproject.toml)
- [pip documentation v23.3.1](https://pip.pypa.io/en/stable/)
- [Packaging PEPs | peps.python.org](https://peps.python.org/topic/packaging/)
- [PEP 660 – Editable installs for pyproject.toml based builds (wheel based) | peps.python.org](https://peps.python.org/pep-0660/)
- [PEP 621 – Storing project metadata in pyproject.toml | peps.python.org](https://peps.python.org/pep-0621/)

Pandas uses this package (I've seen it other places recently): [versioneer · PyPI](https://pypi.org/project/versioneer/)

---

**Simon Willison - only pyproject.toml**

[Python packages with pyproject.toml and nothing else | Simon Willison’s TILs](https://til.simonwillison.net/python/pyproject)
- Uses [setuptools](https://setuptools.pypa.io/en/latest/)
	- Setuptools - [Package Discovery and Namespace Packages](https://setuptools.pypa.io/en/latest/userguide/package_discovery.html#automatic-discovery)
- Uses [build · PyPI](https://pypi.org/project/build/)
- Not part of packaging, but mentioned [pluggy](https://pluggy.readthedocs.io/en/stable/) as used in some of his projects that have plugins.

Also linked [Freezing requirements with pip-tools | Simon Willison’s TILs](https://til.simonwillison.net/python/pip-tools) - [jazzband/pip-tools](https://github.com/jazzband/pip-tools)

---

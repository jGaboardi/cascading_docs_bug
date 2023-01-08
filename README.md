# cascading_refs_bug

This repo serves as a starting point to figure out what's causing the cascading references in `sphinx`.

## Problem Description

* When a rendered reference entry from within `docs_*/_static/references.bib` is one line long or less, the subsequent entery is indented. This cascades until an entry is longer than one line and then the indentation resets.

## Repo Setup

* `docs_sphinx_<MAJOR>-<MINOR>-<PATCH>/`
  * docs build with `sphinx==<MAJOR>.<MINOR>.<PATCH>`
* `environments/`
  * environment `cascading_ref_sphinx_<MAJOR>-<MINOR>-<PATCH>.yml` used for buidling docs in `docs_sphinx_<MAJOR>-<MINOR>-<PATCH>/`

## Troubleshooting

* There seems to have been a change between `sphinx==5.0.2` ([html](https://github.com/jGaboardi/cascading_refs_bug/blob/main/docs_sphinx_5-0-2/_build/html/references.html), [image](https://github.com/jGaboardi/cascading_refs_bug/blob/main/images/references_sphinx_5-0-2.png)) and `sphinx==5.1.0` ([html](https://github.com/jGaboardi/cascading_refs_bug/blob/main/docs_sphinx_5-1-0/_build/html/references.html), [image](https://github.com/jGaboardi/cascading_refs_bug/blob/main/images/references_sphinx_5-1-0.png)) that is causing the cascading reference entries, but I haven't been able isolate the reason.
* I have implemented a workaround (see [`pysal/spaghetti#688`](https://github.com/pysal/spaghetti/pull/688)), but it is not a solution for the problem.

## Linked Issues and PRs

* [pysal/spopt#303](https://github.com/pysal/spopt/issues/303)
* [pysal/spopt#309](https://github.com/pysal/spopt/pull/309)
* [pysal/spaghetti#688](https://github.com/pysal/spaghetti/pull/688)


## Commands
```
# sphinx=6.1.2
$ conda create -n cascading_ref_sphinx_6-1-2 python=3.11 nbsphinx numpydoc pandoc sphinxcontrib-bibtex sphinx_bootstrap_theme matplotlib sphinx=6.1.2
$ conda env export > cascading_ref_sphinx_6-1-2.yml

# sphinx=5.2.0
$ conda create -n cascading_ref_sphinx_5-2-0 python=3.11 nbsphinx numpydoc pandoc sphinxcontrib-bibtex sphinx_bootstrap_theme matplotlib sphinx=5.2.0
$ conda env export > cascading_ref_sphinx_5-2-0.yml

# sphinx=5.1.0
$ conda create -n cascading_ref_sphinx_5-1-0 python=3.11 nbsphinx numpydoc pandoc sphinxcontrib-bibtex sphinx_bootstrap_theme matplotlib sphinx=5.1.0
$ conda env export > cascading_ref_sphinx_5-1-0.yml

# sphinx=5.0.2
$ create -n cascading_ref_sphinx_5-0-2 python=3.11 nbsphinx numpydoc pandoc sphinxcontrib-bibtex sphinx_bootstrap_theme matplotlib sphinx=5.0.2
$ conda env export > cascading_ref_sphinx_5-0-2.yml

# sphinx=5.0.0
$ conda create -n cascading_ref_sphinx_5-0-0 python=3.11 nbsphinx numpydoc pandoc sphinxcontrib-bibtex sphinx_bootstrap_theme matplotlib sphinx=5.0.0
$ conda env export > cascading_ref_sphinx_5-0-0.yml

# sphinx=4.5.0
$ conda create -n cascading_ref_sphinx_4-5-0 python=3.11 nbsphinx numpydoc pandoc sphinxcontrib-bibtex sphinx_bootstrap_theme matplotlib sphinx=4.5.0
$ conda env export > cascading_ref_sphinx_4-5-0.yml
```

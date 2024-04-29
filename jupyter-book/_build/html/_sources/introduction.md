# Getting started

Start by installing your environment with conda:
```bash
conda env create -f environment.yml
conda activate notebook_collaboration
```

Take a look at the first tutorial in `src_notebooks/Tutorial0_Template.py`. As it is a pure python script, you
first need to enable jupytext to display it as a notebook:
* If you use `jupyter notebook`, run the following command `jupyter serverextension enable jupytext`
* If you use `jupyter lab` you have to right click "Open with -> notebook" to open the
  python scripts with the notebook interface.

In this first tutorial you will see how to use tags to generate the two versions of your notebooks:
- the student version in which answers are removed,
- the teacher version in which answers are kept.

# Workflow

This template allows team work on notebooks:
1. Collaborators work on the python scripts in `src_notebooks`, as different versions of `.ipynb` files cannot be easily merged with git.
2. Two notebooks are generated per python script for (student + teacher) by running `make` at the root of the repo.\*

If you want to add previously made `.ipynb` files, please convert them to `.py` before adding them to the repo:
```bash
jupytext path/to/notebook.ipynb --to py -o ./src_notebooks/notebook.py
```

To remove all the notebooks generated, you can run `make clean`.

\* If you run Windows and do not use WSL, then `make` does not work. Run `python .build\build_versions.py` instead.

# Jupyter book

A jupyter book can be built from the notebooks. To customize your notebook, consider updating the following files: 
- `_toc.yml` allows to choose which notebooks or markdown files should be included in the book,
- `_config.yml` contains meta-data about your book and your repository,
- `index.md` is the first page of your book. 

<div class="alert alert-block alert-info">
  <b>Colab launchers:</b> Jupyter book creates a button to directly launch .ipynb files on Colab. This works only if your repository is on GitHub (Gitlab is not supported yet).
</div>

## On Mac or Linux

At the root of the repository, execute the following code:
```bash
make
cd jupyter-book
make
```

<div class="alert alert-block alert-warning">
  <b>Execution:</b> Notebooks are not executed while building the book. If you want to have some outputs ready (for example the result of HTML cells), you have to execute them manually before running the second make in <code>jupyter-book</code>.
</div>

## On Windows

Windows cannot easily use Makefiles. You have to run the commands contained in the Makefiles yourself:
Starting at the root of the repository:
```
python3 .build/build_versions.py
cd jupyter-book
mkdir -p _build/.jupyter_cache
jupyter-book build .
```

<div class="alert alert-block alert-warning">
  <b>Execution:</b> Notebooks are not executed while building the book. If you want to have some outputs ready (for example the result of HTML cells), you have to execute them manually before running the second make in <code>jupyter-book</code>.
</div>



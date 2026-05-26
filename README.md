# Example Jupyter Notebook

A small demo notebook ([example-math.ipynb](example-math.ipynb)) showing NumPy, Pandas and Matplotlib in action. Use it to get a first feel for Jupyter notebooks.

## What you need

- **VSCode** with the [Jupyter extension](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) and the [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- **uv** (already installed on your machine)

## Setup (one time)

Open a terminal in this folder and run:

```powershell
uv sync
```

This reads [pyproject.toml](pyproject.toml) / `uv.lock`, downloads the right Python version, creates a `.venv/` next to the notebook, and installs every dependency (pandas, numpy, matplotlib, ipykernel). It is fully reproducible — everyone ends up with the same versions.

## Running the notebook

1. Open this folder in VSCode (`File → Open Folder…`).
2. Open [example-math.ipynb](example-math.ipynb).
3. In the top-right of the notebook editor, click **Select Kernel**.
4. Choose **Python Environments… → .venv (Python 3.14.0)**. VSCode remembers this choice per folder.
5. Click **Run All**, or step through cell-by-cell with `Shift+Enter`.

That's it — the 3D plot in the last cell should render inline.

## What is a notebook?

A `.ipynb` file is a sequence of **cells**. Each cell is either:

- **Code** — Python that runs in a persistent kernel (variables stay alive between cells).
- **Markdown** — formatted text, like the headings in this notebook.

You run cells out of order, tweak code, and immediately see results (numbers, tables, plots) right beneath the cell. It is the standard way data scientists explore data and prototype.

## Useful keyboard shortcuts (inside VSCode)

| Shortcut | What it does |
|---|---|
| `Shift + Enter` | Run current cell, move to next |
| `Ctrl + Enter` | Run current cell, stay put |
| `Esc` then `A` | Insert cell above |
| `Esc` then `B` | Insert cell below |
| `Esc` then `M` | Convert cell to Markdown |
| `Esc` then `Y` | Convert cell to Code |
| `Esc` then `D D` | Delete cell |

## Adding a library

If you want to experiment with another package (say `seaborn`):

```powershell
uv add seaborn
```

uv updates `pyproject.toml` and `uv.lock`, then installs it into `.venv/`. Restart the kernel in VSCode (the circular-arrow icon at the top of the notebook) and `import seaborn` will work.

## Troubleshooting

- **"No kernel selected" / wrong Python shown** — click the kernel picker again and pick the one ending in `.venv\Scripts\python.exe`.
- **`ModuleNotFoundError`** — you probably picked the wrong kernel, or you added a package without restarting the kernel. Re-run `uv sync` and restart.
- **Plots don't show** — make sure you ran the cell with `import matplotlib.pyplot as plt`; in VSCode plots render inline automatically, no `%matplotlib inline` needed.

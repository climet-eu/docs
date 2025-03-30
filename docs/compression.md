# Online Laboratory for Data Compression in Climate Science and Meteorology

Welcome to the **Online Laboratory for Data Compression in Climate Science and Meteorology**, [compression.lab.climet.eu](https://compression.lab.climet.eu)!

If you are familiar with [JupyterLab](https://jupyter.org/), you should feel right at home with the user interface of this lab. You can use the JupyterLab interface at [/lab](https://lab.climet.eu/latest/lab) and a REPL interface at [/repl](https://lab.climet.eu/latest/repl).

In fact, this laboratory is built using [JupyterLite](https://jupyterlite.readthedocs.io/en/stable/), "a JupyterLab distribution that runs entirely in [your] browser" by leveraging WebAssembly. In other words, while you typically need to install JupyterLab on your own machine or connect to a server that executes your code, JupyterLite runs installation-free in your webbrowser and allows your code, data, and information to stay entirely on your machine. To run Python code within your browser, JupyterLite uses [Pyodide](https://pyodide.org/en/stable/), "a Python distribution for the browser [...] based on WebAssembly".

While Pyodide already supports an extensive list of scientific Python packages, which we have contributed to, this laboratory comes with additional packages that are commonly used in the weather and climate science community, including (but not limited to) `metpy`, `cfgrib`, `earthkit`, and `xeofs`.


## Getting Started

To get started, click the blue `+` button in the top left to open a new launcher and create a new Python notebook from there. After the Python kernel has initialised, you can execute Python code in the cells of the notebook.

!!! tip

    While many Python packages can be `import`ed directly, additional pure Python packages can also be loaded by executing the `%pip install <PACKAGE>` magic inside a cell, after which the package can be imported.

!!! note

    The online laboratory has only been tested in recent Firefox and Chrome browsers. Some features may not (yet) be supported in Safari browsers.

!!! attention

    The online laboratory runs with the strict memory constraints of your web browser. It is therefore recommended to only open and execute one or two notebooks at a time. When a notebook is closed, the kernel will automatically shutdown to preserve resources.

    If the online lab runs out of memory, you can save your work, close the notebook, and try to restart it. If you are still running low on memory, you should first download a copy of your notebooks, then reload the notebook page, re-upload the notebook, and continue working on them.

    If you intend on executing memory intensive workloads, it is best to continue working on the notebooks locally instead. The online laboratory is primarily designed for initial exploration and for sharing codes in a reproducible environment.

!!! caution

    In the online laboratory, changes to notebooks and local files are only saved in your web browser's storage and not persisted to disk.

    Please download copies of any files that you don't want to loose.

    Your files from an old session will usually be kept if you close or refresh this page, unless your browser's storage for `lab.climet.eu` is cleared, e.g.

    - manually by clearing the browser's site data
    - automatically when too much data is stored
    - automatically when you close a private browsing context
    - if you have setup your browser to clear site data, e.g. when the browser is closed


## Overview of the provided notebooks

The **Online Laboratory for Data Compression** comes with several Jupyter notebook examples to

1. introduce you to its functionality
2. showcase different compression methods on various weather and climate datasets
3. allow you to easily and quickly test out compression on *your* data

The following is an overview of all notebooks:

- [`01-intro.ipynb`](https://compression.lab.climet.eu/v0.2/01-intro.ipynb): First introduction to the online laboratory, data loading, compression, and visualisation
- [`02-data-sources/`](https://compression.lab.climet.eu/v0.2/02-data-sources/README.md): Small examples on how to open datasets from different sources
    - [`01-local.ipynb`](https://compression.lab.climet.eu/v0.2/02-data-sources/01-local.ipynb): open a large local read-only dataset by mounting it into the online lab
    - [`02-remote.ipynb`](https://compression.lab.climet.eu/v0.2/02-data-sources/02-remote.ipynb): open large remote datasets using `fsspec`, `kerchunk`, and `zarr`
    - [`03-cdsapi.ipynb`](https://compression.lab.climet.eu/v0.2/02-data-sources/03-cdsapi.ipynb): download small datasets from the Climate Data Store using the `cdsapi`
    - [`04-ecmwfapi.ipynb`](https://compression.lab.climet.eu/v0.2/02-data-sources/04-ecmwfapi.ipynb): download small datasets from the ECMWF Archive using the `ecmwfapi`
- [`03-examples/`](https://compression.lab.climet.eu/v0.2/03-examples/README.md): Longer walkthrough examples that apply and evaluate data compression on different variables
    - [`01-compressors.ipynb`](https://compression.lab.climet.eu/v0.2/03-examples/01-compressors.ipynb): comparison of different compressors on a small temperature and specific humidity dataset
- [`04-example-datasets/`](https://compression.lab.climet.eu/v0.2/04-example-datasets/README.md): Example datasets and access via an S3 bucket
    - [`01-hplp.ipynb`](https://compression.lab.climet.eu/v0.2/04-example-datasets/01-hplp.ipynb): open hplp-experiment dataset from the ECMWF S3 bucket
    - [`02-OpenIFS.ipynb`](https://compression.lab.climet.eu/v0.2/04-example-datasets/02-OpenIFS.ipynb): open OpenIFS-experiment dataset from the ECMWF S3 bucket
    - [`03-NextGEMS.ipynb`](https://compression.lab.climet.eu/v0.2/04-example-datasets/03-NextGEMS.ipynb): open NextGEMS-experiment dataset from the ECMWF S3 bucket
    - [`04-ICONXPP.ipynb`](https://compression.lab.climet.eu/v0.2/04-example-datasets/04-ICONXPP.ipynb): open ICON-XPP-experiment dataset from the ECMWF S3 bucket


## Getting Help and Contributing

This laboratory is being developed at <https://github.com/climet-eu/lab> and <https://github.com/climet-eu/compression-lab-notebooks>. If you come across a bug or would like to suggest a new feature or support for an additional Python package, please submit an issue at <https://github.com/climet-eu/lab/issues/> or <https://github.com/climet-eu/compression-lab-notebooks/issues>.


## License

Licensed under the CC BY 4.0 license (<https://creativecommons.org/licenses/by/4.0/>).


## Funding

The Online Laboratory for Data Compression in Climate Science and Meteorology has been developed as part of [ESiWACE3](https://www.esiwace.eu), the third phase of the Centre of Excellence in Simulation of Weather and Climate in Europe.

Funded by the European Union. This work has received funding from the European High Performance Computing Joint Undertaking (JU) under grant agreement No 101093054.

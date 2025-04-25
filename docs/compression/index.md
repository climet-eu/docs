# Online Laboratory for Data Compression in Climate Science and Meteorology

Welcome to the documentation for the **Online Laboratory for Data Compression in Climate Science and Meteorology**, [compression.lab.climet.eu](https://compression.lab.climet.eu)!

Please first read about the [Online Laboratory for Climate Science and Meteorology][online-laboratory-for-climate-science-and-meteorology] to get familiar with the environment that the Online Laboratory for Data Compression is hosted in.

## Overview of the provided notebooks

The **Online Laboratory for Data Compression** comes with several Jupyter notebook examples to

1. introduce you to its functionality
2. showcase different compression methods on various weather and climate datasets
3. allow you to easily and quickly test out compression on *your* data

The following is an overview of all notebooks (clicking a link opens the specified file in the online compression laboratory):

- [`01-intro.ipynb`](https://compression.lab.climet.eu/v0.3/01-intro.ipynb): First introduction to the online laboratory, data loading, compression, and visualisation
- [`02-data-sources/`](https://compression.lab.climet.eu/v0.3/02-data-sources/README.md): Small examples on how to open datasets from different sources
    - [`01-local.ipynb`](https://compression.lab.climet.eu/v0.3/02-data-sources/01-local.ipynb): open a large local read-only dataset by mounting it into the online lab
    - [`02-remote.ipynb`](https://compression.lab.climet.eu/v0.3/02-data-sources/02-remote.ipynb): open large remote datasets using `fsspec`, `kerchunk`, and `zarr`
    - [`03-cdsapi.ipynb`](https://compression.lab.climet.eu/v0.3/02-data-sources/03-cdsapi.ipynb): download small datasets from the Climate Data Store using the `cdsapi`
    - [`04-ecmwfapi.ipynb`](https://compression.lab.climet.eu/v0.3/02-data-sources/04-ecmwfapi.ipynb): download small datasets from the ECMWF Archive using the `ecmwfapi`
- [`03-examples/`](https://compression.lab.climet.eu/v0.3/03-examples/README.md): Longer walkthrough examples that apply and evaluate data compression on different variables
    - [`01-compressors.ipynb`](https://compression.lab.climet.eu/v0.3/03-examples/01-compressors.ipynb): comparison of different compressors on a small temperature and specific humidity dataset
- [`04-example-datasets/`](https://compression.lab.climet.eu/v0.3/04-example-datasets/README.md): Example datasets and access via an S3 bucket
    - [`01-hplp.ipynb`](https://compression.lab.climet.eu/v0.3/04-example-datasets/01-hplp.ipynb): open hplp-experiment dataset from the ECMWF S3 bucket
    - [`02-OpenIFS.ipynb`](https://compression.lab.climet.eu/v0.3/04-example-datasets/02-OpenIFS.ipynb): open OpenIFS-experiment dataset from the ECMWF S3 bucket
    - [`03-NextGEMS.ipynb`](https://compression.lab.climet.eu/v0.3/04-example-datasets/03-NextGEMS.ipynb): open NextGEMS-experiment dataset from the ECMWF S3 bucket
    - [`04-ICONXPP.ipynb`](https://compression.lab.climet.eu/v0.3/04-example-datasets/04-ICONXPP.ipynb): open ICON-XPP-experiment dataset from the ECMWF S3 bucket


## Getting Help and Contributing

This laboratory is being developed at <https://github.com/climet-eu/lab> and <https://github.com/climet-eu/compression-lab-notebooks>. If you come across a bug or would like to suggest a new feature or support for an additional Python package, please submit an issue at <https://github.com/climet-eu/lab/issues/> or <https://github.com/climet-eu/compression-lab-notebooks/issues>.


## License

Licensed under the CC BY 4.0 license (<https://creativecommons.org/licenses/by/4.0/>).


## Funding

The Online Laboratory for Data Compression in Climate Science and Meteorology has been developed as part of [ESiWACE3](https://www.esiwace.eu), the third phase of the Centre of Excellence in Simulation of Weather and Climate in Europe.

Funded by the European Union. This work has received funding from the European High Performance Computing Joint Undertaking (JU) under grant agreement No 101093054.

# Customize the pre-installed Python packages

Starting from version v0.2.1, the online laboratory supports customizing the selection and versions of (pure-Python) packages that are pre-installed and can simply be `import`ed, i.e. the provided virtual environment (venv).

For simple use case, sharing a URL to the default virtual environment and adding

```py
%pip install my-package==1.0.0
import my_package
```

to your notebooks is the easiest solution.

However, if you are hosting custom demos or documentation in the online laboratory, you might wish to control which packages and versions are available. Creating a custom venv requires a bit of one-time setup:

1. Open a special configuration notebook in a laboratory version of your choice:

    <a href="../urls/gist/?org=juntyr&id=a7e5030f0c1d1a603bfc5c2979531bf6&path=my-pyodide-lock.ipynb" target="_blank">https://gist.github.com/juntyr/a7e5030f0c1d1a603bfc5c2979531bf6</a>

2. Follow the instructions inside the notebook to specify your package requirements, install them, and create a custom lockfile

3. Upload the custom lockfile to e.g. a GitHub Gist. The URL where the lockfile is available must be publicly accessible and support CORS[^1] requests.

4. Append the following search query to the online laboratory that you share (remember to include the quotation marks around the URL):

    `pyodideKernelLockFileURL="<custom-lockfile-url>"`

    e.g. <a href="https://lab.climet.eu/v0.2.1/lab/index.html?pyodideKernelLockFileURL=%22https://gist.githubusercontent.com/juntyr/a58f9b1ab35fb8dec85b016f74f969a5/raw/2d34fdae6bc513597260f1b45485d7ffb11e1804/my-pyodide-lock.json%22" target="_blank">https://lab.climet.eu/v0.2.1/lab/index.html?pyodideKernelLockFileURL="https://gist.githubusercontent.com/juntyr/a58f9b1ab35fb8dec85b016f74f969a5/raw/2d34fdae6bc513597260f1b45485d7ffb11e1804/my-pyodide-lock.json"</a> (in this example custom venv, you can `import humanize` which is not possible in the default venv)

5. Test your new custom venv by checking if your required packages can be imported and have the correct versions.

Please reach out by opening an issue at <https://github.com/climet-eu/lab/issues/> if you encounter an issue creating your custom environment, or if you need a package (version) that the online laboratory does not yet support.

[^1]: <https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS>

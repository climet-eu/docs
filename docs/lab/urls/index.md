The Online Laboratory for Climate Science and Meteorology, [lab.climet.eu](https://lab.climet.eu), supports the following special URL patterns for downloading git repositories into the lab during startup:

- `https://lab.climet.eu/`: opens the latest version of the lab
- `https://lab.climet.eu/<version>`: opens the specified version of the lab
- `https://lab.climet.eu/<version>/[github|gitlab]/<org>/<repo>/<branch>`: downloads the specified GitHub / GitLab repository in the specified version of the lab
- `https://lab.climet.eu/<version>/[github|gitlab]/<org>/<repo>/<branch>/*filepath`: downloads the specified GitHub / GitLab repository in the specified version of the lab and opens the file path
- `https://lab.climet.eu/<version>/gist/[github]/<org>/<gist>/*filepath`: downloads the specified GitHub gist file and opens it in the specified version of the lab
- `https://lab.climet.eu/<version>/raw/[github]/<org>/<repo>/<branch>/*filepath`: downloads the specified file from a GitHub repository's branch and opens it in the specified version of the lab
- `https://lab.climet.eu/<version>/raw/[github-tag]/<org>/<repo>/<tag>/*filepath`: downloads the specified file from a GitHub repository's tag and opens it in the specified version of the lab
- `https://lab.climet.eu/<version>/raw/http/*url`: downloads the file from the specified URL and opens it in the specified version of the lab

where

- `<version>` refers to one of the following published versions of the lab:
    - `latest`: the latest published version, currently `v0.2.1`
    - `v0.2`: the latest version of the 0.2.x release stream, currently `v0.2.1`
    - `v0.2.1`
    - `v0.2.0`
    - `v0.1`: the latest version of the 0.1.x release stream, currently `v0.1.0`
    - `v0.1.0`

    The online lab follows semantic versioning, i.e. breaking changes to the lab and the packages it provides are only made in breaking releases. To ensure that your code works in the laboratory as expected, you should use one of the *.x release streams, e.g. `v0.1` or `v0.2`.

- `<org>` refers to the organisation / user that owns a GitHub / GitLab repository
- `<repo>` refers to the name of the repository
- `<branch>` refers to the name of a branch in the repository
- `<tag>` refers to the name of a tag in the repository
- `<gist>` refers to the hash of a GitHub gist
- `*filepath` refers to a path, starting from the repository root, for a file that should be opened
- `*url` refers to the URL to a file that should be downloaded

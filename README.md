This is an example repository of a Python package with CI/CD to build and deploy pdoc API documentation and additional manually provided documentation for both [GitHub](#GitHub) and [GitLab](#GitLab).

The [pdoc documentation is here](https://pdoc.dev/docs/pdoc.html).

For the API documentation, types are taken from type hints, with docstrings being used for descriptive documentation.

There's an assumption that the root directory contains one Python package. There are more details on that in the [GitHub](#GitHub) and [GitLab](#GitLab) sections below.

To include other manually generated documentation content, add it to the `__init__py` as a top level docstring, and include other Markdown files from there using reStructuredText's .. include::. There's an example in the `__init__.py` in this project.
```


# GitHub

The following files are specific to GitHub CI/CD: `./.github/workflows/docs.yml`.

Under `Settings > Pages` for your repository on GitHub, set the build and deployment source to GitHub Actions.

This repository includes an example yaml file for the build/deploy action at `./.github/workflows/docs.yml`.

Note the pdoc command in there looks for a package under the root directory (a directory containing an `__init__.py`) and assumes there to be only one, so that the package name doesn't need to be specified. It triggers whenever the master branch is pushed to, but can be modified to, for example, only trigger when tags are pushed.

The resulting GitHub Pages URL is `https://<user or group>.github.io/<project name>/`.

# GitLab

The following files are specific to GitLab CI/CD: `./.gitlab-ci.yml, ./Dockerfile.pdoc-gitlab-ci`.

For your repository on GitLab, enable CI/CD under `Settings > General > Visibility, project features, permissions`.

This repository includes an example yaml file for the build/deploy action at `./.gitlab-ci.yml`. To be general, it assumes a simple shell executor. The building of the documentation is done in a Docker container built using `./Dockerfile.pdoc-gitlab-ci`. Note that the tags in there might be specific to the GitLab runners available when writing these instructions.

Note the pdoc command in there looks for a package under the root directory (a directory containing an `__init__.py`) and assumes there to be only one, so that the package name doesn't need to be specified. It triggers whenever the master branch is pushed to, but can be modified to, for example, only trigger when tags are pushed.

The resulting GitLab Pages URL is `https://<username or group>.gitlab.io/<project name>/`. (Obviously URLs are different for self hosted GitLabs. The URL can be found under `Deploy > Pages`, and the short (non-build) specific URL can be found by unchecking "Use unique domain" on that page.)
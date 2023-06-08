### Notebooks

This folder contains various reproducible and interactive Jupyter notebooks created for the project.
The notebook organizational structure is described in detail below.

* [`access_github_ci_data.ipynb`](access_github_ci_data.ipynb) - Notebook which collects historical test data like the test duration values from running workflows on Github using the GitHub API.

* [`pass_fail_likelihoods.ipynb`](pass_fail_likelihoods.ipynb) - Notebook which examines a set of tests and determines the likelihood of a test failing based on the distribution of the test runtimes.

* [`experimental`](experimental/test_distributions.ipynb) - This folder contains some of our previous experiments conducted to determine the optimal stopping point such as approximating distributions and finding goodness of fit.
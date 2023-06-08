# Optimal Stopping Point

The aim of this tool is to predict an optimal stopping point for CI tests based on their test duration (runtimes). We perform an initial data analysis as well as feature engineering on the CI test data. Furthermore, we also calculate the optimal stopping point by identifying the distribution of the test duration values for different CI tests and comparing the distributions between the passing and failing tests.

## AI4CI: AI for Continuous Integration

This tool is part of a wider project that we have been working on called [AI4CI](https://github.com/aicoe-aiops/ocp-ci-analysis). AIOps is a critical component of supporting any Open Hybrid Cloud infrastructure. As the systems we operate become larger and more complex, intelligent monitoring tools and response agents will become a necessity.

The problem that we are trying to address is that there is a need for automated monitoring, altering, AI driven analysis for operations and testing systems. Open source testing data originating from real world production systems is a rarity for public datasets. Also, we noticed a lack of AI driven metrics for open source community health. This brings us to the opportunity of leveraging datasets that are made available by running open source software and applications in production like openshift-ci, kubernetes, fedora and develop a collection of open source data science tools and AI models to collect and analyze the CI/CD data. Thus, enabling AI for CI. 

## Data Collection

We collect historical test data mainly the test duration values from running workflows on Github and store the data on s3 storage.

## Predicting the Optimal Stopping point

After performing initial data analysis, we predict the optimal stopping for a given test based on their test duration(runtimes). We have explored a few different approaches to determine the optimal stopping point for a given test:

* **Best Distribution** - In this approach we approximate the distributions of the test duration value and also check its goodness of fit for different tests. Based on the type of distribution identified, we calculate the probability of the test failing. Probability density plots are used to understand the data distribution for a continuous variable and the likelihood (or probability) of obtaining a range of values that the continuous variable can assume. We find an optimal stopping point for the test by finding the point where the probability of the test failing is greater than the probabilty of the test passing. You can find more details in our [notebook.](notebooks/experimental/test_distributions.ipynb)

* **Pass Fail Likelihood** - In this approach, we evaluate the trends of passing and failing tests and plot the likelihood of a test to pass or fail throughout the run duration of tests. We group the tests into durations of 10/30 second buckets and find the number of tests falling under each of the buckets. We then find the likelihood of the test failing. By default, we define the threshold as 75% after which the test is likely to fail. This threshold can be customized as per your liking. You can find more details in our [notebook.](notebooks/pass_fail_likelihoods.ipynb)

Once we have calculated the optimal stopping point values for tests, it can be used to stop long running tests from consuming the resources after a certain point and resolve the bottlenecks in CI/CD systems. It can help improve software development workflows and facilitate effective management of development resources.
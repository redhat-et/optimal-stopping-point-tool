# Optimal Stopping Point

The aim of this tool is to predict an optimal stopping point for CI tests based on their test duration (runtimes). We perform an initial data analysis as well as feature engineering on the CI test data. Furthermore, we also calculate the optimal stopping point by identifying the distribution of the test duration values for different CI tests and comparing the distributions between the passing and failing tests.

## Data Collection

We collect historical test data mainly the test duration values from running workflows on Github and store the data on s3 storage.

## Finding the Best Distribution

We then visualize the distribution of the test durations and based on the distribution type identified, we can find a point after which the test has a higher probability of failing. We approximate the distributions of the test duration value and also check its goodness of fit for different tests. Based on the type of distribution identified, we calculate the probability of the test failing.

We fetch data for all the passing and failed tests and find the distribution type for the test duration. This tracks the time it took for a test to complete its execution. We can visualize the distribution of the test duration, based on the distribution type identified, we can find top two distributions based on betterment of fit. Probability density plots are used to understand data distribution for a continuous variable and likelihood (or probability) of obtaining a range of values that the continuous variable can assume. The area under the curve contains the probabilities for the test duration values. In a test duration probability distribution function, the area under the curve from 0 to a given value represents the probability that the test_duration is less than or equal to that value.

## Predicting the Optimal Stopping point

After performing initial data analysis and calulating the probability to fail, we predict the optimal stopping for a given test based on their test duration(runtimes). We find the best distribution(s) for the given test, and find an optimal stopping point for the test by finding the point where the probability of the test failing is greater than the probabilty of the test passing.

Once we have calculated optimal stopping point values for tests, this can be used stop long running tests from consuming the resources after a certain point. This can help the engineering teams and managers better allocate their resources.

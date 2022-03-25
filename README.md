# Data Engineer / Scientist Take Home Test

### This assignment is designed to test your skills around data wrangling, cleaning, and visualization

### What is the data?

This is a time-series data set representing transactions that entered the Bitcoin mempool and the state of the Bitcoin network when the transaction was broadcasted. If and when the transaction was confirmed, an additional feature `conf` (UNIX timestamp) is also collected

### Questions and Instructions

Your solutions should be in the form of a python notebook or python program. Non-code questions can be answered in comments.

#### Data import and cleaning

<ol>
    <li>Pull down this repo. You might need to use <a href="https://git-lfs.github.com/">git lfs</a> to import the dataset found in `data/`</li>
    <li>Read data found in `data/raw_data.json` into a pandas dataframe</li>
    <li>Start by examining a few rows. What are the different features? </li>
    <li>Start by dropping some meta data fields: `hash, version, locktime, vsize`</li>
    <li>This is a timeseries dataset. Plot `mempooldate`. Is the plot as expected? If not, what is a possible cause for abnomalities</li>
    <li>If `mempooldate` has any issues how would you fix it? Apply your solution to the original dataframe </li>
    <li>Re-plot `mempooldate` after the solution is applied </li>
    <li>Convert `mempooldate` from unix timestamp to a python date time object. And apply your transformation to the whole dataframe </li>
    <li>Set `mempooldate` as the primary index for original dataframe </li>
    <li>Do all rows have a unique index? If not, how many rows have overlapping indecies <l/i>
    <li>Group each row by unique index. If two rows have the same index, take the mean of the all the column values. Apply this transformation to the original dataframe</li>
    <li>Resample data set at 15 seconnd intervals and forward fill when NaNs are created</li>
    <li>Lets say `txid` was sensative information (its not). Sanatize `txid` in such a way that the original data cannot be derived but with the original data when can verify the sanatized version is valid.</li>
    <li>Lastly remove outliers from the dataset. Anything with a zscore < 3</li>
    <li>Create copy of the original data frame and perform min/max normalization on each col</li>
</ol>

#### Data analysis

<ol>
    <li>Drop txid </li>
    <li>Use the dataframe from the section above to perform some analytics </li>
    <li>List the count, mean, std, min, 25%, 50%, 75% percentiles for each feature in the data set</li>
    <li>Plot every column over time</li>
    <li>Plot a violin char for each column</li>
    <li>Are there any strong (both negative or positive) correlations between features?</li>
    <li>Plot the distributions for each feature <li>
    <li>How many rows have a non-NaN value for `conf`?</li>
    <li>Create a new column called `confimationtime`. The value for this column should be `mempooldate` - `conf`. If `conf` is NaN leave, `confimationtime` leave the value as NaN</li>
    <li>Export the dataframe to parquet partitions</li>
    <li>What are some cloud ETL options to automate the transformation steps from above?</li>
    <li>What are some storage options before and after the ETL pipeline?</li>
    <li>How would you strucuture the data differently to make it more accessible and/or consumable by your etl process?</li>
</ol>

#### Nice to have

<ol>
    <li>Save each plot in a seperate dir `img/`</li>
    <li>Use a virtualenv and save dependencies in `requirments.txt`</li>
    <li>Provide instructions on how to install dependencies and run solutino</li>
    
</ol>

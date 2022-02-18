# Data Engineer / Scientist Take Home Test

### This assignment is designed to test your skills around data wrangling, cleaning , and visualization

### What is the data?

This is a timeseries data set repersenting transactions that entered the Bitcoin mempool and the state of the Bitcoin network when the transaction was broadcasted. If and when the transaction was confirmed, an additional feature `conf` (unix timestamp) is also collected

### Questions and Instructions

Your solutions should be in the form of a python notebook or python program. Non-code questions can be answered in comments.

#### Data import and cleaning

<ol>
    <li> Pull down this repo. You might need to use <a href="https://git-lfs.github.com/">git lfs</a> to import the dataset found in `data/`
    <li>Read data found in `data/raw_data.json` into a pandas dataframe</li>
    <li>Start by dropping some meta data fields: `hash, version, locktime, vsize`</li>
    <li>This is a timeseries so its important that time is linear. Plot `mempooldate`. Is the plot as expected? If not, what is a possible cause for abnomalities</li>
    <li>If `mempooldate` has any issues how would you fix it? Apply your solution to the original dataframe </li>
    <li> Re-plot `mempooldate` after the solution is applied </li>
    <li> Convert `mempooldate` from unix timestamp to a python date time object. And apply your transformation to the whole dataframe </li>
    <li> Set `mempooldate` as the primary index for original dataframe </li>
    <li> Do all rows have a unique index? If not, how many rows have overlapping indecies <l/i>
    <li> Group each row by unique index. If two rows have the same index, take the mean of the all the collumn values. Apply this transformation to the original dataframe</li>
    <li>Resample data set at 15 seconnd intervals and forward fill when NANs are created. <a href="https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.resample.html">Re-sample Pandas</a></li>
    <li>Lets say `txid` was sensative information (its not). Sanatize `txid` in such a way that the original data cannot be derived but with the original data when can verify the sanatized version is valid.</li>
    <li>Lastly remove outliers from the dataset. Anything with a zscore < 3</li>
    <li>Create copy of the original data frame and perform min/max normalization on each feature</li>
</ol>

#### Data Analyst

<ol>
    <li> Use the data frame from the section above to perform some analytics </li>
    <li>List the count, mean, std, min, 25%, 50%, 75% percentiles for each feature in the data set</li>
    <li> Plot `mempoolsize` over time </li>
    <li> Are there any strong (both negative or positive) correlations between features?</li>
    <li>Export the dataframe to parquet partitions</li>
    <li>How would you automated transfomration steps from above? </li>
    <li>What are some storage options before and after ETL?</li>
    <li>How would you strucuture the data differently to make it more accessible and/or consumable by your etl process.</li>
</ol>

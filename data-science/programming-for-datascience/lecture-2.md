# Lecture 2 for programming with python
Today it's about capstone project, along with rest of the topics

Capstone project is relation BSE (Bombay stock exchange) between Crude oil prices

BSE and NSE have price difference for less time, but if the time is large then there is an option of arbitrage.

Today we will be looking at **Time series plotting** also.

Expectations for the project:
* Relation between BSE and crude oil prices
* BSE &rarr; talks about economy etc
* try to find how oil prices effect the economy
* Finally we should be able to give a conclusion with description.

Broad tasks in project:
* Importing data
* Data cleaning
* Data manipulation
* Descriptive statistics
   - we need to do it by some time period.
* Visualization.

## Revision of matplotlib
```Python
fig, ax = plt.subplots() # Create a figure containing a single axes.
ax.plot([1, 2, 3, 4], [1, 4, 2, 3], marker = 'o' , color = 'red') # Plot some data on the axes. marker is for points.
ax.set_xlabel('X axis') # x axis label
ax.set_xlim([0, 6])
ax.set_title('chart')
ax.set_xscale('linear')
```

ax.plot() &rarr; it is for line plot (which does not mean linear)
* It can be quadratic, cubic, log, etc continuous line.
* ax.plot(label = 'linear') &rarr; label is for line not axis.

ax.legend() &rarr; adds legend

np.linspace(start, end, number-of-elements) &rarr; linear space

Pie chart creation:
* **ax.pie(sizes, explode, labels, autopct, shadow etc)** &rarr; to create pie chart
    - sizes &rarr; is for sizes of pieces.
    - labels &rarr; for labels of pieces.
    - autopct &rarr; to write the values in a particular format
    - shadow &rarr; true/false for giving shadow
* labels, sizes are in list of values.
* explode &rarr; to make a particular piece to move away.

Timeseries data &rarr; data that changes with time, time being independent factor.
* In terms of data frame we need our datetime should be indices.

```Python
filepath = r'https://img1.wsimg.com/blobby/go/8c96521b-7ee0-4579-b983-c9c9fac1057e/downloads/unemploymentrate_usa_timeseries.csv?ver=1594214439799' # for file
ts = pd.read_csv(filepath)
```
From this code we can see that we can obtain a file from an URL.

dataframe.info() &rarr; gives you information about the data frame
* like columns, type of that column, etc
* by using dataframe.info() we can find missing values.
    - non-null &rarr; means no missing.

Convertion of the date time mentioned in the file we have to convert it datetime data type

Todo this there are three ways:
* "parse_dates" parameter can be used in read_csv(parse_dates = [column])
    - read_csv('filepath', parse_dates = [])
    - parse_dates &rarr; converts the datestamp in string to datetime dtype.
    - Multiple column can be passed.

Matplotlib needs datetime type for dtype for plotting, and our dataframe's index should be our datestamp.


This week into data cleaning and processing

We use **Pandas library** for this data cleaning and processing.

**Pandas is built on top of Numpy, it adds labelling to different dimension arrays** (arrays can hold heterogenous elements)
* Series &rarr; Labelled 1D Numpy array
* DataFrame &rarr; Labelled 2D Numpy array
* Panel &rarr; Labelled 3D Numpy array

Stores data in tables mainly.

If you wanna know about anything in python use "?" to open the manual about that thing.

### Series Data Structure in Pandas
* Cross b/w list and dictionary
* Can create a series by passing a list or a dictionary or a Numpy array to pandas.Series(list/dictionary)
    - We create series usings pandas.Series(data = None, index = None, name = None, copy = None, fastpath = false) (default values)
    - List ex: pd.Series([1,2,3]).
    - Dictionary ex: pd.Series({'hey':3, 'hello': 4})
    - Numpy array ex: pd.Series(Numpy.array([1,2,3,4,5]))
    - When using random.randint we need to consider 1D array (for size)
    - We can get Series from Pandas DataFrames by accessing the columns and bringing them.

Special case for creating series with dictionary

```Python
sports = {'Archery': 'Bhutan',
          'Golf': 'Scotland',
          'Sumo': 'Japan',
          'Taekwondo': 'South Korea'}
s = pd.Series(sports, index=['Golf', 'Sumo', 'Hockey'])
s # output is Golf &rarr; Scotland, Sumo &rarr; Japan, Hockey &rarr; NaN (No arrows)
```
Here we can see while creating the series indices explicitly mentioned are considered in the series and not the keys in dictionary.

Now whatever index is mentioned for that if there is a value in the dictionary then we bring that particular value and if it's not present then we assign that index value to be "NaN"

Basically like filtering the dictionary.

**None and numpy.nan are different**
* None is a special python type specifing no value
* But NaN is "not a number" which is used when dealing with numerical arrays / numbers
    - NaN is something that we don't know so logically we can't assume that every NaN is the same.
    - Not every NaN are the same, so np.nan == np.nan will give you FALSE. (Type of NaN is float)
      * As **==** checks the type and value of the objects
      * **is** operator is used to check whether two references are pointing to **same object or not**. (checks via memory addresses)
* None and NaN are both single objects which can have multiple references.

To see our index array &rarr; seriesName.index, which gives numpy array of indices used for the elements

DataFrame consists of various Series data structures

When we don't mention any index explicity, the index and label are basically the same and the indices are created by an inbuilt function.

### Querying in Series data structure
As series are 1D arrays we can query data by the use of normal array indices or we can use the label that we have specified for an element.

iloc and loc are attributes not methods

There are two properties for query compared to normal way of indexing:
* **series.iloc[ num ]** &rarr; iloc stands for integer-location which is searching for element by the use of integer indices
* **series.loc[ label ]** &rarr; loc stands for location which searches for an element by the use of label.

Now instead of using "iloc" and "loc" we can directly mention the integer and label in square brackets "[]" like in the example
```Python
series_name[ integer ] # for getting element by integer (like array)
series_name[ label ] # for getting element by label (like dictionary)
```
But for the above method of querying there is an exception, as **series[ integer ]** doesn't actually invoke **series.iloc[ integer ]** when the indices are all integers. (type &rarr; pandas.indexes.numeric.Int64Index)
* This throws an error as pandas doesn't really know if your searching based on integer or label location

series[ integer ] seems to invoke series.iloc[ integer ] when atleast one label in index list is an object and not numeric. (type &rarr; pandas.indexes.base.Index)

**Use iloc and loc to minimize errors**

We can use loc to add new values into series and series can handle different types in index as well as in data values.

**Working with all the values present in series**
* Now pandas and numpy have this feature called vectorization, which allows our code to run much faster making use of parallel computing.
    - Ex: np.sum()
* Rather than iterating the series explicitly try to use inbuilt functions / features that use vectorization.
    - Taking sum of all elements in series, np.sum(iterator/series)
    - If we want to add, subtract, multiply or divide some value from all the elements in series we can use series += / -= / *= / /= which are much faster than iterating the series.
      * This is known as broadcasting, where we apply an operation to all the elements.
      * Ex: series += 2

series.head() &rarr; shows first few elements of a series

series.iteritems() &rarr; returns list label and value respectively

series.append(diff_series) &rarr; returns new series which is joining of the two series.

**Magic functions in jupyter notebooks**
* We use **%** to use or create magic functions
* Cellular functions &rarr; specific to a cell we use "%%"
* %% timeit &rarr; cellular function where it runs our code in a particular cell and gives average time of execution
    - %%timeit -n num_of_times_to_run

Until now we have seen that indices were unique, but it is possible to give different data values with same index. So if we query data with that label we get all the data values associated with that label.

### DataFrames in Pandas
As mentioned earlier they are just labelled 2D array. Now there is an index for every row and for every column.

We can also look at each column as a series where row labels act as labels of 1D array. So our data frame is just combination of several series where each series has it's own label (the column label)

Data frame axes:
* axis 0 (vertical) &rarr; for rows
* axis 1 (horizontal) &rarr; for columns

To identify an element uniquely we need two indices or two labels or one index and one label.

**Every row and column possible forms a series**

#### Creation of data frames
We can create individual series (columns) then create the data frame from those series

**Creating through series**:
* Create each series which have same set of labels
    - Now if I don't create series before hand and use arrays / list then the **column labels are by default integers**
* Now use pandas.DataFrame([list of series], index = []), now here index creates row labels and labels on the series become column names.
    - If index is None then by default we get integers as labels for rows.

#### Finding elements in data frames
In series we used iloc and loc for identifying an element, similarly in data frame we use **loc and iloc for identifying rows (effectively elements from different series)**

As loc and iloc as explicitly used for rows, we use only **indexing for identifying columns based only on labels**

dataframe.loc and dataframe.iloc return dataframes containing the requested elements

dataframe.loc and dataframe.iloc do take two parameters rowLabel, colLabel and integers respectively
* for multiple column selection, dataframe.loc[rowLabel, [col1, col2, ...]] and similarly for multiple rows

loc and iloc both support slicing
* Incase of integers its the same as in numpy arrays, first till end-1
* But in case of labels, start label to end label (end included)
    - Ex: temp['comp1':'comp3'] &rarr; all columns from 'comp1' to 'comp3' inclusive
* dataframe.loc[ label ] &rarr; returns a series, which is also a dataframe
* Here row labels can be non-unique and when we query for data using them we get multiple rows just like in a relational database.
* To query for a particular element we can use **dataframe.loc[ rowLabel, colLabel ]**
    - This is also valid dataframe.loc[rowL][colL] &rarr; find a certain element
      * Chaining? &rarr; basically combining two operations together, querying for data by using loc and also indexing for a particular column
      * Ex: dataframe.loc[ rowLabel ][ colLabel ]
      * **Chaining causes pandas to return copy of dataframe instead of view the original**
* We can use two consecutive indexing operator, like **df['col'][int] &rarr; 'col' is column label and int is index of a row**.

**All properties of numpy arrays are present in data frame and series**

Transpose is allowed

#### Droping / deleting data in data frames (same in series)
Drop function &rarr; you pass which row (Index val) or which column (column val) you wanna drop.
* dataframe.drop(labels=None, axis=0, index=None, columns=None, level=None, inplace=False, errors='raise')
* optional parameter inplace (bool value), axis (0 or 1)
* Returns a copy of the original data frame after deleting requested elements
* To not have a copy using "inplace" parameter doesn't create a copy and directly affects the data frame.

Copy method &rarr; dataframe.copy() just returns a copy of that data frame

del keyword &rarr;

Broadcasting a value to a certain row and column

### DataFrame indexing and Loading
Generally when we work on a data frame we tend to work on interested rows and columns, so this is where indexing comes into the picture but pandas indexing gives use the view of the data not copy
```Python
costs = df['costs'] # gives you a view of series 'costs'

costs += 2 # broadcasting, this will reflect "df" too

# safer side is to copy
costs = df['costs'].copy()

costs += 2 # will only reflect in costs series and not in the data frame
```

So basically pandas indexing to get a row(s) or columns(s) doesn't create copy explicitly but gives a view and this saves memory and is faster than creating a copy.

Now coming to loading, we have so far tried to create a data frame using lists, dictionaries, series etc where we assumed data was extracted from an external file.

Now we can use pandas functions to extract files
* pandas.read_csv() example is the way of calling a read function
* **pandas read functions** convert the data extracted to data frames, now you can control what are the column/row labels by additional parameters like index_col, skiprows etc.
* Different file formats have different read functions
   - Ex: read_csv() &rarr; is for reading csv files
   - read_excel() &rarr; is for reading excel files

**FYI**
* csv &rarr; comma-seperated values file.
* using ! we can apply shell commands
   - Anything after ! is sent to shell to execute
   - Ex: !cat file.txt in jupyter notebook invokes cat command

We will be using read_csv() for practice.

#### read_csv()
This is a pandas function to basically takes a csv file and returns a data frame.

This function has hell load of parameters but we will be using only selected few

The default data frame created uses indices for both columns and rows as labels, in case you wanna change this we need to play with other parameters.

So to change to the desired rows and columns we use:
* index_col (integer) &rarr; this parameter will tell read_csv to consider the dataframe columns from that column index.
    - Ex: read_csv(filepath, index_col = 1) &rarr; means that the data frame will have columns including and after the column with index 1 (second column).
* header (integer) &rarr; parameter to tell which row will serve as column indices.
* names &rarr; user provides column names externally as a parameter.
* engine &rarr; which parsing engine to use either C engine (faster) or python engine (more features)
* skiprows (integer) &rarr; tells how to many rows to skip from top and resultant row on top is used as column labels.
* nrows &rarr; to specify how many rows to read from the file.

Now we know that a data frame is ultimately an object so to keep track of row labels and colum label it has certain attributes for that.

So to change any column/row name we need to see in the list of column/row names.
* dataframe.column &rarr; for column labels
* dataframe.index &rarr; for row labels

### Querying a Data Frame
Boolean masking is where we consider a series / data frame of same size as the one with data and here elements are true / false only based on which values we want to see or filter.
* Corresponding elements with True value will have values passed from original data frame / series.
* Whichever elements are false will be shown as NaN in the final data frame / series.

Boolean masking is useful for querying specific data, they can be used to filter data where we can see whichever data is required.

**Q) Now how to write boolean masks and how to use them?**

How to write boolean masks:
* We can broadcast comparision operators onto the whole series or data frame.
* Or we project rows / columns and then broadcast an operator (comparision operator) which results in **corresponding series which has labels mapped to true / false based on the condition mentioned**
    - Ex: df['column1'] > 5 &rarr; returns a boolean mask which is obtained by applying the ">" operator to 'column1'
    - Corresponding elements will have true / false based on whether the condition is met or not, here if value is greater than 5 or not.
* **Whatever boolean mask we get is a copy of the original series / data frame**

**Applying boolean masks over our data frame, this can be done using:**
* where function &rarr; df.where( boolean condition ) returns the filtered series / data frame
    - Ex: df.where(df['col1'] >=5)
* indexing, overloads indexing operator ( [ boolean condition ] )
    - Ex: df [ df['col4'] > 6 ]

**Note!** boolean condition &rarr; boolean masks, df > / < .. any comparision operator.

**Dropping data that don't have values (NaN)**

We can use dropna() (dropping any values that are NaN). Default axis for dropna() is axis = 0 (which is top to bottom / through rows)
* Axis = 0 if any row has NaN element then that row is dropped (axis = 0 is default)
* Axis = 1 if any column has NaN element then that whole column is dropped

More interesting things about boolean masks:
* Two or more boolean masks with bit-wise operator results in a boolean mask
* Applying these operations is similar to boolean algebra.

Ex: df['col2'] > 3 | df['col3'] < 7 (| &rarr; bit-wise OR, & &rarr; bit-wise AND)

By the use of boolean masks we can create complex conditions with can filter data to our needs.

### Note !!!
When using multiple boolean masks / basically an expression **wrap** each boolean mask in () to avoid conflict in operator precedence.

Ex: df[ (df['col3'] > 5) & (df['col4'] < 7) ]

**Q) How to query a subset of elements from already filtered data frame by the use of boolean masks?**

Ans)
* Instead of a one line statement, we could copy it to another reference and then query the required element(s).
```Python
temp = df[ df['col1'] > 6 ]
print(temp['col4'])
```
* Other way is to get filtered data frame and then apply your query on it (similar chaining)
```Python
temp = df[ df['col1'] < 5 ][ 'col4' ] # idea is that operation happens from left to right
# so first we get the filtered array then we query the element required from that.
print(temp)
```

* We could query our data and then filter it to the final requirement too!!
```Python
temp = df['col4'][ df['col1'] < 5 ]
print(temp)
```
This example gives the same result as the above one

This means that we can query any other column/row based on a condition(s)

### Indexing DataFrames
**When you have an empty it's values will be NONE or NaN(if with numerical values)**

Apparently dataframe.index and dataframe.columns are immutable lists

**Promoting a column's values to index** (here old indices get destroyed so you need to copy them)

Promotion is done by set_index(column) &rarr; gives copy, to do it in place we have to use 'inplace = True' to not create a copy and change the main data frame.

For multilevel indexing we use set_index([columns]), this multilevel is done in order which they are mentioned

Resetting indices
We use reset_index() &rarr; removes the current index and converts it into a column and sets up default numeric indices.

Changing indices
* As index and columns are immutable you have to use special functions to make any changes.
* can use **dataframe.rename(columns={oldcol : newcol}, index={oldindex : new index})**
    - rename creates a copy of original data frame, we have to use inplace = True for change to reflect on the original.
* 

Multilevel indexing (similar to composite keys in DBMS)

Multilevel indexing is generally used in demographic data or wherever you want to structure it logically.

levels in multilevel indexing (hierarchical labelling) (same thing can be done for columns)
* Each column which has become an index is known as a level, the level's numerical value gradually increase from left to right.
    - Left most level is 0
* When we want to **query** values from multilevel indices we can use **loc** where we pass the multilevel indices as a **one / list of tuples in order of levels**
    - df.loc[ [(multilevel indices)], forColumns ], for using multilevel with columns
    - df.loc[ index1, index2 ] / df.loc[ (index1, index2) ] when we need only the row.

**Q) How to add new rows and columns in multilevel indexing?**
* Firstly it is not the same way as in single level indexing
* we can use **dataframe.append(other, ignore_index=False, verify_integrity=False)** &rarr; adds new rows from 'other' to original and returns appended data frame (original + new rows)
    - Other &rarr; DataFrame / Series / dictionary-like objects
    - So we try to use "name" parameter to align them to the multilevel indices.
      * But "name" parameter is used in data frame or series function not in append.

### Missing values
Pandas use None and NaN to show missing values.

Missing values are common during data cleaning activities.

**Dealing missing values while loading**

The built-in functions that read from delimited files (like csv) have a few ways to control missing values, like in **general na_values list indicates other strings that could indicate missing values**

If you want to turn off whitespace filtering, to maybe want whitespaces for some reason then we can use **na_filter**

**Dealing with missing values in data frame**

Sometimes missing values do have information in them, there are multiple ways to work with missing values, one of them using filling function.

Filling function:
* df.fillna(value = None, method = None, ...) helps filling up missing values. (na &rarr; not applicable)
    - "value" parameter is used for replacing all missing values by a single value.
    - "method" refers to which way must the filling of missing values occur
       * ffill &rarr; stands for forward filling, we fill previous cell's value to corresponding cell of next row (next below cell is filled)
       * bfill &rarr; backward filling, which is opposite of forward filling. (basically previous above cell is filled)
    - To be able to use these methods data must be **sorted**, so the filling can take please according to you

Sorting in pandas data frame can be done based on indices by use of sort_index() and we can also sort based on values.

We can deal with one column or multiple columns which have missing values by projecting them.

Statistical functions like calculating mean exclude missing values by default.
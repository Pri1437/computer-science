\# In week 3 we continue to explore pandas library

## Merging dataframes
As we have already considered that data frames are like tables in DBMS, so **merging** of data frames is similar to joining tables.

As we know two tables can be joined as:
* Outer join (union)
* Left join
* Right join
* Inner join (intersection)

In a similar fashion we use pandas merge() to merge two dataframes.

Merge(df1, df2, how = '', left_index, right_index, on, left_on, right_on, suffixes = ('_x', '_y')...):
* df1, df2 are data frames to be merged
* **How** parameter states what type of merge whether it is 'outer', 'left', 'right' and 'inner'.
    - Default value of how = 'inner'.
* left_index, right_index take boolean values which is whether they need to be merge about them or not.
* on &rarr; label or list of labels, where it takes keys to join the data frames on!. **So whatever is mentioned should be present in both the data frames**
    - On &rarr; like generalization of left_on and right_on.
* left_on &rarr; What columns from left data frame which will be used for joining. This can be a label or list of labels.
* right_on &rarr; What columns from right data frame which will be used for joining. This can be a label or list of labels.
* Suffixes &rarr; we add _x to left df and _y to right df column in case columns have same names.

## Idiomatic Pandas: Making Code Pandorable

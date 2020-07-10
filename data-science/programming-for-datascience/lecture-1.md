# Lecture 1 of programming for data science
Data visualization is very important to be able to make sense of the data.

We humans are comfortable with pie chart / bar graph than a table.

Today's lecture is on visualization:
* Matplotlib
* Seaborn (Scientific visualization)

Most used libraries for visualization:
* Matplotlib
* Seaborn (scientific visualization)
* Bokeh (interactive plotting, with alot of info)

Q) What is the difference between these libraries?

Q) When to use these different libraries?
* Matplotlib is simple and easy to use, basically when we start out in visualization
* Seaborn is used when we look into relations, scientific data, for categorical variable
* Bokeh is used when showing clients, when we want to change different features of the visualization basically for interactive visualization

The chart should be valid, the data and visual should be related.

## Matplotlib
importing conventionally
```Python
import matplotlib as mpl
import matplotlib.pyplot as plt

# you code
#

plt.show() # for showing our plot / chart
```
Parts in a chart/plot:
* Legends
* Axes
* Axes labels
* Label
* Annotation
* Scaling

We plot by part by part, code the chart part by part.

We can merge two charts in same frame or in two different frames.

Anatomy in a chart/plot:
* figure &rarr; your design area, like your frame. (basic element)
    - This is created first before plotting.
    - You can change the size of figure by the use of "figsize" parameter for figure().
      * plt.figure(figsize = ()) (in inches)
    - You can change background of figure, "facecolor"
      * plt.figure(facecolor = 'yellow')
    - 
* Axes &rarr; smaller boxes used for creating chart
    - We can create them along horizontal or vertical.
    - so axes are better known as **subplots**
    - A figure can be divided in rows and columns which can be used for subplots.
    - Numbering of subplots happen from **Top left** and numbering goes left to right then down.
    - A subplot can be referenced by (row, column, position)
      * 2,2,1 &rarr; 2 rows, 2 columns and we are looking at position 1.
    - **We use fig.add_subplot(xyz)** to add axes (subplot)
      * x &rarr; rows
      * y &rarr; columns
      * z &rarr; position
* Axis &rarr; contain numbers with scaling. This refers to your x and y axis
    - Default axis limits are 0 to 1.
    - we create axes first, axes.set() &rarr; to create the axis.
      * axes.set(xlim = [], ylim = [], title = '', xlabel = '', ylabel = '')
    - To change limits we use **xlim and ylim**
      * xlim = []
      * ylim = []
* Creating actual plots now:
    - We use different functions for different plots
    - ax.plot(x, y, color = '' , linewidth = width) (this is for line)
    - ax.scatter(x, y, color= [], marker = '')

Color:
* we can use RGB
* RGBA &rarr; red green blue and alpha (alpha is transparency)

Order of creating a plot, import library &rarr; figure &rarr; axes(subplot) &rarr; create axis/plot &rarr; plt.show()


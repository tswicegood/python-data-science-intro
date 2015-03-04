---
layout: page
title: Pandas, Digging Deeper
---

* Deaths by county (bar)
* Accidents over time (line)
* Number of people involved over time (histogram)
* Number of people involved by day (scatter)

Here, we'll read in our dataframe, filter it and do a few group bys, creating several dataframes for the visualizations. 

```
from datetime import datetime
newframe = pd.read_csv('smallertab.csv')
```

```
newframe.groupby('County Name')
```

```
##What county had the most accident deaths?
newframe.groupby('County Name').sum()
```

Let's deconstruct this a bit, because we're chaining a lot together at once here.
We start with our DataFrame object, called newframe. We then do .groupby(), passing it the name of the column we're aggregating on. This is similar to our old friend SQL and returns a DataFrameGroupBy object.
We can then run .sum() on it to add up the numeric columns for each county, which returns a table.

```
newframe.groupby('County Name').sum().iloc[:,1].order(ascending=False)
```
Let's slice out just the column we care about using .iloc[], which wants a two-item list. The first item is a slice of the rows. Since we want all rows, we'll use the standard notation of an empty colon. The second liste item is the columns we want, which is just column 2, or if you're counting from 0, as python does, column 1.

Finally, let's use .order to sort the resulting series and pass it the ascending keyword as False (it defaults to true) to get the largest figures at the top.

We'll assign that to a new dataframe variable that we'll use later to make a bar chart and move on for now.

```
countydeaths = newframe.groupby('County Name').sum().iloc[:,1].order(ascending=False)

```

Notice that your dates are strings and not actual date objects, so when you try to sort them, you get 01/01/2008, 01/01/2009, 01/01/2010, and so on. 

We need convert the date strings to actual Python dates

```
newframe['Crash Date']=newframe['Crash Date'].apply(lambda x: datetime.strptime(x, "%m/%d/%Y").date())
```

Now we can aggregate the crashes by date and assign this to a new variable containing the resulting dataframe, that we'll use later to make a line chart.

```
crashesbydate = newframe.groupby('Crash Date').count().iloc[:,0]
```


Let's create a people involved column, adding total killed and total injured. This works similarly to creating a new key in a Python dict.

```
newframe['Total Involved']=newframe['Total Killed']+newframe['Total Injured']
```

With that value, we can create a histogram later.

##Let's scatter plot the counties by total killed and pedestrians killed.

```
import matplotlib.pyplot as plt

countyframe = newframe.groupby('County Name').sum()
countyframe.plot(kind='scatter', x='Total Killed', y='Pedestrians Killed')
```

Now, let's move on to visualize our data.
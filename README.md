# PyBer Analysis Report
Pyber Ride-Share Analysis
## Background and Results
After a presentation depicting information about rides, fares, and city types, the next step was
creating a summary DataFrame of the key metrics for the ride-sharing data by city type. The deliverd 
data was merged and manipulated to produce a summary of the data for executives.
![](Summary_df.png)
![](Weekly_Fare_Total_line_graph.png)
### Purpose
This exercise is intended to visually explain the relationship between average fares and city types over 
a period of 4 months. Additionally, a summary is provided to show by City type: Total Drivers, Totals Rides,
Total Fares, Average Fare by Driver, and Average Fare by Rides.

### Technical Analysis 
The data was anaylized by utilizing functions like count(), index(), unique(), .dtypes, and describe(). Various
plots were made with the merged data to develop an understanding of the data metrics.

Data Sources:

city_data.csv
ride_data.csv
Software:

Pyton 3.7.6
Jupyter Notebook 6.0.3
Pandas 1.0.1
Numpy 1.18.1

## Challenges Encountered and Overcome
The biggest challenge was understanding that the merged data contained a column with the summed driver count 
per city.  When that column was merged into the ride data, the total driver count per city was included on 
every line of the merged dataframe.  Therefore, that column in the merged dataframe could not be summed by line.
To overcome this issue, it was necessary to go back to the original dataframe to get the sum of the driver count.
Then this number could be used in further calculations such as average.

### Challenges and Difficulties Encountered

* Programming
The most challenging part of this exercise was understanding indexes and knowing they can not be referened the 
same way a column is referenced. Initally, the index to a dataframe was created but it was saved to a variable
name so it was lost once the next cell was started. Once that was fixed, everything smoothly. 

* Data analysis
The difficulty with analysis was realizing that the index was not properly set to DateTimeIndex.  It was still
set to object. Also, working around the total driver count referenced above was a big holdup.  I've ended up 
with the correct result by using the original data and not the merged dataframe but I feel sure there is a more
elegant solution.

* Graphing, etc
Keeping straight the differences between the MATLIB and OO techniques was the biggest challenge.
   
### Technical Analyses Used
Creation of summary data as well as the Line Graph inticating total fares by city over time will
inform executives in future decision-making.

## Recommendations and Next Steps
Continue focusing on increasing rides especially in the Urban areas since that is where the fares are highest.
Gather information as it arrives and chart these weekly.  

### Recommendations for Future Analysis
A focus on low months to determine what triggers a drop in rides as well as fares.

### Additional Analysis 1

* Description of Approach
Merge two datasets into one dataframe.  Determine the Total rides, Total Fares, and Average Fare by ride.  
Use original city dataset to determine the total drivers and the Average Fare by driver.  Use this to
create a dataframe with summary data.


* Technical Steps
To gather the aggregates (count and mean) for the different data points, the groupby function must be used
to summarize the aggreated data. A dictionary must be created with each data point as the column.  The
variables containg the data are Series so the .value[] attribute must be used to get the desired number. 
To use the original city dataset, the city type must be explicitly referenced in the groupby.  

### Additional Analysis 2

* Description of Approach
With merged summary dataframe, create a new dataframe with just the ride date, the city type, and the fare.
Pivot the dataframe so the date is the index and the city types are the columns. Slice out a smaller date
range to examine and create a line plot with date as x-axis and Fare as the y-axis.

* Technical Steps
By pivoting the dataframe into a new dataframe with an index of date and columns of city type, the dataframe 
can be resampled to sum up the fares for each city type by date.  It is then easy to slice a small portion
of data by date to use in the line graph.

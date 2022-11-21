# global_warming
## Is Global Sea Ice Decreasing?
For this part of the analysis, we looked at data from The National Snow and Ice Data Center.  The data we used from NSIDC (https://nsidc.org/data/g02135/versions/3) was an Excel workbook containing four spreadsheets with monthly average sea ice extent and area in both the Northern and Southern Hemispheres from 11/1978 through 9/2022. Also included in the data was weighted average monthly extent and area for each year.  The unit of measurement for both the sea ice extent and area was in millions of square kilometers.

Since the original file was a workbook with 4 sheets, the data was then split into 4 separate csv files: 
  1. sea_ice_NH_extent.csv
  2. sea_ice_NH_area.csv
  3. sea_ice_SH_extent.csv
  4. sea_ice_SH_area.csv
   
Next, a Jupyter notebook with Python file (sea_ice.ipynb) was created to analyze the data.  The following steps were taken:
* All 4 csv files were uploaded individually and made into DataFrames using Pandas.
* 
* Each file was manipulated so that the index was the year and the second column was either "Sea Ice NH Area", "Sea Ice NH Extent", "Sea Ice SH Area", or "Sea Ice NH Extent. Below is a snapshot of the head of each DataFrame. 
  ![](Resources/4_df.jpg)
* Next, all 4 DataFrames were merged into one DataFrame as seen below:
![](Resources/merged_sea_ice.png)
* Two more columns were added which totaled the NH and SH area and extent, respectively. 
![](Resources/global_merged_sea_ice.png)
* JSON files were then exported for the future purpose of creating web visualizations in Plotly using Javascript. 
 
## Are Global Surface Temperatures Increasing?
The data used for this analysis was extracted from the Food and Agriculture Orangization of the United Nations (FAO) as the file "data\Annual_Surface_Temperature_Change.csv".  Data is separated by country and shows the mean temperature change with respect to a baseline climatology, corresponding to the period 1951–1980.  The global mean surface air temperature for 1951-1980 period was about 14°C (57°F), with an uncertainty of several tenths of a degree.


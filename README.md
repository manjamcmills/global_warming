# global_warming
## Is Global Sea Ice Decreasing?
For this part of the analysis, we looked at data from The National Snow and Ice Data Center.  The data we used from NSIDC (https://nsidc.org/data/g02135/versions/3) was an Excel workbook containing four spreadsheets with monthly average sea ice extent and area in both the Northern and Southern Hemipsheres from 11/1978 through 9/2022 . Also included in the data was weighted average monthly extent and area for each year.  The unit of measurement for both the sea ice extent and area was in millions of square kilometers.

Since the original file was a workbook with 4 sheets, the data was then split into 4 separate csv files: 
  1. sea_ice_NH_extent.csv
  2. sea_ice_NH_area.csv
  3. sea_ice_SH_extent.csv
  4. sea_ice_SH_area.csv
   
Next, a Jupyter notebook with Python file (sea_ice.ipynb) was created to analyze the data.  The follwoing steps were taken:
* All 4 csv files were uploaded individually and made into DataFrames using Pandas.
* Each file was maniuplated so that the index was the year and the second column was either "Sea Ice NH Area", "Sea Ice NH Extent", "Sea Ice SH Area", or "Sea Ice NH Extent. Below is a snapshoot of the head of each DataFrame. 
  ![](Resources/4_df.jpg)
* Next, all 4 DataFrames were merged into on DataFrame as seen below:
![](Resources/merged_sea_ice.png)
* Two more columns were added which totaled the NH and SH area and extent, respectively. 
![](Resources/global_merged_sea_ice.png)
* JSON files were then exported for the future purpose of creating web viuslations in Plotly using Javascript. 
  
* 

# Who’s next?: Extinction 🦕🦖🧌

**Introduction**

Global Climate change & its effects

- [x] Our team is passionate about science 👩‍🔬
 
 ➡️ We want to understand if global temperatures have changed within the last 20 years, and what temperatures are estimated to look like 20 years from today. We chose to focus on 4 different global measurements in our research:
 
1. Sea levels
2. Carbon emissions
3. Polar ice caps
4. Surface temperatures

While these four variables listed above are not an exhaustive list, we believe that the audience will better understand how these variables are interconnected as a starting point for raising awareness of this subject. 

Questions of curiosity include: *“Are global temperatures rising? Are they cooling? Is climate change happening in our lifetime? How can we help the planet?”*

➡️ In order to capture our full analysis, we’ve organized our process in 3 total phases. 
 
## Phase 1: Direction ##
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

Each of us chose a variable (from the list above) to focus on for data gathering, data cleaning, and data modeling (using python in jupyter notebook). We sifted through multiple kaggle.com data csv files to see if the data we were looking for existed publicly. 
We originally wanted to upload our data to a SQL database using PGAdmin because we thought that it’d be easier to retrieve all of the data sources.

Here's a screenshot of what our database began to look like at the beginning:


![Pg_admin-emissions](https://user-images.githubusercontent.com/106992995/204065212-011c2d25-7e3d-469a-a4a3-b3a01b614493.png)




![PG_admin databases](https://user-images.githubusercontent.com/106992995/204065214-7c429909-5ed7-4e9f-a310-5bfbe01f12ae.png)







After examining close to 30 different Kaggle datasets in jupyter notebook, we found that many datasets could not be used for the final analysis due to multiple reasons: column headers were too ambiguous, references were not available, missing row data. 
Kaggle was a great starting point, but ultimately, we used datasets from <https://climatedata.imf.org/>

Each of us used <https://climatedata.imf.org/> as the centralized point to find additional data sources from its reference page that could help support our 4 categories (Sea levels, Carbon emissions, Polar ice caps, Surface temperatures). 
Instead of using a SQL database for our analysis, we decided that loading the csv directly from a data folder and looking at the files in jupyter notebook (importing pandas and matplotlib) would be faster, easier to edit the column headers, and produce a quick visualization to see if we were going in the right direction was best. 

This process took about 1 week to complete and we decided to keep our data folder open in case we found additional data later on. 

*Summary Phase 1:*

> Cancel our SQL database direction
>> Keep all relevant climatedata.imf.org datasets
>>> Clean datasets in Python with pandas and matplotlib (visualizations as checkpoints)


 
## Phase 2: Methodology ##
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

In this phase, we gathered all final data sources and created a website to deploy our findings. Each category below outlines how we configured each data source using Python:

### **Sea Levels** ### 
🌊 🌊 🌊 🌊 🌊 🌊

Datasets from: IMF: Climate Change Indicators - Change in Mean Sea Levels (https://climatedata.imf.org/datasets/b84a7e25159b4c65ba62d3f82c605855_0/about)

The dataset consisted of monthly measurements of sea levels across all oceanic bodies. For our website, we focused on displaying the top 3 ocean bodies (Pacific ocean, Atlantic, and Indian Ocean). 

Csv file used for global Sea Level analysis: Change_in_Mean_Sea_Levels.csv

JSON files were then exported for the future purpose of creating web visualizations in Plotly using Javascript. 

-------------------
### **Carbon emissions** ###
🫧 🫧 🫧 🫧 🫧 🫧 🫧

Datasets from: IMF: Climate Change Indicators - Atmospheric CO₂ Concentrations (https://climatedata.imf.org/datasets/9c3764c0efcc4c71934ab3988f219e0e_0/about). 
The data consisted of Monthly atmospheric carbon dioxide concentrations measured by CO₂ Parts per million and CO₂ percent concentration units from years 1958 - 2022. The dataset was cleaned by creating two data frames using pandas (CO₂ Parts per million df and CO₂ percent concentration df). The problem with this first initial dataset was that the country codes were missing, therefore, we could not map out and or trace back CO₂ concentration by region without the ISO dataset. To fix this, we used the global ISO tags and added an additional column (ISO Standards Tag Set: https://github.com/lukes/ISO-3166-Countries-with-Regional-Codes/blob/master/all/all.csv ), to organize the data based on CO₂ PPM concentrations by region. 
Csv file used for global CO₂  analysis: CO2_emission_by_countries.csv
* JSON files were then exported for the future purpose of creating web visualizations in Plotly using Javascript. 

-------------------
### **Polar Ice caps (Sea Ice)** ###
🧊 🧊 🧊 🧊 🧊 🧊 
 

Datasets from: The National Snow and Ice Data Center.  The data we used from NSIDC (https://nsidc.org/data/g02135/versions/3) was an Excel workbook containing four spreadsheets with monthly average sea ice extent and area in both the Northern and Southern Hemispheres from 11/1978 through 9/2022. Weighted average monthly extent and Area for each year were additional columns.  The unit of measurement for both the sea ice extent and area was in millions of square kilometers.

Since the original file was a workbook with 4 sheets, the data was then split into 4 separate csv files: 
  1. sea_ice_NH_extent.csv
  2. sea_ice_NH_area.csv
  3. sea_ice_SH_extent.csv
  4. sea_ice_SH_area.csv

The Sea Ice analysis took place in Jupyter notebook: sea_ice.ipynb 
The following steps were taken:
All 4 csv files were uploaded individually and made into DataFrames using Pandas
Each file was manipulated so that the index was the year and the second column was either "Sea Ice NH Area", "Sea Ice NH Extent", "Sea Ice SH Area", or "Sea Ice NH Extent. Below is a snapshot of the head of each DataFrame. 

![NH Sea Ice](https://user-images.githubusercontent.com/106992995/204066989-2a6eb941-2528-47c8-b453-fc19b57f6d56.jpeg)


Next, all 4 DataFrames were merged into one DataFrame as seen below: 

![merged_sea_ice](https://user-images.githubusercontent.com/106992995/204067031-eedc31b2-b5fd-4cc9-b55d-8f07b2ad798f.png)


Two more columns were added which totaled the NH and SH area and extent, respectively. 
JSON files were then exported for the future purpose of creating web visualizations in Plotly using Javascript

![global_merged_sea_ice](https://user-images.githubusercontent.com/106992995/204067015-05795382-b6b8-428f-8146-a704ddfb4fc3.png)


-------------------
### **Surface temperatures** ###
🌎 ☀️ 🌍 🌤 🌏 ⛅️ 

Datasets from: Food and Agriculture Organization of the United Nations (FAO) as the file "data\Annual_Surface_Temperature_Change.csv".  Data is separated by country and shows the mean temperature change with respect to a baseline climatology, corresponding to the period 1951–1980.  The global mean surface air temperature for 1951-1980 period was about 14°C (57°F), with an uncertainty of several tenths of a degree.

The Surface temperature analysis took place in Jupyter notebook: temperature.ipynb 

The following steps were taken:

The original csv file "data/Annual_Surface_Temperature_Change.csv" was uploaded and turned into a DataFrame using Pandas.  There were originally 227 rows (countries) and 71 columns (data).

![temp_orig](https://user-images.githubusercontent.com/106992995/204067470-4eee80b4-6df3-4a0c-ac03-684ef69b4c2b.png)


The data was then cleaned and filtered so that only the Country name, Country code, and temperature change by year was shown. 
![temp_cleaned](https://user-images.githubusercontent.com/106992995/204067480-6816195c-37e2-4a22-9aa4-e6dc41c17acd.png)



Next, another file was loaded ("data/countryContinent.csv") which gave more information about each country like the Continent and sub_region it belonged to.  This was turned into a data frame and later merged with our original dataframe.
After merging the dataframes, all NaN values were dropped.  We were left with 158 countries, their country code, sub_regionb, and temperature data from 1961-2021.


After this process, the data was again exported to JSON files for the future purpose of creating web visualizations in Plotly using Javascript. 

![temp_merged](https://user-images.githubusercontent.com/106992995/204067503-423263f4-1e2b-4169-a174-40dbd83aedca.png)


 ###### **Website creation** #######
Title: Extinct: Who's next?
We decided the best way to visualize our data and make it interactive was to deploy an informative website.
To do this, we made another repository in GitHub: https://github.com/manjamcmills/extinct_whos_next  and subsequently a website at https://manjamcmills.github.io/extinct_whos_next /.  


To make our website interactive, we used the D3 library to read in the JSON files and an event listener to make a dropdown menu for each data set (Temperature, CO2, Sea Ice, and Sea Levels).  In turn, each data page was able to show the following:
1. Global overview graphs with a linear regression for a trendline
2. Interactive Graphs (by country, ocean, or hemisphere ) with a linear regression for a trendline.

*Summary Phase 2:*

> Uploading all csv files to Jupyter notebook
>> Data cleaning of all 4 categories using Python (importing pandas, matplotlib)
>>> JSON files were uploaded, HTML and JavaScript files were created, and Plotly was used to create the interactive graphs


 
 
## Phase 3: Creativity ##
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

The 3rd and final phase was created after our first run-through 1 week prior to the November 21, 2022 final presentation date. We took the feedback from our TA’s seriously and incorporated an emotional element (using a 3rd party character as the influencer) to our presentation in order to keep our audience's attention. Our fictional Bitmoji character, Cozmo, was created and embedded into our google slides + inserted onto each section of our webpage. 
We created Cozmo from the Bitmoji app. Cozmo’s personality was modeled after a fictionalized curious elementary school kid wanting to understand more about Global warming from data experts. We built a fictional storyline from the beginning to capture our audience’s attention and hone in on the content that the website is portraying: The global warming crisis. On each website page, you’ll find Cozmo at the bottom next to other inserted images. 


![PNG image-8AF148C2CA4B-1](https://user-images.githubusercontent.com/106992995/204067973-8ef0bf3e-f720-455d-b38c-682a66c883e1.png)
![Attachment-1 4](https://user-images.githubusercontent.com/106992995/204067969-3a2d118e-71e1-4b26-929f-db4807f60fe8.png)



Website layout:

1. *Home page* - overall info about climate change and why it should matter to us. The bottom portion of this page included an infographic for the “next steps” we can do to help the planet.
2. *Carbon Emissions Data* - with global and country carbon emission totals by year 
3. *Temperature Data* - with global and country temperature change data by year
4. *Sea Ice Data*  - with global and  Northern/Southern hemisphere sea ice area and extent data by year
5. *Sea Level Data* - with Global and Ocean sea level change by year

*Summary Phase 3:*

>Incorporate feedback into final design
>>Create fictional character the audience could relate to (Cozmo Bitmoji)
>>>Embed Cozmo into each webpage for a seamless presentation




## Conclusion: ##

 - Global temperatures are rising, global carbon emissions are increasing, global sea ice is decreasing and the sea levels are rising
 - We all need to work together towards green energy and helping to protect our planet for generations to come
 - 2050 is the year we'll find out if we're the next runner up for extinction like the dinosaurs (*this is a bad joke*)
 - But seriously, we should take steps (see infographic below) for how to help the planet vs. hurt it
 
![earthday-infographic](https://user-images.githubusercontent.com/106992995/204065843-a948fbd6-65ae-4c37-8361-c4d6421aa648.jpeg)



 

 - The key to our success as a group was through our clear communication and constant check-ins (Everyone in the group met every day for two weeks for 2-3 hours each day)
 
We created 3 separate supporting documents that help guide the main project to completion.

- 1st doc = final project google slides (https://docs.google.com/presentation/d/1OCcpPCFstG_TmgeyxjIWLizuJ5WkOVaHhz27OCaOcGs/edit?usp=sharing)
- 2nd doc = data gathering and explanation google sheets (https://docs.google.com/document/d/1uH294wUx5PHa5RpVKROHF2aiceWwoX-AfSVVuE2yENs/edit?usp=sharing)
- 3rd doc = final read.me collab (https://docs.google.com/document/d/15LfPm26SNHDJaf7dodAzpAEFRJjo9Nwthoa7QHXQMRM/edit?usp=sharing)






### Sources: ###
- - - - - - - - - - - - - - - - - - - -

**Homepage:** 
>1. New Report Suggests ‘High Likelihood of Human Civilization Coming to an End’ Starting in 2050: 
>><https://www.vice.com/en/article/597kpd/new-report-suggests-high-likelihood-of-human-civilization-coming-to-an-end-in-2050>

>2. What happens near the year 2050? 
>>How Oil and Gas Materials Used in Hospitals Saves Lives – Powering California
>>><https://poweringcalifornia.com/how-oil-and-gas-materials-used-in-hospitals-saves-lives/>

>3. When Fossil Fuels Run Out, What Then? - MAHB
>><https://mahb.stanford.edu/library-item/fossil-fuels-run/>

>4. Nested under Cozmo Bitmoji (dinosaur reference) 
>>“The coal we burn today got its start some 300 million years ago. Back then, dinosaurs roamed the Earth. But they didn’t get incorporated into coal. Instead, plants in bogs and swamps died. As this greenery sunk to the bottom of those wet areas, it partially decayed and turned into peat. Those wetlands dried out. Other materials then settled down and covered the peat. With heat, pressure and time, that peat transformed into coal. To extract coal, people now have to dig deeply into the earth.” 
>>><https://www.snexplores.org/article/explainer-where-fossil-fuels-come>

>5. -- next steps to take (infographic for 10 simple choices for healthier planet treatment:
>><https://oceanservice.noaa.gov/ocean/earthday.html>
-----------

**CO2 Atmospheric data:**
>6. “...It is one of the most important gasses on the earth because plants use it to produce carbohydrates in a process called photosynthesis. Since humans and animals depend on plants for food, photosynthesis is necessary for the survival of life on earth.” 
>><https://www.airthings.com/what-is-carbon-dioxide>

>7. *CO2 screenshot infographic*
>><https://cbs6albany.com/weather/weather-extra/soaring-co2-raising-global-temperatures-another-record-set-this-year-2022>
--------

**Polar Ice Caps:** 
>8. "The Arctic and Antarctic are the world’s refrigerator. Since they are covered in white snow and ice that reflect heat back into space, they balance out other parts of the world that absorb heat. Less ice means less reflected heat, meaning more intense heat waves worldwide." 
>><https://www.worldwildlife.org/pages/six-ways-loss-of-arctic-ice-impacts-everyone#:~:text=The%20Arctic%20and%20Antarctic%20are,meaning%20more%20intense%20heatwaves%20worldwide.>
--------

**Sea Level:**
>9. Coral reefs image source
>><https://www.boredpanda.com/sad-10-year-challenge-nature-memes/?utm_source=facebook&utm_medium=social&utm_campaign=BPFacebook&fbclid=IwAR3MxNeSeXFvm0zRqD_h3E3aEq6oqt7kbBmP5o0JlYpua4NoLoCwQJn1iTk>

>10. Coral reef coastline
>><https://www.noaa.gov/education/resource-collections/marine-life/coral-reef-ecosystems#:~:text=Coral%20reefs%20protect%20coastlines%20from,food%2C%20income%2C%20and%20protection>
--------

**Sea Ice:**
>11. Polar bear extinction estimate
>><https://www.biologicaldiversity.org/species/mammals/polar_bear/index.html#:~:text=Two%2Dthirds%20of%20the%20world's,Species%20Act%20is%20under%20attack.>
--------

**Surface Temperatures:**
>Question: “Why is the surface hot and how does that impact me?”
>>12. Answer: “Changes in ozone, greenhouse gasses and climate change affect agricultural producers greatly because agriculture and fisheries depend on specific climate conditions. Temperature changes can cause habitat ranges and crop planting dates to shift and droughts and floods due to climate change may hinder farming practices.” 
>>><https://www.epa.gov/agriculture/agriculture-and-climate#:~:text=Temperature%20changes%20can%20cause%20habitat,change%20may%20hinder%20farming%20practices>




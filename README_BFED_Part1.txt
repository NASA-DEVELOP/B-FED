NASA DEVELOP Massachusetts Water Resources
Spring 2020 Boston, MA Node
Beaver-Flood Event Detector (B-FED) Tool Kit
Part I Preprocessing

See Part II Analysis to run the script.

Date created: 03/18/2020

Functionality of Script
=================

B-FED Tool Kit: 
B-FED is a Google Earth Engine script that uses NASA Earth Observations, a MassGIS 
wetland polygon layer, citizen science Global Biodiversity Information Facility (GBIF) Data 
and remote sensing methodology to detect floodig events that are likely caused by beavers 
in Massachusetts, USA. The objective of this kit is to have an algorithm with conditional 
statements to determine for a given year if flooding, based on spectral signatures, caused 
by beavers has occurred. This is then filtered for a wetland layer and then inlaid with citizen 
science data of beaver observations from GBIF. The correlation of having flooding, 
along with reported beaver observations acts as a validation for the tool. B-FED is divided into 
three scripts.

Part I Preprocessing: This script filters for our study area,incorporates wetlands layer, 
ingests citizen science beaver observations data, preprocess Landsat imagery, and generates 
Tasseled Cap components: Tassled Cap Brightness (TCB) & Tassled Cap Greeness(TCG) for our alogrithm.
The end products of this script are exported as assets, and are imported into the second script, 
Part II Analysis.

Outputs:
1.	Tasseled Cap Components: Apply Crist 1985 tasseled cap coefficients to Landsat bands 
    to create tasseled cap components (Tasseled Cap Greenness (TCG), Tasseled Cap Brightness (TCB), 
    Tasseled Cap Wetness (TCW)) for the region of interest & export.
2.	Beaver Observations: filter by state & export
3.	Wetlands Layer: simplify & export
4.	Region of Interest (ROI): simplify boundary of state & export

How To Run Script Overview:
To obtain the outputs listed above, make the variable name equal to 1
Then the output will be executed and the exported layer will appear in the task tab.
Click the run button next to the asset, this will take a few seconds, then press upload, 
This might take several hours and can be left to run over night. Once it is complete, 
in the Assets tab, click refresh. Then click New, then click Image Collection and click 
and drag layers to the new Image Collection. 

How to Run Script for Specific Outputs:
1.	Tasseled Cap Components
    -Change DEPENDENT value to export different TC component (line 111)
        -Only one TC component will be exported at a time, greenness, brightness or wetness
    -Change START_YEAR and END_YEAR to export specific years of data (lines 112, 113) o To export one year, make the START_YEAR and END_YEAR the same value
    -Export this layer by changing FEATURES_EXPORT value to 1 (line 102)
        -The exported layer will appear in the Task tab
        -Click Run next to the asset, this will take a few seconds,
        -Then press upload, this might take several hours and can be left to run over night o In the Assets tab, click refresh
        -Then click New, then click Image Collection
        -Click and drag layers to the new Image Collection
2.	Beaver Observations
    -Change STATE_NAME to get a different state’s GBIF beaver observations (line 108)
    -Export this layer by changing BEAVER_EXPORT value to 1 (line 103)
3.	Wetlands Layer:
    -Export this layer by changing WETLANDS_EXPORT value to 1 (line 104)
    -This requires ROI_EXPORT = 1, because uses bounds_geo (line 105)
4.	Region of Interest (ROI):
    -Change STATE_NAME to set a different state as the region of interest (line 108)
    -Export this layer by changing ROI_EXPORT value to 1 (line 105)

Required Packages 
=================
* Google Earth Engine API


Required Data Inputs 
====================
* TIGER: US Census States 2018 dataset (TIGER/2018/States)
* wrs2: World Reference System
* USGS/NASA's Landsat 5 surface reflectance tier 1 dataset (January 1, 1985 - October 31, 2011)
* USGS/NASA's Landsat 7 surface reflectance tier 1 dataset (Nov 01, 2011 - April 10, 2013)
* USGS/NASA's Landsat 8 surface reflectance tier 1 dataset (April 11, 2013 - Dec 31, 2020)
* GBIF MASS Beaver Observations Public Asset: users/liana_stachowicz/global_beaver_observations
* MassGIS Data: MassDep Wetlands (2005): users/rlwcomposto/wetlands_ma_poly 
(link to wetlands data: https://docs.digital.mass.gov/dataset/massgis-data-massdep-wetlands-2005)

Contact
===================
Contributors: 
Dr. Valerie Pasquarella - valpasq@bu.edu
Ahmed Baqai - ahmedbaqai1994@gmail.com
Rebecca Composto - rlwcomposto@gmail.com
Adelaide Gonzalez- emilygonzalez2021@gmail.com
Liana Stachowicz - lianastack6@gmail.com

POC:
Name: Ahmed Baqai
E-mail address: Ahmedbaqai1994@gmail.com


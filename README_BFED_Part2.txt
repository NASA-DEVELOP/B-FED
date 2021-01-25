NASA DEVELOP Massachusetts Water Resources
Spring 2020 Boston, MA Node
Beaver-Flood Event Detector (B-FED) 
Part II Analysis

See Part II Analysis to run the script.

Date created: 03/24/2020

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

Part II Analysis: This script calculates TCG range (normalized to a reference year) and 
TCB mean cumulative sum. It then applies an algorithm (that can be manipulated) to these 
components, which detects flooded pixels. Then there is an option of only selecting flooded 
pixels that occur in wetlands as defined by MassGIS in 2005.


Outputs:
1.	Potential Flooding- No Wetlands Mask: Apply algorithm to TC components 
    to create potential flooding layer & export
2.	Potential Flooding- With Wetlands Mask: Apply algorithm to TC components 
    to create potential flooding layer, filter to create layer with only potential 
    flooding in wetland areas & export

How To Run Script:
To obtain the outputs listed above, make the variable names (lines 89 and 90)
equal to 1. Then the output will be executed and the exported layer will appear in the task tab.
Click the run button next to the asset, this will take a few seconds, then press upload, 
This might take several hours and can be left to run over night. Once it is complete, 
in the Assets tab, click refresh. Then click New, then click Image Collection and click 
and drag layers to the new Image Collection. 

How to Run Script for Specific Outputs:
1.	Potential Flooding- No Wetlands Mask: 
      -Export this layer by changing TC_NM_EXPORT value to 1 (line 89)
      -Change START_YEAR and END_YEAR to export specific years of data (lines 105, 106)
          -To export one year, make the START_YEAR and END_YEAR the same value 
2.	Potential Flooding- With Wetlands Mask: 
      -Export this layer by changing TC_WM_EXPORT value to 1 (line 90)
      -Change START_YEAR and END_YEAR to export specific years of data (lines 105, 106)
          -To export one year, make the START_YEAR and END_YEAR the same value


Algorithm Overview:
First TCG range (normalized to a reference year, TCG_REF_YEAR) and TCB mean cumulative 
sum is calculated. If a pixel has a TCG range less than 70% (TCG_PERC_THRESH) and a 
TCB cumulative mean less than -0.05 (TCB_TRESH), then the algorithm marks that pixel as 
flooded. These thresholds can be manipulated to further constrain detected flooding.
The year to normalize TCG and the threshold values can be manipulated to improve the 
accuracy of the algorithm: TCG_REF_YEAR, TCG_PERC_THRESH, TCB_THRESH (lines 109-111).

Required Packages
===================
* Google Earth Engine API

Required Data Inputs 
===================
* TIGER: US Census States 2018
* Public Asset from Liana_Stachowicz: Global Beaver Observations 
* Public Asset from Ahmed94: TCB_1985_2019_ICollection
        Link: https://code.earthengine.google.com/?asset=users/Ahmed94/TCB_1985_2019_ICollection
* Public Asset from Ahmed94: TCG_1985_2019_ICollection
        Link: https://code.earthengine.google.com/?asset=users/Ahmed94/TCG_1985_2019_ICollection
* Public Asset from Ahmed94: users/Ahmed94/massBeaverObv  (Mass Beaver Observations)
        Link: https://code.earthengine.google.com/?asset=users/Ahmed94/massBeaverObv
* Public Asset from rlwcomposto "users/rlwcomposto/simplifiedMA" (Simplified Massachussets Layer)

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

Notes
===================
This code is based off of Dr. Pasquarella's 2_B-FED_analysis code
The change is exporting the results to feature collections use if statements.
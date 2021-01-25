NASA DEVELOP Massachusetts Water Resources
Spring 2020 Boston, MA Node
Beaver-Flood Event Detector (B-FED) 
Part III Visualization

See Part III Visualization to run script.

Date created: 03/27/2020

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


Part III Visualization: The final script in the tool kit displays flooding events 
at annual time stamps in relation to beaver activity observations in Massachusetts 
Audubon Sanctuaries and across Massachusetts.

Outputs:
1.Time Series Charts: prints group of pixels time series for TCG and TCB specified bands
2.User Interface (UI): allows user to view potential flooding and other relevant information
    a. Toggle layers: Satellite background provided by GEE, Wetlands layer, 
       All potential flooding 1986-2019, Yearly potential flooding, Beaver activity 1999-2020
    b. Displays legend & link to iNaturalist 
    c. Animates yearly potential flooding
    d. Beaver Activity Year: When users click on a beaver observation, displays the year observed and link to iNaturalist submission
3.Time series visualizations 
    a. Maps: Display flooding at one time and/or other layers
    b. Gifs: Display potential flooding through time
	
How to Run Script:
To obtain the outputs listed above, for the charts uncomment lines 273, 288,
for the UI just click Run, for the time series visualizations 
uncomment lines 708-716.

How to Run Script for Specific Outputs:
1.Time Series Charts: 
    **Uncomment print statements in order for the charts to display in the Console (line 273, 288)
    -Change TC component’s bands displayed (line 261, 276)
    -Currently TCG is set to display the ‘min’ and ‘max’ bands
    -Currently TCB is set to display the ‘mean’ band
    -Optional bands to display: ‘mean’ ‘variance’ ‘min’ ‘median’ ‘kurtosis’ ‘skew’ ‘range’
    -Change the date of the time series (line 262, 277)
    -Change the specified area (line 263, 278)
        -The bigger this area, the more pixels will be aggregated to create a time series
        -If there aren’t flooded pixels in this area, it won’t have the expected spectral pattern
    -Change the title of the chart (line 266, 281)
2.User Interface (UI):
    -Just click run
    -Change true to false to not display the layer (user can still toggle this layer) (line 576-580) o Comment out the line (add //) to have the layer not show up at all
    -Change the name of the layer displayed (line 576-580)
    -Change the background imagery (line 582)
      -Options:‘SATELLITE’,‘ROADMAP’,‘HYBRID’,‘TERRAIN’
    -Change how zoomed the UI is when the display opens, ( line 584)
      -Increase the integer to make it more zoomed in and decrease it zoom out
3.Time series visualizations 
    **Uncomment print  statement with the same variable name in order to print the 
    gif in the Console.
    -To make maps, Combine different layers to create desired map. Copy and paste 
    the lines 668-669 at the end of the script and input your desired layers from the 
    titles in Layer Options above, put the layer names in the locations in purple writing 
    and feel free to add more .blend() statements. Also pick a video parameter from the 
    Video Parameters list above, and input that name in the pink text location 
    (see example at line 668-669).
    -To make gifs, display potential flooding through time. Similar to the maps, the 
    layers displayed in the gifs can be changed using the same options. First, select the 
    variable name (timeIpsS, timeBroS, etc.) for your desired area then change the layer 
    options. Lastly, uncomment the print statement with the same variable name in order to 
    print the gif in the Console. In this case you do not need to change the video 
    parameters. (lines 671-716)


Layers & Video Paramters available to combine into different visualizations:

Layer Options:
background1995 – composite Landsat imagery from 1995 (can be made for any year) 
backgroundSentinel – composite Sentinel imagery from 2017
MAS_S – outline of MAS properties
mass_obs2 – beaver observations, 10x size
mass_obs3 – beaver observations 3x size
maOutline – outline of buffered Massachusetts (ROI) 
wetlandsViz – raster layer of simplified wetlands 
allFloods_nmViz – all potential flooding 1986 - 2019 
allFloods_wmViz – all potential flooding in wetlands 1986 - 2019

Video Parameters (to be applied to maps or gifs): 
videoArgsMA – use for Massachusetts 
videoArgsIpswich – use for Ipswich 
videoArgsBroadmoor – use for Broadmoor 
videoArgsWachusett – use for Wachusett

Required Packages
===================
* Google Earth Engine API

Required Data Inputs 
===================
* TIGER: US Census States 2018
* Public Asset from Liana_Stachowicz: 'users/liana_stachowicz/global_beaver_observations' 
* Public Asset from Ahmed94: 'users/Ahmed94/TCB_1985_2019_ICollection'
* Public Asset from Ahmed94: 'users/Ahmed94/TCG_1985_2019_ICollection'
* Public Asset from valerie: 'projects/ee-valeriepasquarella/assets/Massachusetts_wetland_mask'
* Public Asset from rlwcomposto: 'users/rlwcomposto/simplifiedMA'
* Public Asset from rlwcomposto: 'users/rlwcomposto/MA_Flooding_nm_1986-2019'
* Public Asset from rlwcomposto: 'users/rlwcomposto/MA_Flooding_wm_1986-2019'
* Public Asset from rlwcomposto: 'users/rlwcomposto/Mass_Audubon_Shp'

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
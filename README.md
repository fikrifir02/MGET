# MGET Notes

## **Determining cell types given layers overlayed to each others in some area**

This was done because in one cell of planning unit reef proportion is not always 100%. It can consist of reef, land, and or water proportion.
Therefore, we should first determine types of every single cells in the planning unit.

We should have at least three types of cell for our raster planning unit:
1) reef
2) land
3) water

To determine those types using the available shapefile data (this data can be overlaid to each other, due to eg. different source of data,base projection, etc) we have to make priority and #1 priority is reef. Although, later reef cells might not be necessary reef habitas as its proportion can be 0%
1) if reef proportion >0%, set cell as reef cell. Other cells then can be land or water.
2) if land and water layers are overlap, set it as land cell.
3) if water and reef layers are overlap, set it as reef.


**index: land = 0; reef = 2; water = 3; **


## **Number of cells of raster data set**
Apparently, number of cells of land water raster does not have to be same as the reef proportion raster 


## **Adjusting cell size**
cell size adjustment cannot be done directly through the available planning unit (e.g. 1km). Adjustment has to be done from :
1) create new planning unit (e.g. 10 km)
2) create new ID for each cells
3) calculate reef proportion in each cell


## 10km adjustment and reef cell
* it seems weird for some cells. because it is defined as reef cell due to consisting a small amount of reef proportion (e.g. 1%) . Therefore, land cell doesnt exist. It is changed by reef cell. 

we can see the red patch on image below, the largest red patch actually contains land area. However, it is defined only as reef due to they have some reef proportion

![weird cells](https://user-images.githubusercontent.com/73259648/153316511-5cac84e5-c3fa-49ee-83bf-a602cf402720.JPG)

![weird cells 1](https://user-images.githubusercontent.com/73259648/153316365-652dbfee-8ba1-4612-81d6-a8722fc7bae9.JPG)

## Reef IDs
IDs can be done only for reef patch. Land and water patches do not have to have IDs.

_**Larvae seeding**_ 
Larval was seeded to each reef habitat based on Reef IDs.
There are two ways to seed the larvae.
1) one reef one ID, this means one reef can consist of more than one cell. Reefs can have same IDs
2) Each IDs for each reef cell. Reef extent to more than 10x10km in size. That will include more than one cell. Another alternative, we can use same reef ID for many reef cells

## cell size or layer extent
each raster data set should have: 1) same cell size (e.g. 1km, 10km); 2) layer extent (minimum and maximum extent for each side (north, south, east, west) for each layer

1) set land and water layer (as a one layer) area as masking (there is gap inside the layer, as reef might exist)
![reef gap](https://user-images.githubusercontent.com/73259648/153319767-b76efa25-8aaf-4e68-84fc-ef36d539c821.JPG)

2) create a full extent of raster reef data set. This may include land and water area (identified by 0% reef proportion) 
   ![reef full extent](https://user-images.githubusercontent.com/73259648/153319996-6b36fb52-6ba5-4733-94f1-cea3382cf861.JPG)

This solution worked well

## adding HYCOM data into larva dispersal analysis
unfortunately, too complex working directory (eg. connected to onedrive) does not work well in Arcmap toolbox. Thus, input and output directory should be on local directory to avoid errors while simulating.


## Data sources
1) Wilayah Pengelolaan Perikanan/Fisheries Management Area - 2011 - Pusat Riset Kelautan
2) Coral reef Distribution - 500m grided reef distribution - World Resources Institute (WRI)
3) Administration boundariesss - RBI 250K - tanah air


# Data analysissss
* RBI shapefile was dissolved based on province administrative boundaries
* WRI reef distribution was clipped only for WPP713 region
* planning unit was created from the WPP RI 714 feature which was clipped from the whole WPP RI shapefile
* reef area was measured in each cell of planning unit to estimate the proportion of reef in each cell - reef proportion is required in biophysical model (MGET)
* 

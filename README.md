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

sebenerny yang harus diberi ID tu adalah reef habitatnya saja atau land water juga?
Nampaknya hanya reef habitat yang berikan ID, reef habitat bisa memiliki ID yang sama jika merupakan reef yang sama 

karena dasar penentuan D habitat adalah planning unit, maka ID reef bisa berbeda beda walaupun satu reef sebenernya.
Ini akan berpengaruh pada saat seeding larvae, tiap ID akan di seed sejulah larvae yang sudah di set up.
Jika satu reef memiliki 2 ID maka adkan ada dua kali seeding
JIka satu reef hanya memiliki satu ID maka hanya akan sekali seeding


karena berbasis raster asumsinya raster land dan water tidak perlu
di sederhanakan.  Karena raster size setiap habitat bisa sama atau beda

dan land water tidak perlu diberikan ID seperti halnya reef.
Reef dengan size raster yang sama harus diberikan ID dan reef proportion


jika dibedakan bentuk raster reef dan landwater maka simulasi 
larva dispersal tidak bisa dilakukan (error) karena cell size atau extentny berbeda

Kemngkinan solusinya adalah:
1) jadikan land water sebagai masking (namun yang ada bagian reef nya dijadikan bolong)
2) buat raster reef habitat yang mencakup keseluaruhan extent atau cell size
   habitat lain(land/water) diwakili dengan reef prop = 0
........................................................
Solusi di atas berhasil
........................................................
sekarang tinggal menambahkan data oseanografi HYCOM.


............................................................
Sebelumnya

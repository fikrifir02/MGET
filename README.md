# MGET

Deciding habitat definition

(hal ini dilakukan karena dalam satu planning unit atau cell reef proportion tidak 100%.
satu cell merupakan merupakan proporsi (%) land, reef, dan water)

Penentuan habitat dilakukan dengan prioritas terumbu karang, walaupn nantinya terumbu karang akan diberikan nilai proporsinya dalam satu cell 0 - 1.0
1) Prioritaskan terumbu karang, jika terumbu karang overlap dengan daratan, maka habitat yang dimasukan adalah terumbu karang
2) jika land dan water overlap maka area tersebut ditentukan sebagai land
3) jika water dan terumbu karang overlap maka habitat yang menghuni adalah terumbu karang

index: land = 0; reef = 2; water = 3;

if habitat


Apparently, number of cells of land water raster does not have to be same as the reef proportion raster 

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

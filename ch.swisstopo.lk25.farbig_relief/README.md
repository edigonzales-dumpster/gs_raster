```
mkdir gs_pyramid_bilinear
gdal_retile.py -v -r bilinear -levels 4 -ps 4096 4096 -co "TILED=YES" -co "COMPRESS=DEFLATE" -targetDir gs_pyramid_bilinear lk25_farbig_relief.vrt
```

```
mkdir gs_pyramid_lanczos
gdal_retile.py -v -r lanczos -levels 4 -ps 4096 4096 -co "TILED=YES" -co "COMPRESS=DEFLATE" -targetDir gs_pyramid_lanczos lk25_farbig_relief.vrt
```

```
mkdir gs_gpkg
gdal_translate -a_srs EPSG:2056 -of GPKG lk25_farbig_relief.vrt gs_gpkg/ch.swisstopo.lk25.farbig_relief.gpkg -co TILE_FORMAT=PNG_JPEG
gdaladdo -r average gs_gpkg/ch.swisstopo.lk25.farbig_relief.gpkg 2 4 8 16 

```

```
mkdir gs_gpkg_png
gdal_translate -a_srs EPSG:2056 -of GPKG lk25_farbig_relief.vrt gs_gpkg_png/ch.swisstopo.lk25.farbig_relief.gpkg -co TILE_FORMAT=PNG
gdaladdo -r average gs_gpkg_png/ch.swisstopo.lk25.farbig_relief.gpkg 2 4 8 16 
```

```
mkdir gs_gpkg_jpeg
gdal_translate -a_srs EPSG:2056 -of GPKG lk25_farbig_relief.vrt gs_gpkg_jpeg/ch.swisstopo.lk25.farbig_relief.gpkg -co TILE_FORMAT=JPEG
gdaladdo -r average gs_gpkg_jpeg/ch.swisstopo.lk25.farbig_relief.gpkg 2 4 8 16 
```


```
mkdir gs_gpkg_fubar_jpeg
gdal_translate -a_srs EPSG:2056 -of GPKG fubar.vrt gs_gpkg_fubar_jpeg/ch.swisstopo.lk25.farbig_relief.gpkg -co TILE_FORMAT=JPEG
gdaladdo -r average gs_gpkg_fubar_jpeg/ch.swisstopo.lk25.farbig_relief.gpkg 2 4 8 16 
```
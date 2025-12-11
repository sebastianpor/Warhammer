---
mapCalc1: 0.3171247357293869
map_height_y: 13696
map_width_x: 14016
scale_pixels: 473
scale_pixels_range: 150
---
```leaflet  
id: Mapa Starego Swiata ### Must be unique with no spaces  
image: [[MSS.jpg]] ### Link to the map image file. Do not add a ! in front of the image  
bounds: [[0,0], [13696 , 14016]] ### Size of the map in px Height_y, Width_x. Ignore 0,0  
height: 800px ### Size of the leaflet embed in px on your screen  
width: 95% ### Size of the leaflet embed in your note  
lat: 7000 ### To center the map, make this half of the map height.  
long: 8350 ### To center the map, make this half of the map width.  
minZoom: -5 ### Controls how far away from the map you can zoom out. Hover over the target icon to see the current level.  
maxZoom: 1 ### Controls how far towards the map you can zoom in. Hover over the target icon to see the current level.  
defaultZoom: -1 ### Sets the default zoom level when the map loads. Hover over the target icon to see the current level.  
zoomDelta: 0.5 ### Adjust how much the zoom changes when you zoom in or out.  
unit: km ### The value displayed when measuring so you know what type of unit is being measure.  
scale: 0.3171247357293869 ### Real units/px (resolution) of your map  
recenter: false  
```


![Module Cover image](./assets/images/GY4027_new_banners_Course_Banner.png)

# Lab Exercise: Geospatial Assessment of Landscape Maturity

In the Week 4 lecture, we discussed upland landscapes, and the concept of landscape maturity. One of the ways geomorphologists study upland landscapes is to look at the proportion of an area at each level of elevation. This is called a hypsometric curve. In this lab exercise, you will produce hypsometric curves for two upland areas of Ireland, and use these to contrast the two landscapes.

## QGIS

In order to produce the curves, you will use the free and open source GIS software QGIS. This is available on the PCs in A0-060A/B/C in the Main Building, and S1-19 in the Schuman Building. It's also completely free, so you can [download and install it on your own PC](https://qgis.org/en/site/forusers/download.html).

When you open QGIS, from the menu choose `Project > New` to open a new project.

![New project](./assets/images/)

The main part of the QGIS window is the map canvas. To the left you should see the Layers and Browser panels. You should also see the Toolbars below the menu above the map canvas.


## Task 1 - Adding the Data

I would like you to compare an upland area from Munster to an upland area from Connacht or Ulster. For both, you have a choice:

**Munster**

| Region | Extent | DEM |
| Dingle Peninsula | [Dingle.gpkg](./assets/gis/Dingle.gpkg) | [dingle_dem.tif](./assets/gis/dingle_dem.tif)
| Iveragh Peninsula / Killarney National Park | [Iveragh-Killarney.gpkg](./assets/gis/Iveragh-Killarney.gpkg) | [iveragh_killarney_dem.tif](./assets/gis/iveragh_killarney_dem.tif)
| Beara Peninsula | [Beara.gpkg](./assets/gis/Beara.gpkg) | [beara_dem.tif](./assets/gis/beara_dem.tif)
| Galtee Mountains | [Galtees.gpkg](./assets/gis/Galtees.gpkg) | [galtees_dem.tif](./assets/gis/galtees_dem.tif)
| Knockmealdown Mountains | [Knockmealdown.gpkg](./assets/gis/Knockmealdown.gpkg) | [knockmealdown_dem.tif](./assets/gis/knockmealdown_dem.tif)
| Comeragh Mountains | [Comeragh.gpkg](./assets/gis/Comeragh.gpkg) | [comeragh_dem.tif](./assets/gis/comeragh_dem.tif])

**Connacht / Ulster**

| Region | Extent | DEM |
| Connemara | [Connemara.gpkg](./assets/gis/Connemara.gpkg) | [connemara_dem.tif](./assets/gis/connemara_dem.tif)
| South Mayo | [SouthMayo.gpkg](./assets/gis/SouthMayo.gpkg) | [south_mayo_dem.tif](./assets/gis/south_mayo_dem.tif)
| North Mayo | [NorthMayo.gpkg](./assets/gis/NorthMayo.gpkg) | [north_mayo_dem.tif](./assets/gis/north_mayo_dem.tif)
| Donegal | [Donegal.gpkg](./assets/gis/Donegal.gpkg) | [donegal_dem.tif](./assets/gis/donegal_dem.tif)

Choose one from each list. For your chosen areas, you will need to download the two linked files. These are:

1. A digital elevation model. This is a kind of data known as raster data, made up of pixels, with each pixel having a value. Photographs are an example of raster data - in that case, the pixel values are colours. Here, the pixel values are the elevation of the land surface.
2. Boundary shapes. This is a kind of data called vector data. In this format, rather than saving data as values for each pixel, these store information as a series of co-ordinates, defined as points, lines, or polygons. These particular layers are vector polygons, defining the areas of interest.

Create a folder for this exercise in your UL OneDrive. Save the 4 files in that folder. You should be able to drag and drop the 4 files into the QGIS map canvas to add them to your project.

You should now see the four layers listed in your `Layers panel`, and see them displayed in the map canvas area. You might also notice that at the bottom right corner, there is a small text box which now reads `EPSG:2157`. When working in GIS, it is vitally important to know what co-ordinate system you are using for your data, because there are many, many different systems. In this case, `EPSG:2157` is the Irish Transverse Mercator (ITM) coordinate system, used by Ordnance Survey Ireland and for all Irish geospatial data. This is better than working in, say, latitude and longitude, which have units of degrees, minutes, and seconds; the units of the ITM grid are metres, which is much more useful on the ground.

At this point, let’s save the project to ensure we don’t have to start again. From the menu, choose `Project > Save As`, navigate to your folder in your OneDrive, type the name `uplands` for the `File name`, and click `Save`.

## Task 2 - Elevation Classes

What you’re going to do in this exercise is to create hypsometric curves for both areas, to compare the height profiles of two of Ireland’s uplands areas. There’s a few steps along the way.

The first step in creating a hypsometric curve is to divide the area into a number of discrete elevation classes. Then we can look at what percentage of the area is at each of these different levels of elevation. We’ll start by styling one of your DEM layers - it doesn't matter which.

In the `Layers panel`, click on one of your DEM layers, and drag it to the top of the list of layers. Then right-click this layer in the `Layers panel`, and choose `Properties`, and if necessary, `Symbology`.

Change `Render type` from *Singleband gray* to *Singleband pseudocolor*. Click the arrow to expand `Min/Max Value Settings`; ensure *Min/Max* is selected, and change `Accuracy` to *Actual (slower)*.

Change `Interpolation` from *Linear* to *Discrete*. Click the dropdown arrow for `Color ramp` and pick one – I recommend *Spectral*, and choosing `Invert Color Ramp` so that blue indicates low elevation, and red indicates high elevation.

Under the central panel, change `Mode` from *Continuous* to *Equal Interval*, and on the right change `Classes` to *12*.

You should now see a series of colours in the central panel, each with a value to the left and a label to the right. Scroll down to the bottom of the list, which should have a value of `inf`. Change the value to the left for this to *1100*. Now change the one above it to *1000*, and the next to *900*, and so on until you reach the top, which should be *0*.

Now click OK to close the Layer `Properties` window. You should see the DEM layer displayed in the chosen colour ramp, with the different colours indicating different elevations.

You can get a much better visual of this. Right click on this DEM layer in the `Layers panel`, and choose Duplicate layer. Drag the copy layer above the original, click the checkbox beside it to make it visible, and right click on it and choose `Properties`. Change `Render type` to *Hillshade*, and under `Layer rendering` change `Blending Mode` to *Overlay*. When that's done, click `OK` to close the `Layer Properties` window.

You should now see the DEM layer appearing in 3D, and should be able to see the relationship between the colours and the elevation a lot more clearly.

To do this for your second DEM layer, you can first right click on your original (not copy) DEM layer and choose `Styles > Copy` style, then click on your second DEM layer and choose `Styles > Paste` style. Duplicate the second DEM as you did for the first, making the copy visible and dragging it above the original, then copy and paste the styles from the first DEM copy to the second DEM copy.

Save the project before continuing.


## Task 3 - Reclassifying

You might be able to see a difference between the two areas now, but we want to quantify the difference, not just see it. To do this, we want to essentially measure the size of the areas shown in each colour after the previous task. We can't do this from just how it's displayed, but we can reclassify each DEM so that areas shown in the different colours are each set to a single value.

From the menu, choose `Processing > Toolbox`, and the Processing Toolbox panel will open. Type *classify* in the search bar, and choose *Reclassify by Table*.

For *Raster layer*, choose one of your original DEM layers. Click the Browse `...` button beside *Reclassification table* to open the table. Click the `Add Row` button 12 times, to add 12 rows. This table will define how the raster is reclassified: any values between the `Minimum` and the `Maximum` will be changed to the `Value`. Double-clicking on a cell will allow you to edit it; enter values so that the table matches our `Symbology` classes, with *-10* for the `Minimum` in Row 1, and 1100 for the `Maximum` in Row 12. For `Value` in each row, enter the same number as the `Minimum` – that’s the elevation value where that row starts.

| Minimum | Maximum | Value |
| -10 | 0 | -10 |
| 0 | 100 | 0 |
| 100 | 200 | 100 |
| 200 | 300 | 200 |
| ... | ... | ... |
| 900 | 1000 | 900 |
| 1000 | 1100 | 1000 |


When you’re finished the table, click `OK` to return to the main `Reclassify by Table` window.

Under `Advanced Parameters`, ensure `Output NoData` value is set to *-9999*, and `Range boundaries` is set to  *min < value <=max*.

Click the checkbox beside `Use NoData when no range matches value`, and change` Output data type` to  *Int16*.

Click the Browse `...` button beside `Reclassified raster` and choose `Save to File`. Navigate to your GY4027 GIS folder in your OneDrive, type a name like *DEM1reclassify* for the `File name` (ideally include the location name), and click `Save`. 

Click `Run` to reclassify the raster. 

When it's finished, you can more easily repeat this for the second DEM if you click the `Change Parameters` button to return to the main `Reclassify by Table` window, then change `Raster layer` to your second original DEM layer. You'll have to change the save file as well, so again click the Browse `...` button beside `Reclassified raster` and choose `Save to File`, navigate to your GY4027 GIS folder in your OneDrive, type a name like *DEM2reclassify* for the `File name` (again ideally including the location name), and click `Save`. Once you've done that, you can click `Run` to reclassify the second DEM raster. 

When finished, you can click `Close` to close the `Reclassify by Table` window. 

You should now see the DEM layers looking somewhat like the coloured versions, but in shades of grey.

Save the project before continuing.


## Task 4 - Raster to Vector

Now, this has given us a reclassified digital elevation model, with the elevations divided into 9 areas of different height bands. The next thing we need to know is the area in each of those height bands – and more specifically what percentage of the overall area is in each of those height bands. To get those numbers, we need to convert the reclassified DEM from a raster image to vector data.

From the menu, choose `Raster > Conversion > Polygonize (Raster to Vector)`. In the `Polygonize (Raster to Vector)` window, change `Input layer` to your first reclassified DEM (made in the previous task).

Change `Name of the field to create` to  *elevation*, then because we need to save this as well, click the Browse `...` button beside `Vectorized` and choose `Save to File`. Navigate to your GY4027 GIS folder in your OneDrive, type a name like *DEM1classes* for the File name (ideally include the location name), and click `Save`.

Click `Run` to polygonize the raster. As in the previous task, we can easily repeat this for the second DEM if you click the `Change Parameters` button to return to the main `Polygonize (Raster to Vector)` window, then change `Input layer` to your second reclassified DEM (made in the previous task). You'll have to change the save file as well, so again click the Browse `...` button beside beside `Vectorized` and choose `Save to File`. Navigate to your GY4027 GIS folder in your OneDrive, type a name like *DEM2classes* for the File name (ideally include the location name), and click `Save`. Once you've done that, you can click `Run` to vectorize the second DEM raster. 

When finished, you can click `Close` to close the `Polygonize (Raster to Vector)` window.

Save the project before continuing.

## Task 5 - Dissolve

You should now see the two DEM layers as single colours, but with lines outlining the different elevation bands. However, disconnected areas of the same elevation class will still be different features. If you open the attribute table for one of the vector layers (right click on the layer in the `Layers panel`, and choose `Open Attribute Table`), you'll see hundreds or thousands of features. We only want one feature per elevation class, for a maximum of 12. We can merge areas of the same elevation class, so that's our next step.

From the menu, choose `Vector > Geoprocessing Tools > Dissolve`. In the `Dissolve` window, change `Input layer` to your first vectorised DEM (made in the previous task).

We want this tool to dissolve areas of the same elevation class, so click the Browse `...` button beside `Dissolve field(s) [optional]`, select the checkbox beside `elevation`, and click `OK` to return to the main `Dissolve` window.

We also need to save this, so click the Browse `...` button beside `Dissolved` and choose `Save to Geopackage`. Navigate to your GY4027 GIS folder in your OneDrive, choose the same Geopackage file you saved in the previous task, and click `Save`. A pop-up will appear asking for a ``Layer name``; type *dissolved*, and click `OK`. Then click `Run` to dissolve the layer.

As in the previous tasks, we can easily repeat this for the second DEM if you click the `Change Parameters` button to return to the main `Dissolve` window, then change `Input layer` to your second vectorized DEM (made in the previous task). You'll have to change the save file as well, so again click the Browse `...` button beside beside `Dissolved` and choose `Save to Geopackage`, navigate to your GY4027 GIS folder in your OneDrive, and choose the geopackage file you saved for the second DEM. Again you'll get the pop-up asking for a ``Layer name``; same as the previous, type dissolved, and click `OK`. Then click `Run` to dissolve the second layer.

When finished, you can click `Close` to close the `Dissolved` window.

Save the project before continuing.

## Task 6 - Reproject

Now, unfortunately our DEMs came using the latitude-longitude coordinate system, and so the vector layers you've just made are also in that system (`EPSG:4326`). This is no good for us, because the coordinate units here are degrees, and we can't measure area in degrees. We need them to be in the Irish Transverse Mercator coordinate system (`EPSG:2157`), which uses coordinates in metres.

Fortunately, this is an easy fix.

From the menu, choose `Vector > Data Management Tools > Reproject Layer`. In the `Reproject Layer` window, change `Input layer` to your first dissolved DEM (made in the previous task).

Change `Target CRS` to `Project CRS: `EPSG:2157` - IRENET95 / Irish Transverse Mercator`.

Again we need to save this, so click the Browse `...` button beside `Reprojected` and choose `Save to Geopackage`. Navigate to your GY4027 GIS folder in your OneDrive, choose the same Geopackage file for this DEM you saved in Task 4 and used in the previous task, and click `Save`. A pop-up will appear asking for a ``Layer name``; type *reprojected*, and click `OK`. Then click `Run` to reproject the layer.

Once again, we can easily repeat this for the second DEM if you click the `Change Parameters` button to return to the main `Reprojected` window, then change `Input layer` to your second dissolved DEM (made in the previous task). You'll have to change the save file as well, so again click the Browse `...` button beside beside `Reprojected` and choose `Save to Geopackage`, navigate to your GY4027 GIS folder in your OneDrive, and choose the geopackage file you saved for the second DEM. Again you'll get the pop-up asking for a `Layer name`; same as the previous, type reprojected, and click `OK`. Then click `Run` to reproject the second layer.

When finished, you can click `Close` to close the `Reproject Layer` window.

The DEMs should not look particularly different after these tasks - single colours with lines separating the elevation classes. However, if you hover over the reprojected layers in the `Layers panel`, you should see a pop-up saying (in part) `EPSG:2157` showing that they're now in a coordinate system we can use; and if you open the attribute table, you should see 12 or fewer classes. Not everything is about looks!

Save the project before continuing.

## Task 7 - Calculating areas

Open the attribute table for your first reprojected DEM. You should see a table with two columns: `fid`, and `elevation`. We need to add a column giving the area of each elevation class.

To do this, we’ll use QGIS’s Field Calculator. Click the `Field Calculator` button in the Attribute Table toolbar (looks like a small abacus: three rows of coloured circles on horizontal lines). In the `Field Calculator` window, type *ClassArea* for the `Output field name`, and change `Output field type` to *Decimal number (real)*. Then, in the central panel, click the arrow beside `Geometry` to expand it, then double-click `$area`. Now click `OK`.

You should now see a new column in the attribute table, which contains the area covered by landscape within the elevation limits for each class.

However, these areas are in square metres, which is good, but also the numbers are huge which makes them hard to compare. It would be easier to see them as percentages of the total area.

This is where the original geopackage layers showing the extent of each area come in. Right click on the extent layer relevant for this DEM in the `Layers panel`, and open the attribute table for it. You should see one feature, with four attributes – one of which is area. Copy the number shown for area.

Now go back to the attribute table for your reprojected layer, and click the `Field Calculator` button again. This time, for `Output field name` type *%area*; for `Output field type`, choose *Decimal number (real)* again.

Below the left panel, click the open bracket button `(`, then in the central panel, click the arrow to expand `Fields and Values`, and doubleclick on the new `ClassArea` attribute you calculated in the last step. Then click the `/` symbol, and then type or paste the value for area you just copied.

Now click the close bracket button `)`, then click the `* `button (for multiply), and type *100*.

When you’ve done that, click `OK`. 

You should now see a new `%area` column in the attribute table, giving the area of each elevation class as a percentage of the total area.

Click the pencil icon in the toolbar to toggle editing off for the layer, clicking `Save` on the `Stop Editing` popup asking if you want to save the changes to the layer reprojected.

Repeat for the second reprojected DEM layer.

Save the project before continuing.

## Task 8 - Hypsometric Curves

Now, we want to make a graph with this data, so we want to bring it into Excel. We do this by exporting the data to a spreadsheet. Close the attribute table, then right click on the reprojected layer (to which you added the areas in the previous task) in the `Layers panel`, and choose `Export > Save Features As`.

For `Format`, choose `Comma Separated Value [CSV]`. Click the Browse `...` button beside `File name`, navigate to your GY4027 GIS folder, type a name like *DEM1Hypsometry* for the `File name` (again, ideally include the location name in that), and click `Save`. For `Geometry type`, choose `No Geometry`, and deselect the `Add saved file to map` checkbox. Click `OK` to save the spreadsheet.

Repeat for your second reprojected layer, and save the project before continuing.

Now open the first spreadsheet in Excel. We need to do one more thing before we make the graph, because we want the graph to show cumulative percentage area.

First, sort the data so that it’s in order of elevation, from highest to lowest. To do this, go to the `Data` tab, highlight all the data and click `Sort`. In the `Sort` window, change `Sort by` to `elevation`, and `Order` to `Largest to Smallest` (i.e. so the highest elevations are at the top), and click `OK`.

Now add a new column. In cell `E1`, give the column the name *Cumulative*. For the highest elevation level in `E10`, the cumulative area is the same as the area for this class (because there is no higher class), so in cell `E10` type the formula `=D10`.

For the remaining cells, the cumulative area will be the area for that class, plus the cumulative area for the class above. We can calculate this for cell `E9` by typing in the formula `=D9+E10`, and hit the enter key (also called the return key).

Once that’s done, and you see a number in the cell, click on cell `E9` to select it; then click the small square at the bottom right corner, and drag it up to `E2`. This will fill the formula into the rest of the cells.

That’s it – that’s the data. Now we have to graph it.

Create a graph using columns `B` and `E`, with `Elevation` on the Y-axis, and `Cumulative Area` on the X-axis. This is the hypsometric curve for your first DEM.

Save your spreadsheet in your GY4027 GIS folder (change file type to `.xlsx`).

Repeat for the second DEM.

## Task 9 - TASK

You now have hypsometric curves for two of Ireland's uplands areas. I have three questions for you:

1. What is the difference between the two areas, as shown by their respective hypsometric curves?
2. What could you interpret from these differences?
3. Can you suggest any limitations of this methodology?




___

[Module Home](./README.md) | [Labs](./labs.md)
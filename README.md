# Nashville area Tornadoes Emergency Response Imagery

The National Geodetic Survey has published Emergency Response Imagery for the damage track from the 2020 tornadoes near the Nashville area.

The data are available as [cloud optimized geotiffs](https://www.cogeo.org/) on Amazon S3 at **s3://noaa-eri-pds/2020_Nashville_Tornado/**. The geotiffs can be used in GIS mapping software such as ArcGIS, QGIS, or explored with analysis software such as Python.

## How to get this data

The [AWS CLI](https://aws.amazon.com/cli/) can be used to access this data. No AWS account is necessary.

To list all of the available data:

```
aws s3 ls s3://noaa-eri-pds/2020_Nashville_Tornado/ --recursive --no-sign-request
```

To download a single geotiff file:

```
aws s3 cp s3://noaa-eri-pds/2020_Nashville_Tornado/20200307a_RGB/20200307aC0853600w361200n.tif . --no-sign-request
```

You can also access this data via HTTPS at [https://noaa-eri-pds.s3.amazonaws.com/index.html#2020_Nashville_Tornado/20200307a_RGB/](https://noaa-eri-pds.s3.amazonaws.com/index.html#2020_Nashville_Tornado/20200307a_RGB/)

NOAA provides a web map view of this data available at [https://storms.ngs.noaa.gov/storms/nashville/index.html#9/36.1800/-86.2000](https://storms.ngs.noaa.gov/storms/nashville/index.html#9/36.1800/-86.2000)

## Visualizing the Cloud Optimized Geotiffs (COG)

There are a few platforms that can directly visualize cloud optimized geotiffs and the virtual rasters:

[https://cholmes.github.io/cog-map/#/url/https%3A%2F%2Fnoaa-eri-pds.s3.amazonaws.com%2F2020_Nashville_Tornado%2F20200307a_RGB%2F20200307a_COG.vrt/center/-85.58207,36.177/zoom/20](https://cholmes.github.io/cog-map/#/url/https%3A%2F%2Fnoaa-eri-pds.s3.amazonaws.com%2F2020_Nashville_Tornado%2F20200307a_RGB%2F20200307a_COG.vrt/center/-85.58207,36.177/zoom/20)

and

[https://cogeo.xyz/mosaic.html?mosaicid=78090264bf9804d89334b8b58c86e3d6f3798b3cf4443f86da37878d](https://cogeo.xyz/mosaic.html?mosaicid=78090264bf9804d89334b8b58c86e3d6f3798b3cf4443f86da37878d)


## Working with the data with GDAL

GDAL includes the vsis3 driver which allows you to access data directly off of S3. For example to merge all of the geotiffs into a single one you could execute the follow command, cautioning that this will touch a lot of data and result in a multi gigabyte file:

```
gdalwarp /vsis3/noaa-eri-pds/2020_Nashville_Tornado/20200307a_RGB/20200307a_COG.vrt mosaic.tif
```

## Example of this data

![Example image from Nashville Tornadoes ERI](img/example.png)

## Accessing other Emergency Response Imagery

The imagery since 2005 is available in the `noaa-eri-pds` bucket.

It can be accessed via the command line or via https. For example to list all of the events from 2019:

```
aws s3 ls s3://noaa-eri-pds/2019 --no-sign-request
```

or via HTTPS: [https://noaa-eri-pds.s3.amazonaws.com/?delimiter=/&prefix=2019](https://noaa-eri-pds.s3.amazonaws.com/?delimiter=/&prefix=2019)

To see all of the collection dates in an event:

```
aws s3 ls s3://noaa-eri-pds/2019_Hurricane_Dorian/ --no-sign-request
```

or via HTTPS: [https://noaa-eri-pds.s3.amazonaws.com/?delimiter=/&prefix=2019_Hurricane_Dorian/](https://noaa-eri-pds.s3.amazonaws.com/?delimiter=/&prefix=2019_Hurricane_Dorian/)